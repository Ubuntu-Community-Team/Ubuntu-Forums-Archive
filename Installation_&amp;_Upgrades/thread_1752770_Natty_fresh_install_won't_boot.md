---
title: "Natty fresh install won't boot"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by Bearly Able on 2011-05-08
Hi all,

I had a problem yesterday with 10.10, which suddenly refused to boot for no apparent reason.  (See thread [here]("http://ubuntuforums.org/showthread.php?t=1751541").)

I decided to do a fresh install of Natty, as the quickest and easiest solution.  However, I still can't boot.  If I try to boot the first option ( kernel 2.6.35-28 ) I get ```
error: environment block too small
```followed after a few seconds by ```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem does not have requested /sbin/init.
No init found. Try passing init =bootarg.
```
Then it drops to BusyBox.

If I try using the recovery option, I just get more of the same, and it ends as above.

Apart from "environment block too small", this is basically the same problem that developed in Maverick yesterday, and which prompted me to do a fresh install to fix it.  I'm now totally stumped as to what to do next.

Any assistance would be most appreciated.

---

### Post by kansasnoob on 2011-05-08
Well lets start with a look at the partitioning arrangement:

```
sudo parted -l
```

---

### Post by Bearly Able on 2011-05-08
Hi Kansasnoob, and thanks for your help.  Here's the info:```
Model: ATA WDC WD1600JS-00N (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  36.7GB  36.7GB  primary   ntfs         boot
 2      36.7GB  160GB   123GB   extended               lba
 5      36.7GB  68.2GB  31.5GB  logical   ntfs
 6      68.2GB  102GB   33.9GB  logical   ntfs
 7      102GB   137GB   34.4GB  logical   ntfs
 8      137GB   160GB   23.5GB  logical   ntfs


Model: ATA WDC WD1600AAJS-0 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  84.5GB  84.5GB  primary   ext4            boot
 2      84.5GB  160GB   75.5GB  extended
 6      84.5GB  152GB   67.1GB  logical   ext4
 7      152GB   154GB   2141MB  logical   linux-swap(v1)
 5      154GB   160GB   6290MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                           
```
The first drive has Windows XP, but I've been unable to boot that for months (ever since I installed Maverick & Grub2).
The partition sizes on the Ubuntu drive are what the installation gave by default; I didn't change anything because I don't know enough to make any decision about it.  I've always gone with default settings in the past without problem.

---

### Post by Bearly Able on 2011-05-08
I came across Kansasnoob's excellent guide [http://ubuntuforums.org/showpost.php?p=10778491&postcount=55]("http://ubuntuforums.org/showpost.php?p=10778491&postcount=55") and tried using Super GRUB2 Disk, as suggested.  That booted Natty for me, and I noticed that the kernel number was not one shown on my existing GRUB menu.  When I looked again at the partition info, I realised I now have boot flags on both drives, which I didn't have before.  The new install seems to have put GRUB on my Ubuntu drive, but the BIOS was set to boot from the other drive, so I was still getting the out-of-date menu.  I followed Step 2 of the guide, just to be on the safe side, reset the BIOS and bingo! we're up and running.

Many thanks to Kansasnoob for that very clear and helpful guide.

---

