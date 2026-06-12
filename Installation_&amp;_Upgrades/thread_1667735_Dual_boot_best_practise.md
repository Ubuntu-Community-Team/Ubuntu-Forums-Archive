---
title: "Dual boot best practise"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by Biscuity on 2011-01-15
Hi

System: Windows 7 32bit Ultimate (clean install), 1x SATA hard drive, 1x Windows partition + the usual hidden WinRE partition.

I'd like to try Ubuntu on my main desktop. It runs ok as a Live CD. The desktop currently runs Windows 7 32bit Ultimate & is pretty well 100% reliable. I've been reading some of the problems people have got with bootloaders & I'm getting the collywobbles about it as I don't want to mess up my W7 installation.

Installing a 2nd hard drive to run Ubuntu seems to create it's own set of problems on this forum, so what is the most reliable way to set up dual boot? Should I instead build another pc for Ubuntu & use a KVM switch?

Thanks.

---

### Post by Quackers on 2011-01-15
First, do you have a Windows repair disc? If not, make one. Control Panel > Backup & Restore Centre > in the left pane select "create recovery cd". This is not a set of recovery dvd's! This is a repair cd.
Second, do you have a set of recovery dvd's? If not make them. They are worth having - in fact make them twice! and check that they work.
Third backup independently any data you don't want to lose.
Have a look in Windows dsik management screen. Confirm that only 2 or 3 primary partitions are in use. 4 would be bad!
If you need to create space for Ubuntu to install in to you may need to shrink the C: partition. You can do this from the same screen by right-clicking on the C: partition and selecting "shrink".
*** You should defragment Windows before shrinking the C: drive. Preferrably twice!
Once the sapce for Ubuntu is created you can boot from the Live cd/usb and install (after trying Ubuntu first, to make sure everything works). Select the manual partitioning option and create partitions for Ubuntu from the unallocated space now available.

---

### Post by Biscuity on 2011-01-15
Thanks for your reply.

2 Windows partitions are in use.

I use Acronis for backup to a USB drive, but I will also set up the repair CD as suggested.

My disk is 300gb, with about 200gb free. How many partitions & of what approximate size should I set up for Ubuntu? Would it be better to install a 2nd hard drive instead?

---

### Post by Quackers on 2011-01-15
You say you have 200GB free, but is that unused space within C: 
If so, then that's not space that Ubuntu can install into. There needs to be unallocated space, or partitions created for Ubuntu.
Disc use is a question for you to answer. It would depend on how much space you need for Windows and for Ubuntu.
The basic Ubuntu installation uses one partition for /root and usually a swap partition. These are usually within an extended partition.
A separate /home partition can also be created, if required.
Obviously the size of your /root partiton will depend on whether you are having a separat /home partition.

---

### Post by kansasnoob on 2011-01-15
Glad you asked. You didn't mention which version of Ubuntu you'll be installing but, if it's 10.10, I'd particularly point you here first (check out post#1 and post #15):

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

And you might want to check out this bug report and it's two duplicates:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Basically if you choose the option to "Install alongside other operating systems” and get to this screen:

[ATTACH]181172[/ATTACH]

**[COLOR="Red"]If you click on either "Use entire partition" or "Use entire disc" you will very likely wipe out your Windows OS and any data contained therein![/COLOR]**

No need to panic because you planned ahead and asked for advice :D

My personal suggestion is to first boot the Live CD and from the live desktop go to terminal and post the output of these two commands:

```
sudo fdisk -l
```

```
sudo parted -l
```

BTW that's a lower case L at the end of both.

Then one of us will take the time to explain Ubuntu's drive and partition designations, and discuss possible partitioning arrangements.

While I personally prefer resizing Vista and Win7 partitions with their own partitioning tools rather than using Gparted this is my preferred method of dual/multi-booting:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

I must go play in the snow and the mud so I may be unavailable for a while.

---

### Post by Ad@m on 2011-01-15
> **Biscuity said:**
> 
Installing a 2nd hard drive to run Ubuntu seems to create it's own set of problems on this forum, so what is the most reliable way to set up dual boot? Should I instead build another pc for Ubuntu & use a KVM switch?


I run a 2 disk setup problem free. Most problems occur due to a misunderstanding with the grub loader.

For a fool proof method physically setup your disks as follows,

Disk 1 --- SATA 1 /dev/sda ------ Ubuntu / Linux
Disk 2 --- SATA 2 /dev/sdb ------ Windows 7 / Vista / XP

With this setup, when you install Ubuntu it will by default keep grub on /dev/sda and not alter your Windows drive /dev/sdb.

Both drives will therefore be capable of booting independently.

---

### Post by Biscuity on 2011-01-15
Here are the results:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1fb2852b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       36482   292931584    7  HPFS/NTFS

```

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD3000GLFS-0 (scsi)
Disk /dev/sda: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   300GB  300GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

```

---

### Post by Biscuity on 2011-01-15
> **Ad@m said:**
> I run a 2 disk setup problem free. Most problems occur due to a misunderstanding with the grub loader.

For a fool proof method physically setup your disks as follows,

Disk 1 --- SATA 1 /dev/sda ------ Ubuntu / Linux
Disk 2 --- SATA 2 /dev/sdb ------ Windows 7 / Vista / XP

With this setup, when you install Ubuntu it will by default keep grub on /dev/sda and not alter your Windows drive /dev/sdb.

Both drives will therefore be capable of booting independently.

I like your idea of 2 disks. If I decided to remove Ubuntu, I could remove the drive & my Windows installation would be unaffected by the bootloader?

---

### Post by Biscuity on 2011-01-15
> **Ad@m said:**
> I run a 2 disk setup problem free. Most problems occur due to a misunderstanding with the grub loader.

For a fool proof method physically setup your disks as follows,

Disk 1 --- SATA 1 /dev/sda ------ Ubuntu / Linux
Disk 2 --- SATA 2 /dev/sdb ------ Windows 7 / Vista / XP

With this setup, when you install Ubuntu it will by default keep grub on /dev/sda and not alter your Windows drive /dev/sdb.

Both drives will therefore be capable of booting independently.

I like your idea of 2 disks. If I decided to remove Ubuntu, I could remove the drive & my Windows installation would be entirely unaffected by the bootloader?

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked computers. This is because I have an SBS2003 premium server running ISA 2004. Although I can put the proxy settings within Firefox & get to work - with having to install my network username & password every time I run it - but it doesn't seem to accept the system wide proxy settings for other things - like the weather app, searching for printer drivers etc. A Windows pc would use the ISA client & this handles Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers & just use it for my lower spec non-networked computers & my oldish laptop.

Thanks

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked computers. This is because I have an SBS2003 premium server running ISA 2004. Although I can put the proxy settings within Firefox & get to work - with having to install my network username & password every time I run it - but it doesn't seem to accept the system wide proxy settings for other things - like the weather app, searching for printer drivers etc. A Windows pc would use the ISA client & this handles Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers & just use it for my lower spec non-networked computers & my oldish laptop.

Thanks

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked  computers. This is because I have an SBS2003 premium server running ISA  2004. Although I can put the proxy settings within Firefox & get to  work - with having to install my network username & password every  time I run it - but it doesn't seem to accept the system wide proxy  settings for other things - like the weather app, searching for printer  drivers etc. A Windows pc would use the ISA client & this handles  Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers  & just use it for my lower spec non-networked computers & my  oldish laptop.

Thanks

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked  computers. This is because I have an SBS2003 premium server running ISA  2004. Although I can put the proxy settings within Firefox & get to  work - with having to install my network username & password every  time I run it - but it doesn't seem to accept the system wide proxy  settings for other things - like the weather app, searching for printer  drivers etc. A Windows pc would use the ISA client & this handles  Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers  & just use it for my lower spec non-networked computers & my  oldish laptop.

Thanks

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked  computers. This is because I have an SBS2003 premium server running ISA  2004. Although I can put the proxy settings within Firefox & get to  work - with having to install my network username & password every  time I run it - but it doesn't seem to accept the system wide proxy  settings for other things - like the weather app, searching for printer  drivers etc. A Windows pc would use the ISA client & this handles  Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers  & just use it for my lower spec non-networked computers & my  oldish laptop.

Thanks

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked  computers. This is because I have an SBS2003 premium server running ISA  2004. Although I can put the proxy settings within Firefox & get to  work - with having to install my network username & password every  time I run it - but it doesn't seem to accept the system wide proxy  settings for other things - like the weather app, searching for printer  drivers etc. A Windows pc would use the ISA client & this handles  Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers  & just use it for my lower spec non-networked computers & my  oldish laptop.

Thanks

(Good grief, what is it with this site! Times out constantly!)

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked  computers. This is because I have an SBS2003 premium server running ISA  2004. Although I can put the proxy settings within Firefox & get to  work - with having to install my network username & password every  time I run it - but it doesn't seem to accept the system wide proxy  settings for other things - like the weather app, searching for printer  drivers etc. A Windows pc would use the ISA client & this handles  Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers  & just use it for my lower spec non-networked computers & my  oldish laptop.

Thanks

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked  computers. This is because I have an SBS2003 premium server running ISA  2004. Although I can put the proxy settings within Firefox & get to  work - with having to install my network username & password every  time I run it - but it doesn't seem to accept the system wide proxy  settings for other things - like the weather app, searching for printer  drivers etc. A Windows pc would use the ISA client & this handles  Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers  & just use it for my lower spec non-networked computers & my  oldish laptop.

Thanks

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked  computers. This is because I have an SBS2003 premium server running ISA  2004. Although I can put the proxy settings within Firefox & get to  work - with having to install my network username & password every  time I run it - but it doesn't seem to accept the system wide proxy  settings for other things - like the weather app, searching for printer  drivers etc. A Windows pc would use the ISA client & this handles  Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers  & just use it for my lower spec non-networked computers & my  oldish laptop.

Thanks

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked  computers. This is because I have an SBS2003 premium server running ISA  2004. Although I can put the proxy settings within Firefox & get to  work - with having to install my network username & password every  time I run it - but it doesn't seem to accept the system wide proxy  settings for other things - like the weather app, searching for printer  drivers etc. A Windows pc would use the ISA client & this handles  Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers  & just use it for my lower spec non-networked computers & my  oldish laptop.

Thanks

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked  computers. This is because I have an SBS2003 premium server running ISA  2004. Although I can put the proxy settings within Firefox & get to  work - with having to install my network username & password every  time I run it - but it doesn't seem to accept the system wide proxy  settings for other things - like the weather app, searching for printer  drivers etc. A Windows pc would use the ISA client & this handles  Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers  & just use it for my lower spec non-networked computers & my  oldish laptop.

Thanks

(what is it with this site - an hour to make a post!)

---

### Post by Biscuity on 2011-01-15
Update:
 
 I don't think I can successfully install Ubuntu on any of my networked  computers. This is because I have an SBS2003 premium server running ISA  2004. Although I can put the proxy settings within Firefox & get to  work - with having to install my network username & password every  time I run it - but it doesn't seem to accept the system wide proxy  settings for other things - like the weather app, searching for printer  drivers etc. A Windows pc would use the ISA client & this handles  Internet access.
 
 I'll therefore scrub the idea of running Ubuntu on my regular computers  & just use it for my lower spec non-networked computers & my  oldish laptop.
 
 Thanks

(what is it with this site - an hour to make a post!)

---

### Post by Biscuity on 2011-01-15
Update:

I don't think I can successfully install Ubuntu on any of my networked  computers. This is because I have an SBS2003 premium server running ISA  2004. Although I can put the proxy settings within Firefox & get to  work - with having to install my network username & password every  time I run it - but it doesn't seem to accept the system wide proxy  settings for other things - like the weather app, searching for printer  drivers etc. A Windows pc would use the ISA client & this handles  Internet access.

I'll therefore scrub the idea of running Ubuntu on my regular computers  & just use it for my lower spec non-networked computers & my  oldish laptop.

Thanks

(what is it with this site - an hour to make a post!)

---

### Post by Ad@m on 2011-01-15
> **Biscuity said:**
> I like your idea of 2 disks. If I decided to remove Ubuntu, I could remove the drive & my Windows installation would be unaffected by the bootloader?

Yes, each drive can boot without the presence of the other drive.

---

