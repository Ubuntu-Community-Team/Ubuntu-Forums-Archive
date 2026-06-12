---
title: "boot-repair not working"
date: 2016-08-23
forum: Installation &amp; Upgrades
---

### Post by cyril-auburtin on 2016-08-23
[http://paste.ubuntu.com/23081819/](http://paste.ubuntu.com/23081819/)

When I run boot-repair, it warns to save data, then there's only the option to generate the paste report, but the fix isn't attempted

---

### Post by oldfred on 2016-08-23
Boot-Repair is giving you a big clue here:
> 
 Error: no partitions 


Details on drive info also show no partitions.
You have an UEFI system, but show a Windows boot loader in the MBR for BIOS boot.
But with UEFI Windows only boots from gpt partitioned drives.
And a BIOS Windows boot loader can only boot Windows from MBR(msdos) partitioned drives.

Do you know if drive was gpt or MBR? That will be first question testdisk asks.
You may be able to recover partitions with testdisk, but need to know if gpt or MBR.
       Testdisk Instructions
[URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"]http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step
[/URL][https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) 

Was this a Windows only system? Some of those with Windows mention that Windows tools may work better for NTFS.[URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"]
[/URL]

---

### Post by cyril-auburtin on 2016-08-23
Hello, thanks, the laptop (acer aspire E1-572) was previously on windows10.

I don't need to keep a dual boot, but I removed all partitions, I can't run window anymore, I think I should have kept the boot one. Too late (maybe a recovery, I'm trying it).

I made some new partitions back, they are empty of course

/dev/sda1  fat32  250M boot
/dev/sda2  ext4  /target  50G
/dev/sda3  linux-swap  8G
/dev/sda4  ext4 /target/home 407G

tried installing ubuntu on them, and I get


> The 'grub-efi-amd64-signed' package failed to install into /target/.  Without the GRUB boot loader, the installed system will not boot.

It was probably MBR, not totally sure, but why does the former windows boot matter? I can discard it if needed

my BIOS is set in legacy, and not in UEFI, because I can't manage to boot from an usb key in UEFI, I get a security message

I guess, in last resort, I should reinstall windows, get back that boot section somehow

---

### Post by oldfred on 2016-08-23
With MBR partitions, you do not need an ESP - efi system partition, FAT32 with boot flag.
But with gpt, you need either the ESP for UEFI boot or a bios_grub unformatted 1 or 2MB unformatted partition.
I normally partition with gpt in advance and add both the ESP & bios_grub, particularly for new larger flash drives that I may later want to change from one boot mode to the other.

How you boot install media UEFI or BIOS is how it installs, but that may not be the same mode as default boot of install itself or UEFI/BIOS settings.

If you are getting security messages, turn off UEFI Secure Boot. BIOS mode by default has Secure boot off, but UEFI can be UEFI with Secure Boot or without. And somewhere you have a setting for that. Some systems just call it "Windows" or "Other" and that is secure boot as manual will say if installing Windows 7 use "Other" as default install of Windows 7 is normally BIOS/MBR.

Or you may have a setting in UEFI to turn on USB boot or similar setting.

       MBR or gpt partitions:
[URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by cyril-auburtin on 2016-08-23
Thanks for the help, I have put the UEFI mode without secure boot, it needed to set a password.

I tried a new ubuntu install, but same problem

I'm going to try to restore the boot partition with windows now

---

### Post by cyril-auburtin on 2016-08-24
Ok, I have reinstalled windows, it works fine, it has indeed created a small "system" partition again. (I had to set the boot mode to legacy back, windows seems to want it) 

So now, is it possible to install linux only on this laptop, or do I have to keep this small partition, and have a boot selection menu (I find it annoying, I want to use only one OS). Thanks I'm really confused

---

### Post by oldfred on 2016-08-24
I do not know what boot partition you are discussing.

UEFI systems require a FAT32 formatted partition with the boot flag(if gparted) or ESP - efi system partition. But boot flag with UEFI/gpt is not like a BIOS system boot flag which says which NTFS partition to boot from, but really is just an indicator to add a very long GUID to partition and then UEFI knows that has .efi boot files.

All systems use same ESP for UEFI booting but have different folders in that partition.

Generally Windows makes ESP smallish like 100MB, I normally suggest 300MB, but have seen the author of gpt & rEFInd suggest 600MB more for future use. But install does not actually use much and works fine sharing the ESP with Windows boot files in the 100MB. But if multiple booting, experimenting or other activities larger is better when setting it up. Actually not a lot of most new systems drive unless flash drive where I also use a smaller ESP as I know I just have Ubuntu.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

---

### Post by cyril-auburtin on 2016-08-26
Yes thanks, the guided installation installs an ESP partition, I used the manual before, and that's why it failed

---

