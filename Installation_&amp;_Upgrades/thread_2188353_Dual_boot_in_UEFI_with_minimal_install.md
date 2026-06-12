---
title: "Dual boot in UEFI with minimal install"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by Jeffrey Martin on 2013-11-16
I'm setting up a new system from scratch and i just spent alot of time experimenting with a dual boot setup on GPT in UEFI, but it seems problematic at best and i'm not successful at getting it to work.

I'm using Win7 and Ubuntu Minimal install from the mini.iso, which DOESN'T contain the ability to boot into UEFI ([see note here]("https://help.ubuntu.com/community/Installation/MinimalCD")).

I tried the following:

/dev/sda1  --- The EFI/boot partition
/dev/sda2  --- Win7 120GB 
/dev/sda3  --- / (ubuntu) 30GB
/dev/sda4  --- linux-swap


Installed everything first, the minimal iso in normal mode, then booted a live CD to run boot-repair, it did work in the end, but i did get a few generic errors from boot-repair and there ends up being two windows7 entries in the GRUB2 menu.
I also tried installing with a normal ubuntu live cd but i still end up running boot-repair and fixing some things.

Surely there has to be a better way to do it?

Is there any way to do a minimal install or something similar in UEFI mode and is there a better way to setup GRUB2 on the boot partition without having to do boot-repair or other tweaks?

Basically installing windows 7, then properly setting up GRUB and finally (?) installing the mini.iso and adding it to the GRUB menu

---

### Post by fantab on 2013-11-16
You can use [EasyBCD]("https://neosmart.net/wiki/easybcd/") in Windows to boot Ubuntu. However, I have never used EasyBCD so I will stop. You can explore more about it on WWW.

If you can post the 'Bootinfo Summary' Link which Boot-Repair creates here, then perhaps we can help you figure out those errors.

---

### Post by Jeffrey Martin on 2013-11-17
I can do that when i experiment again yes, but i would like to know if anyone has any other solutions.

Doing a boot-repair just doesn't seem like a very clean solution to me, there has to be some way to just set it up or configure it properly manually without having to repair anything afterwards.


I also would like to hear if someone can explain the minimal install, since it doesn't have the UEFI data you can't boot the installation of mini.iso in UEFI, so it's installed in "legacy" i suppose? Is this entire installation flawed at that point? (Since it's not installed in UEFI mode) -- Or is this only important for GRUB to setup correctly under /boot/efi and nothing else

---

### Post by oldfred on 2013-11-17
New UEFI systems have the BIOS compatiblity mode. So you can boot in BIOS or UEFI. It just is that they are not compatible, so once you start booting in one mode you cannot in grub menu switch to another install in the other mode.

All Boot-Repair is really doing is uninstalling grub-pc and installing grub-efi. That also installs an entry into fstab so efi partition is auto mounted. (I do not think Boot-Repair does that, but grub install does).
Boot-Repair then also adds correct Windows entries to grub menu to chainload to Windows. Grub has been only createing BIOS entries that do not work with UEFI. Bug finally fixed only in the very newest verision of grub, and for it you then get duplicate but both working entries. But you can easily add your own entries in 40_custom. Boot-Repair puts its entries in 25_custom.

You could just install in BIOS boot mode. Boot into mininal and install the grub-efi package. The grub in the MBR will not get overwritten and then trying to boot in BIOS mode will probably give an error. But UEFI may not pick up new entry and you have to reboot twice.

Boot-Repair is just automating with scripts many of the standard fixes that we used to have to try to get new users who were hesitant to use command line to run.

I recently saw a thread where  a user wanted different software in his install. So instructions were on respinning the ISO. You should be able to to the same thing by adding grub-efi (and maybe support files).

---

### Post by Jeffrey Martin on 2013-11-17
> **oldfred said:**
> New UEFI systems have the BIOS compatiblity mode. So you can boot in BIOS or UEFI. It just is that they are not compatible, so once you start booting in one mode you cannot in grub menu switch to another install in the other mode.

All Boot-Repair is really doing is uninstalling grub-pc and installing grub-efi. That also installs an entry into fstab so efi partition is auto mounted. (I do not think Boot-Repair does that, but grub install does).
Boot-Repair then also adds correct Windows entries to grub menu to chainload to Windows. Grub has been only createing BIOS entries that do not work with UEFI. Bug finally fixed only in the very newest verision of grub, and for it you then get duplicate but both working entries. But you can easily add your own entries in 40_custom. Boot-Repair puts its entries in 25_custom.

You could just install in BIOS boot mode. Boot into mininal and install the grub-efi package. The grub in the MBR will not get overwritten and then trying to boot in BIOS mode will probably give an error. But UEFI may not pick up new entry and you have to reboot twice.

Boot-Repair is just automating with scripts many of the standard fixes that we used to have to try to get new users who were hesitant to use command line to run.

I recently saw a thread where  a user wanted different software in his install. So instructions were on respinning the ISO. You should be able to to the same thing by adding grub-efi (and maybe support files).


Thanks.

It just seems kind of hacked together to me, whereas the standard MBR way actually works as it's supposed it. Don't get me wrong, i would very much like to run my system with UEFI, but it seems i will need to take some time to tweak and test things first.
Can i try this from a virtual environment aswell, so i can start using my PC with the standard MBR i have now while i learn/figure out how to properly do this?

So the duplicate entries will get fixed/removed in future versions of GRUB?

Regarding the minimal: it's just the grub-efi that differs here right? And the actual files/installation of the OS is exactly the same even if it were UEFI bootable?
To be precise, once you've fixed grub after installing minimal in BIOS compatibility, it's actually working as it would be if it were installed in UEFI mode?

And the GRUB to "MBR" install in bios-compatibility mode also confuses me since you're on a GPT drive, is this where the "protective MBR" is for, so it's writing GRUB to that? 

I think respinning the ISO is a bit above my skill level at my point, i will try to learn about it though!


Jeff

---

### Post by oldfred on 2013-11-17
In gpt partitioning the protective MBR is still the first sector of the drive. It has one partition table entry supposed for the entire drive so old tools like fdisk see drive as fully partitioned and do not attempt to repartition it or at least let you know something is there. But the boot code portition of the MBR is usually empty, so grub can install to it. Windows only boots from gpt partitioned drives with UEFI, but Ubuntu will boot either way if either bios_grub partition or efi partition are there. But I do not think you can have both working at same time.

With the protective MBR, there is no space after MBR where grub adds its additional code, core.img. So you have to create a bios_grub partition which is just that extra space for core.img. It can be anywhere on drive.

Your UEFI/BIOS should have settings to turn on/off UEFI or CSM/Legacy/BIOS boot modes. If secure boot is on only those systems that are secure boot will be offered to boot. CSM has no secure boot mode. Some auto switch modes depending on what device/entry you choose.

Boot-Repair will proably need an update to recognize the very newest grub does add correct chain entries and not create duplicates. But it is easier to delete duplicates than add an entry.  But Some UEFI still only boot Windows and Boot-Repair does a rename and it has to create the renamed files.

Never used vitual install, so cannot suggest much. But you can boot minimal from BIOS mode even if Windows is UEFI. You just have to go into UEFI to choose which to boot. You may have to change UEFI settings or UEFI on, CSM/BIOS on etc.

---

