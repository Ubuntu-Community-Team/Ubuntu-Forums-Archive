---
title: "Howto install Windows on an existing Kubuntu/machine?"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by odinb on 2008-01-29
Hi!

How does one install windows while still maintaining the current Kubuntu-install on my machine?

I need to install winXP due to a windows-app that is not compatible with Wine, and that needs hardware-access (USB-flashing app for phones).

Kubuntu 7.10 is already installed and running just fine!

If I use Gpatrted and create a partition for windows and tell winXP to install there, I assume it will kill grub. Is this a corect assumption?
Also, will my linux-partitions stay intact during a winXP install (assuming I tell WinXP to install in the newly created empty partition)?

Is there an easy way to get Grub back and get both OSes to run as a dual-boot machine (with kubuntu as default os ofcourse) in this case?

---

### Post by taurus on 2008-01-29
The best way is to download GParted LiveCD and boot from it.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Then, use gparted from the CD to resize your Kubuntu, making room for window.  Then, boot with the window CD and install it on the empty partition.  And of course, windows will erase GRUB from MBR so you need to install it again once you have finished installing windows.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

Of course, _ALWAYS_ back up your important files first before you do any resizing.

---

### Post by odinb on 2008-01-29
Thanks!

Will try it later when I get home....

---

### Post by odinb on 2008-02-01
Created a 15GB empty space for windows with GParted, rebooted from Windows CD, pointed to the empty space, partitioned, and started the install.

Windows copies a bunch of files as usual, then reboots. At reboot it gives me an error about error on partition.

I then ran the supergrubdisk, and was able to boot Linux again. While editing my menu.lst, I realised I did not know what I should write as the root (i.e. hd0.0).

Ran the command sudo fdisk -l and got the following:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb23eb23e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10336    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xd7bbe615

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17702   133821418+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *       17703       19868    16374960    7  HPFS/NTFS
/dev/sdb3           19869       20674     6080602+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sdb5           19869       20674     6080571   82  Linux swap / Solaris

The part "Partition x does not end on cylinder boundary." sounds scary to me!!

What do I do???

---

### Post by odinb on 2008-02-02
Bump!

---

### Post by Partyboi2 on 2008-02-02
You could use something like testdisk  to try and fix the cylinder boundary.
```
 sudo apt-get install testdisk
```

---

### Post by odinb on 2008-02-04
Thanks! Only problem is that testdisk claims it cannot recover my swap-space.....

Ended up disabling my swap, and delelting all partitions except sdb1using fdisk , and then re-created them using the same tool. After this I re-enabled the swapdisk.

Will see if I can install windows later today...

New printout of the disk shows no overlap and no cylinder boundary errors:

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
60 heads, 63 sectors/track, 82693 cylinders
Units = cylinders of 3780 * 512 = 1935360 bytes
Disk identifier: 0xd7bbe615

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       70805   133821418+  83  Linux
/dev/sdb2           70806       72873     3908520   82  Linux swap / Solaris
/dev/sdb3           72874       82693    18559800    7  HPFS/NTFS

---

### Post by odinb on 2008-02-07
After trying to install windows on partition3, I get the following error:
Error 18: Selected cylinder exceeds maximum supported by BIOS

Any idea on this one?

Running testdisk, it tells me this:

Disk /dev/sdb - 160 GB / 149 GiB - CHS 82693 60 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Linux                    0   1  1 70804  59 63  267642837
 2 P Linux Swap           70805   0  1 72872  59 63    7817040

Warning: Bad starting head (CHS and LBA don't match)
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 60 (HD)
 3 * HPFS - NTFS          72873   0  1 82692  59 63   37119600

Warning: Bad starting head (CHS and LBA don't match)


Any idea on how to fix this?

---

### Post by Partyboi2 on 2008-02-07
create a /boot (approx 100mb) partition and see if that works.
If that does not work look at [this]("http://www.google.com.au/search?hl=en&rlz=1B3GGGL_enUS260US260&q=Error+18%3A+Selected+cylinder+exceeds+maximum+supported+by+BIOS+ubuntu&btnG=Search&meta=")

---

### Post by odinb on 2008-02-07
Editing to answer my own questions:

Sorry for being a n00b, but what do I do with this 100mb /boot-partition?

First, where on the disk do I create it (first, last, in the middle, does it matter)?

Answer: 
It has to be within the first 512MB on the disk for (E)IDE disks on older machines orwithin 8GB on others.

Secondly, do I add/copy anything to it?

Answer: 
Your /boot should be located here.

Third, do I reference it somewhere, like the grub menu-list?

Answer: 
Doing the previous bullet, this is also taken care of!

Thanks!

Result:
So in other words, I have to reinstall my whole system...

---

### Post by odinb on 2008-02-13
Hi!

Update on my progress:

My setup:
Laptop HP NW8440 with USB-Drive Maxtor OneTouch 3 Mini 160GB.
Partitioned as follows:
Partition 1 is 15GB with Windows XP SP2.
Partition 2 is 2GB Swap for Linux.
Partition 3 is 30GB for / for Linux system.
Partition 4 is 110GB (the rest) for /home for Linux.
System is set to boot from USB primarily, and internal drive, even if present, is usually not used.
System was booting up for 3 days using grub.

Install windows first, then Linux.
Make sure you state yes when grub asks to overwrite MBR to get a dual-boot system from grub-menu.

Windows XP now boots fine from USB, after I found this webpage to modify my Windows installdisk to boot from USB: [http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176)

It has worked through many reboots since Sunday (Windows-sickness, reboot after every app install/system change...).

Well it did untill I installed a USB driver for an Omnikey CardMan 3121 yesterday....

See if I can solve that one.

---

