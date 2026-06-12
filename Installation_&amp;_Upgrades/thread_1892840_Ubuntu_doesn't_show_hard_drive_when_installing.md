---
title: "Ubuntu doesn't show hard drive when installing"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by joshj70 on 2011-12-08
I have a 250gb SATA drive that I am trying to dual boot with Ubuntu and Windows. Windows is installed and works fine, but when I load up my live disk from my jump drive and I try to install it doesn't list anything in the partition table. I can mount and access the hard drive and I can manipulate it with GParted but no matter what I do it doesn't show up when installing. Any ideas?

---

### Post by fantab on 2011-12-08
> **joshj70 said:**
> I have a 250gb SATA drive that I am trying to dual boot with Ubuntu and Windows. Windows is installed and works fine, but when I load up my live disk from my jump drive and I try to install it doesn't list anything in the partition table. I can mount and access the hard drive and I can manipulate it with GParted but no matter what I do it doesn't show up when installing. Any ideas?

Post the screen shot of your HDD partitions taken from windows, without this information it will be only guess work on our part.

---

### Post by joshj70 on 2011-12-08
Here is the partition table from Windows and info from fdisk.

---

### Post by oldfred on 2011-12-08
You are showing your Windows partition sda1 & unallocated. Have you tried creating partitions in advance & using manual install/Something Else to use the partitions. You should be able to create the partitions from the installer, but I always create in advance.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by joshj70 on 2011-12-08
I have tried making manual partitions, also I am trying to install 10.04, sorry I didn't mention that before. But no matter what the partitions are it never shows them in the install, it's always empty.

---

### Post by oldfred on 2011-12-09
Try running chkdsk with a Windows repairCD on the NTFS partition.

Once I had a working XP in sda and was installing in sdc. Gparted would take forever and never show sda. I then ran chkdsk on the Windows NTFS partitions and gparted then saw sda immediately. XP also booted slightly faster, but it still booted 2 or 3 times longer than Ubuntu.

Also was drive ever part of a RAID configuration or have you used the RAID setting in BIOS? If so meta data remains on drive that can interfer with installing. That also can be removed. 

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by james2b on 2011-12-09
There is a tool to re-build the drive partition table which is not to hard to use found here; [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) ,and is also on this disk; [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by joshj70 on 2011-12-09
I took it out of a old server I had that used RAID, I will try to remove the meta data as you suggested and let you know what happens.

---

### Post by joshj70 on 2011-12-09
The command you posted kept giving me errors, but I did some more research and I found a code that worked,
```
dd if=/dev/zero bs=1M seek=150000 skip=150000  of=/dev/sda
```

@james2b My friend has a crashed Linux partition so I will try those programs with it.

I am installing Ubuntu right now, thank you for the help, it's greatly appreciated.

---

### Post by darkod on 2011-12-09
Just for reference, you just needed to remove the raid meta data, with the command oldfred gave:
sudo dmraid -E -r /dev/sda

The installer ignores disks with raid meta data expecting you to run raid if you have meta data on the disk.

---

