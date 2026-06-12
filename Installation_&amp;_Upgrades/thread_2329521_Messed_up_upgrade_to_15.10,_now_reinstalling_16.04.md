---
title: "Messed up upgrade to 15.10, now reinstalling 16.04. Need help with partitions"
date: 2016-07-02
forum: Installation &amp; Upgrades
---

### Post by chris-fp-jakins on 2016-07-02
Hello,

To start, I tried upgrading from 14.04 to 15.10 last night. About mid-way through, my comp froze. Apparently there is a known bug that tells the computer to restart before the updater is done configuring. Anyways, after looking around on other forums, the easiest thing to do seems to be a fresh install. I've decided to just go with 16.04.

Since I was running Windows before I installed Ubuntu beside it, I had to set up partitions and followed this guide: [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
So I know I have to delete my root partition and recreate it with the installation (already backed up all my important files), but do I have to delete the others? Specifically, the boot (flagged as BIOS-GRUB), linux-swap, and ext4 partitions. Setting up grub was quite the hassle, so I'm hoping to not have to go through that again.

I can upload a screenshot of gparted output if that would make answering this easier. Thanks in advance to anyone willing to help.

Chris

EDIT: I went ahead and ran gparted off my 16.04 DVD. Output: [http://imgur.com/gWjesvl](http://imgur.com/gWjesvl)

---

### Post by sudodus on 2016-07-02
You can re-use the same partitions (the root partition and the swap partition) where you had 14.04 LTS. You need not wipe them, it is enough to format the root partition (a setting in the installer).

It might work with one of the 'automatic' methods offered by the installer, but I prefer to have full control of the installation and use 'Something else' at the partitioning window. Then you can identify and specify which partition to use for the root partition '/'. The swap partition is usually selected automatically, but you can check it if you wish.

Finally, at the bottom of the partitioning window you can specify where to install grub. This is important and works in BIOS mode, but in UEFI mode it will be installed into the first drive /dev/sda (an EFI partition in that drive).

-o-

I'm glad to read that you have already backed up all your important files - installing an operating system is risky, and can go wrong.

Good luck :-)

---

### Post by chris-fp-jakins on 2016-07-02
Ok, so messing up that upgrade didn't "corrupt" any of the partitions? I did try to follow some other guide for restoring it (using chroot and dpkg), but that is, ultimately, where it went wrong and wouldn't even boot. If not, then that is very good to know.

I guess I'm still a little confused about the installing grub part. 
What is /dev/sda7 (flagged as BIOS-GRUB), and what is /dev/sda2 (fat32, flagged as boot, esp)? 
Which one do I choose for grub installation, or will it be automatically installed into /dev/sda like you said? I'm 98% sure I have a UEFI system.
How will this affect my current GRUB bootloader screen? Will choosing the "Ubuntu" option that I used for the older version boot the newer version instead, or will there be a new option? 

I apologize for all the questions. I'd just like to have a firm understanding before I go through with install, as, like you said (and due to previous experiences), it is risky.

---

### Post by oldfred on 2016-07-02
How you boot installer UEFI or BIOS is then how it installs.
And with UEFI, grub has some files in the ESP - efi system partition (FAT32 with boot flag).
And with BIOS grub has a file (core.img) hidden in the bios_grub partition. 
You do not need both, but I always create both on all new gpt partitioned drives just to have them available.

If Windows is installed in UEFI mode it also has its boot files in the same ESP as Ubuntu just in different folders.

But in all cases you tell grub to install to a drive like sda, never to a partition like sda2, sda3 etc. With UEFI it knows to put files into the ESP and with BIOS it installs part of the boot loader to the MBR and part into bios_grub. In both cases most of grub is still in the / (root) partition in /boot folder and grub configuration files in other folders.

You do not have to delete any partitions, but just during Something Else choose the same / (root) partition. It will find swap automatically. Also if you have separate /home partition, be sure to choose same partition for /home, but DO NOT tick/check the format option or it will erase it.

You should have good backups of /home - per user data &  config files for applications are in /home, possibly /etc if you manually configured system files and an export of installed applications to make it easy to reinstall them.

---

### Post by grahammechanical on 2016-07-02
Under the old BIOS boot system we had an MBR partitioning scheme. With a UEFI boot system we get a GPT partitioning scheme. Now if we install any OS on a GPT hard disk in EFI mode we need a efi_boot partition. Also called EFI System Partition (ESP). It is where the boot files go. If we install an OS in BIOS/Legacy/CSM mode we need a bios_boot partition. Again it is where the boot files will go.

The Ubuntu installer will make use of an existing bios_boot or efi_boot partition and it will put the Ubuntu boot files there. In the case of an efi_boot partition any Windows boot files will not be over-written. The Ubuntu efi boot files will co-exist with the Windows boot files. 

[https://en.wikipedia.org/wiki/EFI_system_partition](https://en.wikipedia.org/wiki/EFI_system_partition)


It seems that you have both types of boot partition. No harm is done. If you had Windows installed in EFI mode that would have created the esp partition. If you then installed Ubuntu in BIOS mode that would have created the bios_grub partition.

Regards.

---

### Post by chris-fp-jakins on 2016-07-02
Thank you all for your answers, they have been very helpful. I will give this a go and report back.

---

### Post by chris-fp-jakins on 2016-07-02
Quick question: When I mark the root partition, do I check the format box?

EDIT: I'm guessing not. It says the system files will be deleted, and I'm assuming they'll be reinstalled?

---

### Post by chris-fp-jakins on 2016-07-02
Installation seems to have gone perfectly. All my files are intact. Thanks again to all of you for your help. I will mark this thread as solved.

---

