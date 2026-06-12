---
title: "Multiboot Help Ubuntu/WinXP/Win7"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by seraieis on 2010-03-02
Hello all!

I'm a recent convert to Linux and am having trouble setting up a multiboot environment. Origionally, I had Windows 7 on my computer, and then I created a new partition and installed Ubuntu 9.10 along side of it, and the two played nicely. Then, I installed Windows XP on another partition, and like the typical younger sybling, he ate my boot loader. With the LiveCD I was able to reinstall GRUB1.97 but now I can't access either of the Windows partitions.  At this point, I think I have all the information I need, but I have no idea what to do with it.

Here's my setup:

SATA Drive 1, Partition 1 = Windows 7
SATA Drive 1, Partition 2 = Windows XP
IDE Drive 1, Partition 1 = Ubuntu

Any advice on how I get GRUB and the boot.ini files working in harmony again?


daniel@daniel-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x445a445a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18707   150263946   83  Linux
/dev/sda2           18708       19457     6024375    5  Extended
/dev/sda5           18708       19457     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18cf299a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       21729   174532246+   7  HPFS/NTFS
/dev/sdb2           21729       24322    20826112    7  HPFS/NTFS

---

### Post by darkod on 2010-03-02
You should have kept windows bootloader on the windows disk and grub2 on the ubuntu disk. Also, when installing windows, remember: It ALWAYS puts the bootloader on the disk set as first boot option. It was enough to set the windows disk as first boot option and grub2 wouldn't have been deleted, not if it was on the ubuntu disk.

The first thing to try is:

sudo update-grub

If that doesn't help find both windows installs, run the boot info script as explained here and post the content of your results file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by tommcd on 2010-03-02
First, be sure to get all the updates for Ubuntu. There have been several updates for grub2 (i.e., grub1.97) since Ubuntu 9.10 came out. So be sure you are running with the latest grub2 updates.
Then for the (hopefully) quick and easy fix, open a terminal and run:
```
sudo update-grub
```
Hopefully this should add entries for your XP and 7 installs and allow you to boot them.
If that doesn't not work, then you may need to add custom entries for XP and 7 in the /etc/grub.d/ directory like this:
[https://wiki.ubuntu.com/Grub2#User-defined%20Entries](https://wiki.ubuntu.com/Grub2#User-defined%20Entries)
Since grub2 originally detected your Windows 7 install though, it should detect it again after running update-grub.

And welcome to the Ubnuntu forums!

---

### Post by darkod on 2010-03-02
The main worry is that windows combines boot files for two versions. And in case XP is installed after 7 I don't know how exactly it would work.
Running the script will show the boot files and their location, so we will know more.

---

### Post by seraieis on 2010-03-03
> **darkod said:**
> You should have kept windows bootloader on the windows disk and grub2 on the ubuntu disk. Also, when installing windows, remember: It ALWAYS puts the bootloader on the disk set as first boot option. It was enough to set the windows disk as first boot option and grub2 wouldn't have been deleted, not if it was on the ubuntu disk.

The first thing to try is:

sudo update-grub

If that doesn't help find both windows installs, run the boot info script as explained here and post the content of your results file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)


I've attached my results file. From the looks of it, I have too many boot sectors (and not a CLUE what to do!).

---

### Post by darkod on 2010-03-04
> **seraieis said:**
> I've attached my results file. From the looks of it, I have too many boot sectors (and not a CLUE what to do!).

Grub2 is on /dev/sda which is where it's supposed to be.
You have old grub2 on /dev/sdb which won't work any more. You could return generic mbr on that disk, it's the windows disk anyway.

Boot ubuntu and execute:

sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr

That will write generic mbr on /dev/sdb.

After that try to boot from /dev/sdb, the 200GB disk. My guess is that you will not be able to boot any windows. The windows boot files seem broken, and that's the reason grub2 can't boot them too. Grub2 just passes the job on to the windows boot files. If they don't work, it doesn't work.

You could try repairing the windows boot process for both XP and 7 but I'm not sure in which order to do it. I never had two windows versions at once.

---

### Post by oldfred on 2010-03-04
If your win7 boots when you try to directly boot sdb, then you can add the missing files to the XP partition.

Similar thread on reinstall XP files
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

If you move the boot flag to the XP partition (gparted will do this), you can test if your XP then boots as the windows boot loader in sdb only looks for a boot flag (active partition) and jumps there to boot.

---

