---
title: "Dual Booting with Windows 7"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by hessczoo on 2012-12-11
Hi,

I recently purchased a new hard drive for my system, I will give you a quick explanation of that

sda - Old 1TB drive, MBR, houses my Windows 7 install
sdb - New 2TB drive, GPT houses Ubuntu 12.10

Ubuntu installs to my new drive no problem, but I can't boot into Windows, I get a "EFI File Path not valid". I tried boot-repair, it says to make a 1MB partition on the drive to be able to fix.

I deleted the whole drive and changed the Ubuntu drive to MBR and tried to reinstall. It set it back to GPT, and I am finding the same problem.

Is what I am trying to do impossible? How can I get this functioning in dual boot, with each OS on it's own drive without having to erase my Windows 7? Is disabling UEFI boot going to fix it?

Thanks

---

### Post by debodas on 2012-12-11
Where did you put your bootloader in your current setup?

---

### Post by oldfred on 2012-12-12
Your system must be UEFI capable.

       Windows will only boot from gpt partitioned drives with UEFI.
Windows x64 Installer determines which firmware has been used for booting the ISO/DVD/USB. If BIOS is used, only MBR is supported. If UEFI is used then only GPT is supported. Not vice-versa.

    
Ubuntu will also install in either UEFI or BIOS boot mode depending on how you boot installer. But Ubuntu will boot from gpt partitioned drives in BIOS mode.

And both systems need to be installed in BIOS or UEFI boot modes as you cannot chainload from one to the other. You may be able to change boot from UEFI to BIOS in UEFI menu and change which system you boot, but a hassle.

If Windows is MBR, I would install Ubuntu on gpt partitions but in BIOS mode. I only have BIOS but boot Ubuntu from gpt drive and chained to XP on a MBR drive.  With gpt and Ubuntu in BIOS, you do have to have a small 1MB bios_grub partition. I believe now the installer does add that, but it did not used to. I might also leave 300MB as a future efi partition as first partition, do not set boot flag or it will be seen as efi partition. That would only be for future use, but it would be difficult to add an efi partition in the future as it should be first (or second) partition.

       gpt(GUID) is required for drives over 2TB, suggested for SSDs, and required for UEFI booting. Ubuntu will work with gpt partitioned drive with either BIOS or UEFI.

            However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.

   In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02.

---

