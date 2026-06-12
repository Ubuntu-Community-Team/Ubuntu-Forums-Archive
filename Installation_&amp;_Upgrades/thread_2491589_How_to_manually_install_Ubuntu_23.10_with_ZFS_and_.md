---
title: "How to manually install Ubuntu 23.10 with ZFS and TPM-backed full disk encryption?"
date: 2023-10-14
forum: Installation &amp; Upgrades
---

### Post by thearde on 2023-10-14
I have a dual-boot system. For work purposes, it's required to use full disk encryption. The option to install Ubuntu alongside Windows doesn't encrypt the install and there's no option to encrypt if a user picks that option. The options for TPM-backed full disk encryption (FDE) and ZFS are both exclusive to the installer option that wipes my entire disk.

Are these options exposed through a command-line driven install? If so, how would I go about it?

---

### Post by MAFoElffen on 2023-10-14
I do a lot of installs of ZFS for both Released versions and in the DEV Cycle for 23.10. I'm tring to get things ironed out for ZFS for 24.04. I have done encrytpted installs of ZFS-On-Root with both ZFS internal encryption and with LUKS1 and LUKS2. (as well as Linux itself within LUKS containers)

I have never "tried" to do ZFS-On-Root encryption with TPM 'yet'.
RE: [https://ubuntu.com/blog/tpm-backed-full-disk-encryption-is-coming-to-ubuntu](https://ubuntu.com/blog/tpm-backed-full-disk-encryption-is-coming-to-ubuntu)
[quote=Canonical]
For full disk encryption, Ubuntu stores the disk encryption key outside of the TPM, protected by the TPM's storage hierarchy inside a sealed data object. The TPM will only reveal the key to code executing inside of the initramfs if the boot environment has previously been authorised to access the confidential data.
[/quote]
So... My current answer is: Let me play with it and see for myself. I'll be back.

As for your last question. No. Not currently, at least not for the new installer for 23.10. I have some questions in for the developers and maintainers of ubuntu-desktop-installer where we can find something to modify the options from a command line during the install. I'm working on it for us to be able to tweak the ZFS install options from the defaults they have set within the canned scripts.

I have the ZFS autoinstall yaml scripts... But that is beyond the basic skills of most normal users. We used to be able to do tweaking during the install, with the old installers.

 Maybe you could add a comment in each, to add weight to them, so that they see it's not just me asking for Users. That there "are" actually Users from here, that need that option to tweak things...

I know these say for partition size, but once they tell me where those new files are, that will open the door to change other options.
RE:
[https://answers.launchpad.net/ubuntu/+source/subiquity/+question/708132](https://answers.launchpad.net/ubuntu/+source/subiquity/+question/708132)
[https://github.com/canonical/ubuntu-desktop-installer/issues/2361](https://github.com/canonical/ubuntu-desktop-installer/issues/2361)

My question to you is: Jammy Ubuntu 22.04.3 LTS) has ZFS-On-Root with encryption. Jammy is long term support and Stable. Your computer is for "work". 23.10 is considered as "development" (not-stable). Why 23.10 on a work computer? You know you can setup encryption keys on on cards and USB flash drives right? Why the requirement for TPM stored key? 

I have to ask those... Just, so I know the whys and can stay in touch with what is pushing the Users I support.

---

### Post by #&amp;thj^% on 2023-10-14
Just my 2 cents worth here, but why a dual-boot system. ?
Most of us won't reply on that subject, MAFoElffen is a very helpful user and your lucky enough he replied.
And please read and reply back to his questions.
> My question to you is: Jammy Ubuntu 22.04.3 LTS) has ZFS-On-Root with encryption. Jammy is long term support and Stable. Your computer is for "work". 23.10 is considered as "development" (not-stable). **_Why 23.10 on a work computer? _**You know you can setup encryption keys on on cards and USB flash drives right? [B][U]Why the requirement for TPM stored key?
[/U][/B]
I have to ask those... Just, so I know the whys and can stay in touch with what is pushing the Users I support. 

---

### Post by sudodus on 2023-10-14
I agree with the previous replies.

- An alternative is to run Ubuntu from an SSD connected via USB 3.

- Another alternative is to run Ubuntu in a virtual machine: install VirtualBox in Windows. This can work well, if the computer is powerful enough.

- If you intend to do the heavy tasks in Ubuntu (and lighter tasks in Windows) you could do it the other way around. Use the whole drive for Ubuntu, install VirtualBox or KVM+Virtmanager and install Windows in a virtual machine.

---

### Post by MAFoElffen on 2023-10-14
Am already playing with unlocking the key - store (spaces added there or the Forum filet removes it) with the TPM. 

That is a very good point... A Hyper-V VM, on Windows Pro that is bitlocker encrypted, "is" in an encrypted container, and passes security requirements for physical security.

(I also support Win and VMware.) If you have BitLocker, then your edition of Windows is a least Pro, and also supports Hyper-V.

You have alternate options available.

Back to playing with installs and testing.

---

### Post by MAFoElffen on 2023-10-14
It is easier than I thought it would be, so far... But doing it still needs some skills.

The install is the same 'manually install' of ZFS-On-Root with encryption... I installed with both LUKS and separately with ZFS native encryption... 

That part it is the same. 

I am still working on the post install processes. The post-installation is where "the hard work starts." It gets different in how to store the key inside the TPM, and building an inistramfs image that can read that key. I've read a lot of information on this today, and trying to see what actually works for a Debian branch bootable root image... 

Then working on a script to read that key from the TPM that gets stored in the initramfs, instead of prompting the user to enter it. Working on how to do that now. 

Then signing the kernel, and initramfs image, because it should work with Secure Boot enabled. Secure Boot is not a hard requirement, but since EFI is unecrytpted, they figure that with Secure Boot enabled, the files built for EFI need to be either signed or marked as trusted by MOK enrolled keys.

Hmmm. Yes.  A good challenge. It has been mostly a whole lot of reading so far. That has been taking me the most time.

---

### Post by MAFoElffen on 2023-10-15
Am still working on this. I broke it. It's a chicken before the egg kid of thing with Grub2, LUKS, and ZFS with an encrypted bpool. I admit, I have never seen a fully encrypted ZFS ZFS-On-Root, but am trying to see if it can work.

For 20.04 up through 22.10, the canned installer scripts and (separately) the ZFS-On-Root installation guides, where there are options for encrypting the install... had rpool as encrypted, but bpool was not. I hadn't thought about the why of that before. 

Logically, I thought that it might be possible if I just setup everything and set the pointers to each. People in the background(, places), where saying they didn't know if it was possible to boot from an encrypted bpool yet. I figured it was time to see, right?

Grub reads LUKS. Grub reads ZFS... But no one can tell me how it sees ZFS inside LUKS, for me to set the pointers and timing precedence.

That is what I am facing. It's a timing issue with Grub2. It has the LUKS filesystem uuid as the helper, but root points to rpool/... etc... and it fails not finding things. It's not even finding the kernel, initramfs, or vmlinuz image. It's not even asking to unlock the LUKS containers, so it's not seeing what is inside them. Chicken before the egg timing issue.

Manually-- I can unlock it, mount it, and chroot into it. But it won't boot on it's own via Grub... Maybe I should recheck the LUKS versions and key-slot types... Because I can boot LUKS2 from Grub2 with the the old key-slot type, but not with the new default key-slot type... Hmmm...

Alternately, trying the same with ZFS native encryption. The problem there, is that, it's been there since around 2015-2016, and been working, but there is only a single key-slot. (LUKS has 8). There has been a feature request to add more since 2017. They say that is not their priority right now. I can see that the code has been added for the hooks for that, but even with ZFS release 2.2 releasing yesterday, I don't see where they had implemented that yet.

Like I said, working on that. I may have step back a moment, go fishing and think on ways into that... LOL

---

### Post by thearde on 2023-10-16
Hey, thanks for digging deep on this with me! I'm very lucky. 

> Maybe you could add a comment in each, to add weight to them, so that  they see it's not just me asking for Users. That there "are" actually  Users from here, that need that option to tweak things...

I've weighed in on both!

>  My question to you is: Jammy Ubuntu 22.04.3 LTS) has ZFS-On-Root with  encryption. Jammy is long term support and Stable. Your computer is for  "work". 23.10 is considered as "development" (not-stable). Why 23.10 on a  work computer? You know you can setup encryption keys on on cards and  USB flash drives right? Why the requirement for TPM stored key? 

I'm in DevRel and part of that job is staying close to where our users are so I build empathy for the kinds of environments they run our software in. That necessitates the dual-boot (Windows and Linux). Running the latest and greatest of Ubuntu gets me ahead of the  early adopters and the environments our users will eventually run when these new features roll into the next LTS. I could choose to run one OS in another but call me old-fashioned I just prefer as real-as-it-gets when it comes to replicating environments.

---

### Post by sudodus on 2023-10-16
> **thearde said:**
> ...

I'm in DevRel and part of that job is staying close to where our users are so I build empathy for the kinds of environments they run our software in. That necessitates the dual-boot (Windows and Linux). Running the latest and greatest of Ubuntu gets me ahead of the  early adopters and the environments our users will eventually run when these new features roll into the next LTS. I could choose to run one OS in another but call me old-fashioned but I just prefer as real-as-it-gets when it comes to replicating environments.

I think it would be valuable for you to boot not only a single Ubuntu version installed alongside Windows in the internal drive. You can test your software in several [Linux] distros and versions running in USB 3 drives (SSDs are faster and more reliable than pendrives). You might also need testing in computers with various hardware which is convenient with a bootable USB system.

So you can try with Ubuntu (and other distros), 1: live, 2: persistent live and 3: installed (installed like into the internal drive but in this case into a USB drive) depending on what you need to verify that your software works.

[HR][/HR]
If it turns out too difficult or if you must wait too long for what you want, then an Ubuntu system in an SSD might work also as your main Linux system for development.

---

### Post by MAFoElffen on 2023-10-16
The closest I could get you with Linux to be full disk encryption was to do a hybrid system of volume managers. I learned some things doing this in the past few days.

There is still a limitation of what Grub2 can work with, and boot. 

For ZFS bpool boot pools, because of Grub2 scripts, the pool name of the boot drive has to be named "bpool". You can change the name to something else 'zpool rename', but then you need to modify script  /etc/grub.d/10_linux_zfs to match that new name. The scripts in that directory are not user scripts, so do get replaced during upgrades, so changes can get lost, and changed back, and may be at risk of breaking the system, during updates if you did that.

For Grub2, it can boot encrypted LUKS volumes if it has ext4 boot within it, or an LVM2 Boot volume. Grub2, as of now, cannot yet handle ZFS boot volumes inside a LUKS container, nor a Boot Pool that is ZFS native encrypted. Here is the compatibility layer of features that Grub2 can handle with ZFS:
```

# Features which are supported by GRUB2
async_destroy
bookmarks
embedded_data
empty_bpobj
enabled_txg
extensible_dataset
filesystem_limits
hole_birth
large_blocks
lz4_compress
spacemap_histogram

```
So that ZFS in not limited by that, that is why if encrypted pools, the boot pool is separated out to an unencrypted bpool. 

So the furthest I could stretch the Linux installs, and have it bootable with full disk encryptions... meaning also having the the boot partition encrypted... Was to install the OS on things, but I had was to place /boot within an encrypted LUKS container, with either an embedded ext4 filesystem, or an LVM2 boot volume with a filesystem, inside that LUKS container... For Grub2 to be able to read it.

Then use ZFS pools for other things. At that point, I could see that that was a whole lot of work just to 'have ZFS'.

I don't personally have an encryption requirement. I have done dual boots for over 18 years now. 

When I do things, I like and want to see what it does on hardware. But... That has shifted in the past 13 years though, with KVM. KVM has been a great tool for me for easily replicating environments, testing and debugging things on them. I am now flexible with arches, OS'es and hardware that I can replicate to test on. I do a lot of testing within VM hosts.

I still have 6 machines here, but 3 of them still dual boot, and all them have KVM installed to support VM Hosts. Those 3, also have Hyper-V. All 3 of those are ZFS-On-Root, (With another of the other machines, being migrated to ZFS-On-Root.)

But my "workstation" is "different." It has Hot Swap drive bays. With that one, I can just swap in a drive and reboot what I need to. That is how I beta test VMware vSphere and vCenter on that machine.

I thought maybe that I could possibly do an fully encrypted ZFS-On-Root... That answer (currenlty) is not fully ZFS for everything. We are limited in what form of encrypted boot volumes we can boot from, because we use Grub2 as a boot loader.

---

### Post by MAFoElffen on 2023-10-16
LOL. I came up with a purely ZFS solution... but it pushes the limits on how fully encrypted is "interpreted." It involved using a removable token.
> 
Encryption essentially means scrambling sensitive data that must  then be decrypted with a unique key in order to be read. Tokenization  involves swapping sensitive data for a token that must then be presented  in order to retrieve the data. Tokenization is often employed by  payment processors, banks, merchants, and other institutions that  operate in fields where additional compliance with regulating bodies is  required. 

To prevent tokens from being altered while on a system, I set them to only be read-only by the user... permission 0400... Removable tokens can be physically security. When removed the system is disabled.

So moving the bpool and key store to a removable token qualifies for fully encrypted... In that interpretation. I know, that is pushing the limits of that.

---

