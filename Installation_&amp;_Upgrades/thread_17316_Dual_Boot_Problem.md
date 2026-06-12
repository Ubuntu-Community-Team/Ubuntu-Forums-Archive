---
title: "Dual Boot Problem"
date: 2005-02-27
forum: Installation &amp; Upgrades
---

### Post by Jonathan_ on 2005-02-27
I installed Ubuntu on a Machine, booted up and it worked fine.

I then installed Windows XP on a different partition and during the install it said it had to make the linux partition inactive, if there were problems with linux booting up, try making the partition active in "control panel - administrative tools - computer management - disk management" - but I am unable to do this as 'make active' is faded out and not 'clickable'

So basically Windows loads all the time and I dont get a choice to choose Ubuntu. Any ideas?

---

### Post by alastair on 2005-02-27
XP's overwritten your boot sector (MBR).

You need to get into an unbuntu prompt and reinstall the grub bootloader. But you will have to make sure that XP is listed in the grub config file i.e. something like :

title XP
        rootnoverify (hd0,0)
        chainloader +1

which would be for XP on /dev/hda1.

NOTE - this is DANGEROUS and might lose ALL your data. Use at your own risk - research!

To reinstall grub, boot an ubuntu CD and get to a prompt e.g. CTRL+ALT+F1 (or whatever).
mount the root unbuntu partition e.g.

mkdir /mnt/root
mount /dev/hda2 /mnt/tmp

Then, perhaps, chroot, to this :

chroot /mnt/tmp

CHECK the grub config file /boot/grub/menu.lst and make sure XP is listed and the right partition.

Reinstall grub :

grub-install /dev/hda

As I said, this is dangerous. Please be careful.

---

### Post by Jonathan_ on 2005-02-28
What if I reinstalled Ubuntu... would it then work properly? I've only just done an install, so I wouldnt loose anything apart from half an hour of my time or so.

---

### Post by lao_V on 2005-02-28
[QUOTE=Jonathan Steel]What if I reinstalled Ubuntu... would it then work properly? I've only just done an install, so I wouldnt loose anything apart from half an hour of my time or so.[/QUOTE]

The best way to have dual boot system is to install XP first and then Ubuntu!

---

### Post by jsgotangco on 2005-02-28
That's right just install XP first then install Ubuntu. Proceed with your installation of Ubuntu and Grub will setup by itself. The default selection would be Ubuntu kernel when Grub starts.

In some installations, XP/2000 can't overwrite the MBR during setup so you have to fdisk /mbr on a dos floppy to fix the mbr and let windows take over. then just install linux like you used to.

---

### Post by ohman11 on 2005-02-28
[QUOTE=jsgotangco]That's right just install XP first then install Ubuntu. Proceed with your installation of Ubuntu and Grub will setup by itself. The default selection would be Ubuntu kernel when Grub starts.

In some installations, XP/2000 can't overwrite the MBR during setup so you have to fdisk /mbr on a dos floppy to fix the mbr and let windows take over. then just install linux like you used to.[/QUOTE]
 I am interested too in loading ubutu on my laptop witht winxp but I am not sure how to prepare the drive for both operating systems.

---

### Post by ytseshred on 2005-02-28
I also had some trouble successfully installing a dual boot Windows XP w/ Ubuntu.

First I had tried to partition the drive as follows (102 GB):
Partition 1: 76 GB, /windows, FAT32, bootable flag on
Partition 2: 20 GB, /, ext3 w/ journaling, bootable flag on
Partition 3: 6 GB, swap, bootable flag off

After reading some of these articles on the forum, I see people usually have some space for /home as well, usually more than under /.  Does that make a difference?

Now for the main question/problem:

1
=
I wrote the partitions, and then installed Windows XP w/o converting the filesystem to NTFS, although when it restarts after first install section, it says "NTLDR missing", and then fails to boot.

I googled this problem, and read that under XP, this problem will occur if you're installing on a FAT32 file system.  So is it impossible to successfully install XP under FAT32, so that when booted in ubuntu it could read the /windows partition?

2
=
Before I got to another computer so I could look up the problem, I tried several things, and finally got windows to successfully install under the same partitioning segments as before, but in the windows install I quick formatted the filesystem to NTFS.  Windows now booted successfully and finished installing, but GRUB was overwritten.

Previously, I had gotten to this point, and I was confused what to do when I put the Ubuntu CD back in, because it didn't seem to be able to skip the partitioning segment.  I forget the exact message/warning it gave, but if someone has gotten to this part, and knows what I'm talking about, can they walk me through what I do at the partition sequence after selecting 'Manually partition...'

Thanks.

---

