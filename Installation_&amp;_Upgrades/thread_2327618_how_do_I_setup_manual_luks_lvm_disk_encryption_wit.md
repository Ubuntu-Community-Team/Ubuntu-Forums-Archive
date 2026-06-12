---
title: "how do I setup manual luks lvm disk encryption with ntfs partition?"
date: 2016-06-12
forum: Installation &amp; Upgrades
---

### Post by a.dusty.trail on 2016-06-12
I'm installing lubuntu 16.04 with the alternate install disk to a second 475gb hard drive that has a 200 gb ntfs partition already on it.
(My other operating systems are on the first drive)
I'm looking for the procedure to manually set up luks I'm encryption. 
I would like to have a 5gb /boot,a 60 gb / ,a10 gb swap and the rest 200gb /home.

Every tutorial I've read this time requires a live CD.i was sure there was a way with just the alternate cd.

What is the best way to set it up?

---

### Post by TheFu on 2016-06-14
I´ve tried on 14.04 to setup manual encryption and failed about 20 times.  None of the how-tos are correct. Think they last worked in 2010.
The only way I´ve been able to get boot-level encryption working was through the automatic installer, which insists on wiping an entire disk.

BTW, it isn´t clear which 200G you are speaking about above, but NTFS cannot be used as HOME.  Also, is the existing NTFS partition just data? If so, back it up before doing anything. luks encryption is normally done at the partition level, then LVM is used to split up that into LVs (which are like logical partitions).  If you create separate partitions for each mount, then you´ll need to enter passphrases/keyfiles for each. OTOH, if you use LVM, only 1 partition is involved and only one passphrase/keyfile is needed to unlock the system.

```
$ lsblk
NAME                          MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 55.9G  0 disk  
ââsda1                          8:1    0  487M  0 part  /boot
ââsda2                          8:2    0    1K  0 part  
ââsda5                          8:5    0 55.4G  0 part  
  ââsda5_crypt                252:0    0 55.4G  0 crypt 
    ââubuntu--mate--vg-root   252:1    0 51.5G  0 lvm   /
    ââubuntu--mate--vg-swap_1 252:2    0    4G  0 lvm   [SWAP]

```
Sorry about the funky characters. I´ve been having that issue since installing 16.04. Just need to find the correct mix of the keyboard mapping and character set for my console.

Hopefully, someone will respond with a manual step-by-step solution that actually works. My attempts to manually modify the initfs and crypttab and fstab has always failed. I´d also really like to use GPT, not MBR, formatting.
[B]
A few hours later ... had a thought for making this work ... [/B] I haven´t tried these techniques, but I´m thinking about both carefully and haven´t come up with a reason either wouldn´t work.

a) use a smaller HDD, perform the number automatic installation with all the encryption defaults to a smaller HDD.  For my situation, I have an install on a 64G SSD, but have a 128G SSD that I can bit-for-bit copy everything onto (use dd or ddrescue for the bit-for-bit copy). That would leave 64G available for other, non-encrypted use, or could encrypt the other space with the same or different key for post-boot access.

b) setup a VM with a smaller virtual-HDD, perform the automatic installation with all the encryption defaults. Key would be to use a fully-allocated, image format virtual HDD, not dynamic or sparse or vdi or vmdk.  Then use dd to copy the image file onto the physical HDD.

Again, don´t know if this will actually work, but I don´t see why not.  The booting system will probably need to be non-UEFI (i.e. legacy boot).

---

### Post by a.dusty.trail on 2016-06-16
I thought of that idea so I grabbed an older smaller hd and installed it using the guided full disk encryption with luks.. 
Tried it ad the only drive in the machine
As one of three drives.tried guided full disk luks..
But for some reason after install.it just will not boot.no grub no nothing just hangs with a cursor in the corner..

I'm thinking that 16.04 is broken as far as Luks is concerned..
I'll try a different install disk and other options. But as of right now it is not looking good.

16.04 has a lot of issues that should not be in a long term release.

---

### Post by TheFu on 2016-06-16
16.04 with LUKS has been working great for me in the default setup. It is only the non-default stuff that I´m having issues around.

The boot issue is probably related to the UUID changing.  Or perhaps the kernel and initramfs closed a known security issue?  After all, if all it took was to clone a disk onto another device ...    security has many tiny considerations that aren´t always obvious at first, second, third or even 4th consideration.

Legacy or UEFI?  I´m using legacy, which is not ideal, but there isn´t any other choice on the HW.

Not booting could be something simple, like a video driver. Try nomemset, but there are other issues. Search for your model of PC/motherboard + ubuntu to check for known issues.  Might be worth reading the release notes too - for example, AMD video drivers have caused issues with prior releases.

The rest of my setup is odd, non-standard, so any GUI issues I have just don´t fit with most other people.

---

### Post by a.dusty.trail on 2016-06-17
I would think if ubuntu boots find with a regular setup it should boot when using the encrypted set up.

It failed before I tried anything other than just installing it guided encrypted.
No way to pass any features
It falls to fire grub. Just a blank screen at boot.

Very disappointing for lts release..

---

### Post by TheFu on 2016-06-17
Did you check the BIOS settings?  Make it legacy boot, not UEFI?  Don't know if this is a thing or not, just something to try.
For one person, a minor issue can seem like a huge failure.  Be assured that for many, many, many, people 16.04 is solid and behaving as expected. That doesn't help you or me, sadly.

Do you have different hardware to try?  What hardware on which is this being attempted?

---

### Post by a.dusty.trail on 2016-06-19
Failure should be based on how well the unusual is supported not the common.
But since I'm installing on pretty common hardware failure is just failure.

I have tried both the alternate and desktop amd 64 install disks tried on a hp pavilion and acer vertion systems. 
And while the desktop install spits out errors right from the start that I have to turn swapoff as the swap I'm not encrypted(duh it's the install swap not one I created) to finally regurgitating a unipartman error 435 failure in partitioning and would I like to try again just to get a partman error of 10 and if I continue
It fails to install grub into the drive and then the option to pick another partition fails to function at all.
(The only drive I the computer I might add)

Which act just like the alternate install except it spits out no errors..

15.10 installs just fine. On both system

Which brings me back to my conclusion that 16.04 is broken as far as luks full disk encryption is concerned(among many other things that have been changed and very little up to date documentation to fix anything)

This is a pretty serious issue for people who are looking for the security and safety of encryption. 

even if someone found the problem and fixed it it will be a long long time before they replace the install disk with updated fixes.
(Which I think personally they should do on a weekly basis and not rely on internet updates)

So I'm not happy at all with the current 16.04 long term support lubuntu and ubuntu.
And I don't expect it to be fixed any time soon.
(I would rather go back to Windows than 15.10 which will lose support before long and it has it's own bugs)

---

