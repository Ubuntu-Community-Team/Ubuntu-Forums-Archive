---
title: "grub-efi-amd64-signed package failed message"
date: 2015-12-15
forum: Installation &amp; Upgrades
---

### Post by MadMax2 on 2015-12-15
While installing   ubuntu 14.04.3 LTS I got a message

> The "grub-grub-efi-amd64-signed" failed to install to /target/. Without the grub boot loader the installation will not boot


I ran from DVD and installed Grub Repair (per Google)
Failed:
"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again."
[http://paste.ubuntu.com/14040565/](http://paste.ubuntu.com/14040565/)


So far I haven't understood how to use G parted.

Can anyone help?
Thanks

Edit
in terminal: Gparted
I checked a BIOS_GRUB flag on the main partition (previously I hadn't hit the tick up the top to *apply*


Now boot repair I wasn't sure which disk and installed it to sda 1 (the small one)?
 It didn't boot.

Used live DVD again and ran boot repair -this time it said it had repaired it.

Reinstalled [clean]. Checked Use LVM (logical Volume Management)  just in case.

---

### Post by oldfred on 2015-12-15
By changing a regular data partition to a bios_grub partition you may have corrupted it.

LVM is another different partitioning system for advanced systems. Often servers but also required if you want full drive encryption. You need different partition tools for LVM. It is a logical overlay to the physical MBR or gpt partitions.

With gpt partitioning you have to have either the ESP - efi system partition or the bios grub partition.I actually add both to all new drives. But now use UEFI to boot.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)

---

### Post by MadMax2 on 2015-12-16
This is a new system. I have had the old system for at least 10 years.
I'm digesting it it now.

[ATTACH=CONFIG]266189[/ATTACH]

$ sudo parted -l
Model: ATA WDC WD10EZEX-00W (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  538MB   537MB  fat32        EFI System Partition  boot
 2      538MB   794MB   256MB  ext2
 3      794MB   1000GB  999GB                                     lvm

---

### Post by oldfred on 2015-12-16
You have a new UEFI based system which can be UEFI or Legacy/BIOS/CSM.
You have partitions typical of a UEFI install with LVM. Cannot tell if encrypted or not.

How you boot install media UEFI or BIOS is how it installs. But then you must boot in same mode on system once installed and every time you boot live installer to make repairs. So you need to always boot in UEFI mode.
If Boot-Repair was asking for a bios_grub partition, you were attempting to install grub-pc for BIOS boot. You may want to totally reinstall grub using Boot-Repair's advanced options.
Be sure to tick the separate /boot and if encrypted mount or unencrypt system as updates need all your partitions.

---

### Post by MadMax2 on 2015-12-16
> **oldfred said:**
> By changing a regular data partition to a bios_grub partition you may have corrupted it.

I see it isn't checked so grub repair must have fixed it?

> **oldfred said:**
> LVM is another different partitioning system for advanced systems. Often servers but also required if you want full drive encryption. You need different partition tools for LVM. It is a logical overlay to the physical MBR or gpt partitions.

can I uncheck that in GParted?

---

### Post by MadMax2 on 2015-12-16
Maybe my boot repair was repaired when I reinstalled a second time as no bios_grub flag is ticked in gparted?

---

### Post by oldfred on 2015-12-16
Possibly, not sure how it would know data partition from bios_grub.

You can only use gparted on the physical partitions. And have to use LVM tools partition tools inside the physical partitions. I do not know LMV, but it becomes more complicated to maintain, but has some advantages for some advanced users.You cannot just convert back to standard partitions.

If you do not want or need full drive encryption, probably better to reinstall without LVM.

---

