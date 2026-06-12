---
title: "GRUB help - RAID-0 dual-boot install"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by Rack1600 on 2007-11-18
Having read through other threads, I feel I am getting somewhere now, but could do with some advice.

I have vista installed on a RAID-0 array (HW RAID from my gigabyte DS3 motherboard) and I decided that I wanted to install ubuntu on that partition as well.  So I made 30G of unpartitioned space, used Ubuntu 7.05 I (thought) installed ubuntu on that 30G partition.

Now when I boot I get GRUB - Error 22.

In Ubuntu Live I can see both the 160G RAID disks seperately as sda (Boot: *, HPFS/NTFS) and sdb (Doesn't Contain a Valid Partition Table).  

I also have 2 other hdd's:
sdc 250G has 
sdc1 (210GB, HPFS/NTFS)
sdc2 (30GB, Linux)

sdd 320G
sdd1 HPFS/NTFS

But I'm sure I created the partition on C: (Raid-0 drive in Vista), not my 250G drive - which appears to have Linux on it.

Why can't it Grub at least boot into Ubuntu?  Is it getting the drive numbering wrong somehow??

Any suggestions?

---

### Post by Rack1600 on 2007-11-18
OK, going back into the install, I did install on a second partition on the 250G drive (why was it there? I don't know) but it looks like Grub is still messed up somehow.

I tried Grub command line from Ubuntu Live, but I couldn't find any drives at all in grub>.  Most commands came back with errors.  *duh, I'm a noob.  I didn't sudo my grub.

Oh, and I tried cycling the HDD to boot from in bios, that didn't help.  not that I'm clear at all where grub is installed!  :?

---

### Post by Rack1600 on 2007-11-18
I decided to try and reinstall unbuntu again, this time using the entire 250G drive.  It is just now formatting the entire drive etc, and I have it as the boot drive now.  

Sorry for the trashy thread.  I'm still interested in installing it on the raid-0 drive, or at least finding out if it's possible when there's already Vista on the RAID-0 array.

---

### Post by RebounD11 on 2007-11-18
I also tried dual-booting Ubuntu (and many more other distros) with WinXP on a RAID 0 (also tried on a RAID 1). It was a total failure. However I could install OpenSuSE 10.3 on a RAID 0 partition (single boot) and worked great.

---

### Post by Pumalite on 2007-11-18
Read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Rack1600 on 2007-11-19
> **Pumalite said:**
> Read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Brilliant, that is my RAID issue.

However I tried last night to install ubuntu on my single 250G drive, and now it is saying there are no partitions on that drive, yet there are 4 partitions on my 320G drive.  I still get Error 22, despite booting from the disk I installed on (?).

I just want to get Vista back before i do anything else, check what's happening to my file system...  my concern is, if I put my Vista DVD in and go to recovery console, will it also not see my RAID array, and therefore not be able to run fdisk /mbr.

---

### Post by Pumalite on 2007-11-19
I'd get rid of Vista and Raid0(software, minimal performance advantage, terrible headaches)

---

### Post by Rack1600 on 2007-11-19
Well, I do like Vista generally, but it looks like I would have been better off with a single 500G spinpoint than 2 x 160G drives.  And the price difference is £10.

My main concern now is that my 320G media drive is still in tact, as FDISK is reporting several partitions on it... not good.

---

### Post by Pumalite on 2007-11-19
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Get Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
You can see your partitions with Gparted and do whatever you want with them. You can fix your MBR or boot any OS with Super Grub.

---

### Post by Rack1600 on 2007-11-20
Ok, I went into grub command line and edited the partition it was trying to boot from - ubuntu now boots.  BUT I have a d-link wifi card which isn't on the list (I looked) so no internet - I can't install DMRAID...

I also used my Vista CD to load into the command prompt for vista but that doesn't work with fixmbr or fixboot.  Apparantly there is command, c:/boot/bootsect.exe /NT60 all but that doesn't work for me.  About to try again - there is a bootsect.exe on the dvd I can use...

At least I can see that all of my drives are still in tact - I have all my documents and the RAID-0 is still there and detected as a vista install, I just can't boot from it.  Oh, and because GRUB doesn't detect the 2 160G drives as a single drive it won't let me boot from it.

---

