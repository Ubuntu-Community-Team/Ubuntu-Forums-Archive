---
title: "Install in Legacy-mode on UEFI system"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by thejrcrafter on 2014-12-22
So I want to wipe everything and install Ubuntu as my main OS, with Win10 as my secondary. Right now, my hard drive contains an EFI partition. I understand what this is; but, can I wipe the EFI partition and install Ubuntu like a normal Legacy-mode OS and then install Win10 as a Legacy-mode OS?
So right now my partition setup is:
[WINRE] [EFI] [Win8] [Ubuntu] [swap] [Windows recovery]
and I want to make it:
[Ubuntu] [Win10] [swap]
Will my computer still work if I get rid of the EFI partition, and will Win10 install correctly as a Legacy OS?

---

### Post by yancek on 2014-12-22
Whether windows 10 can be installed in Legacy mode is something you should ask at a windows forum  Maybe you'll get lucky and someone here will have an answer.  You are always better off installing windows first as a default windows install is incapable of booting Linux and you will have to reinstall the Linux/Ubuntu bootloader after installing windows.  windows 10 being beta software, there is no real expectation that it will perform to the capabilities of a tested system.

---

### Post by grahammechanical on 2014-12-22
I cannot say about Windows 10 but I installed Windows 8 preview on a normal BIOS/MBR partition and I installed it after having some installations of Ubuntu installed. But if Windows 10 is anything like Windows 8 for installing it will put its boot loader into all the hard disks it can find. I had 2 hard disks and I lost the ability to load the Ubuntu installations that I had on both disks. Be ready for that.

I have just thought of something. If Windows 8 was installed in EFI mode, then Ubuntu needed to be installed in EFI mode and that means that there is a Ubuntu EFI file or two in that EFI boot partition. Delete that EFI partition and I doubt that Ubuntu will load.

Regards.

---

### Post by oldfred on 2014-12-22
Windows 8 only boots in UEFI mode from a gpt drive.
Both Windows & Ubuntu only boot in BIOS mode from MBR(msdos) partitioned drives.

I am pretty sure Windows 10 will install either way, but if partitioned in advance, your partitioning much match how you want to install.

And with both Ubuntu & Windows how you boot installer, UEFI or BIOS boot mode, it then how it installs. So be sure to have both correct partitioning & boot in correct matching mode.

---

### Post by carl4926 on 2014-12-23
> **thejrcrafter said:**
> So I want to wipe everything and install Ubuntu as my main OS, with Win10 as my secondary. Right now, my hard drive contains an EFI partition. I understand what this is; but, can I wipe the EFI partition and install Ubuntu like a normal Legacy-mode OS and then install Win10 as a Legacy-mode OS?
So right now my partition setup is:
[WINRE] [EFI] [Win8] [Ubuntu] [swap] [Windows recovery]
and I want to make it:
[Ubuntu] [Win10] [swap]
Will my computer still work if I get rid of the EFI partition, and will Win10 install correctly as a Legacy OS?

It should (check in the windows irc)
I assume you can start from scratch and have the install media for both.

Use gparted to create a new partition table (msdos) on your hdd
Partition it with sda1 ntfs for windows
and the remainder for Ubuntu as you require ( I use / and /home +swap)
Then install windows to the target sda1
update
Move on to ubuntu install
Remember grub goes to sda

---

### Post by fantab on 2014-12-23
> ...can I wipe the EFI partition and install Ubuntu like a normal Legacy-mode OS and then install Win10 as a Legacy-mode OS?
Yes you can theoritically. But we don't know what Win10 is bringing in. Also 'legacy-mode' is just that, a legacy. This option is still available to support certain older hardware. Gradually this option will be phased out.
UEFI with ESP (EFI System Partition) is the way to go.

Unless you have a dire need to use OS in legacy mode, I strongly recommend against it. 

Install both OS in UEFI mode with GPT formatted HDD/SSD.

---

