---
title: "Install OS-independent Grub2"
date: 2021-04-12
forum: Installation &amp; Upgrades
---

### Post by hikariws on 2021-04-12
Hello!

What's the best way to install Grub2 on a partition so that it works independent of the OS?

I'm building a mini-PC to be my router, I'm installing OpenWRT on it and maybe will install OPNsense on the future. I don't plan to move to it, but I have a lot of free storage to spare, so I just wanna make it compatible.

I had installed OpenWRT and using Macrium to backup the drive, but today I tested its restore and it bugged GRUB:

[ATTACH=CONFIG]288296[/ATTACH]

Cursor just keeps blinking.

So I'm considering making a clean install of Grub and then set it for OpenWRT and any other OS I might install on the future.

---

### Post by grahammechanical on 2021-04-13
It is my thinking that the bootloader is independent of the operating system as it loads before the OS and it can in turn load several different operating systems.

In the case of your mini-pc Grub is unable to find its configuration file (grub.cfg). That is my guess. If Grub was able to scan grub.cfg but not find the kernel where grub.cfg says it should be then you would be seeing different Grub prompt. One that would let enter grub commands/directions to load the kernel.

Somehow, you need to run update-grub which will scan the drive for the OS and re-write grub.cfg. I do not know how you would do that or if it is the solution. Is there an Advanced Options section in the Grub menu? That might be a Ubuntu specific modification. The best I can offer is a link to the Grub2 manual.

[https://www.gnu.org/software/grub/manual/grub/grub.html#Loading-an-operating-system-directly](https://www.gnu.org/software/grub/manual/grub/grub.html#Loading-an-operating-system-directly)

I tried looking for OpenWRT documentation on boot loaders. It seems to say you do not need one. I did find one that mentioned Grub but it was outdate information referring to legacy Grub. So, I do not offer that.

I think that you need the Linux compatible version of OpenWRT for Grub to bootload OpenWRT. But I guess you know that. My quick look through the OpenWRT documentation leads me to view it as educational but not practical for someone who does not know what they are doing. Like myself.

Regards

---

### Post by yancek on 2021-04-13
>  
What's the best way to install Grub2 on a partition so that it works independent of the OS?

You can install Grub manually to a specific partition and then manually write your grub.cfg file.  You will not be able to use the grub-mkconfig command or the Ubuntu stub update-grub as there are various grub scripts/files on different parts of the filesystem such as the /etc, /usr and /sbin directories.

I've not used Macrium so have no idea if it would work.  Have you used it successfully to backup and restore Ubuntu or any Linux?

---

### Post by hikariws on 2021-04-13
@grahammechanical lol tnx

I expected Grub2 to be easier to setup and more OS-independant. What I understood from what I had researched is that it has a small part written on special area of MBR and GPT where UEFI reads to boot the drive. Then the boot partition where lies grub.cfg, and in case of Linux resides too its kernel. It seems that each Lix installed would have its own kernel file/folder and there may be multiple kernel for each installed OS. grub.cfg entries define existing kernels and parameters to load root, including the infamous root= that specifies OS partition and where / is to be mounted.

So, we can have a Grub2 partition that boots multiple OSs on multiple partitions, but each OS must install/modify it themselves with their kernel (in case of Lix) and other files and grub.cfg entries.

Most material I had read describe how to reinstall/fix Grub2 for the own OS LiveCD that installed it, or how to make it manually mount the OS then fix it. OpenWRT doesn't have LiveCD and I was unable to manually mount it. I'm able to boot with Parted Magic, mount partitions and I see the kernel and grub.cfg, but it seems that Ubuntu's grub-install moved them elsewhere and I wasn't able to manually load grub.cfg neither manually load and boot the kernel. In fact I managed to boot the kernel, but it crashed during load...

OpenWRT isn't just educational, in fact it's among the best and most flexibile router OSs. In example, it's the only open source one that supports IPv6 "dynamic" global prefix. But they have to support tens of architectures, hundreds of chips and thousands of devices, x86 is just one of them and not much used, with AMD64 being 1 of 4 builds. Its doc is very vast but also hard to understand by ppl with little experience, and relies on volunteers to be updated.

Being AMD64 a niche inside OpenWRT, I'm trying to do uncommon stuff inside of it, so it's even harder to find doc. Still a guy replied me with help on their forum on attempts to recover boot.

@yancek yeah I use Macrium to backup my Ubuntu server and had restored its / partition multiple times. It's unable to mount ext4 partitions to browse from inside Win10 and doesn't have Lix app, but it's able to backup and restore ext4 and Grub2 drives. Due to that I believed it'd just work and didn't try the restoration.

I stopped working on my new router on friday and decided to restart it yesterday and tried to test the restore, but somehow it broke everything. And I failed to fix/recover it.

I managed to replicate the corrupted boot on a VMware VM, from where I took the SS on op. I tried some stuff on it but no success. Indeed Macrium seems to be incompatible with this setup, IDK to which extend it's related to Grub2 or OpenWRT.

I have a list of all apps I installed and have my config files on a Subversion repo, so I'll reinstall the whole thing. But first I'm gonna make more tests on VM, if Macrium corrupts boot again and how Clonezilla and maybe other tools manage it.

---

### Post by oldfred on 2021-04-13
I have installed grub to flash drives by itself, in both old BIOS and newer UEFI modes.
But had to totally do the grub.cfg boot stanza myself as grub does not have an install with the additional scripts to update or create grub menu.
If you did a manual install, you need a grub.cfg that the install sees. And usually can copy boot stanzs from whatever grub.cfg you have for your system. 

I did that primarily for loopmount boot of ISO files on smaller flash drives. Now with larger flash drives and a SSD, I do a full install & just add loopmount stanza to boot ISO.

---

### Post by grahammechanical on 2021-04-13
> OpenWRT isn't just educational, in fact it's among the best and most flexibile router OSs. In example,

I did not mean that the OpenWRT OS was for educational purposes but that the documentation had little practical value for explaining how to do things. Or, so it seemed to me.

Regards

---

