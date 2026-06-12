---
title: "Creating an EFI Partition."
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by BlinkinCat on 2013-08-14
Hi all,

I will soon be installing a sole Xubuntu installation on a new computer. As I plan to have a home partition, I will be opting for manual partitioning. I am a little confused about the wording of Creating an EFI Partition in [UEFI]("https://help.ubuntu.com/community/UEFI").

1. Can the EFI Partition be set up directly from the installer, or will I need to use GParted as suggested in (2)? 

2. If I use GParted, I assume that I could set up the other partions at the same time. Is this so? 

3. If none of the above, I would appreciate a brief summary of at what stage the EFI Partition is normally created.

Thank you - :)

---

### Post by oldfred on 2013-08-14
I have always preferred to create partitions in advance. If not installing Windows which has some unique requirements with UEFI, you can follow this suggestion. Adjust to which ever partitions you may want.

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I suggest both efi & bios_grub and then either can be used. But you really only need efi if UEFI booting or bios_grub if BIOS booting.

  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

    For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

But I do not use a separate /home but still have only 25GB for /. I have large data partitions for all my data and link the folders in those partitions back into /home.

---

### Post by Bucky Ball on 2013-08-14
*Thread moved to **Installation & Upgrades**.*

---

### Post by BlinkinCat on 2013-08-15
Thanks very much oldfred, for your concise explanation.

Cheers - :)

BlinkinCat

---

