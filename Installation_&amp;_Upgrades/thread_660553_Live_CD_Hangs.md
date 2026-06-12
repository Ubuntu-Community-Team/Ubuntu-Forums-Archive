---
title: "Live CD Hangs"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by robert.e.dean.jr on 2008-01-06
Hello all.  I am trying to install 7.10.  However when I boot from the live cd it hangs shortly after getting to the desktop. I have not received any error messages.

Here are the specs on my computer:
Intel Pentium D 3.4 GHz
2 Gb Ram
Foxconn 975X7AB motherboard
Segate 250 Gb SATA3 hdd-about a year old, but checks good through check disk. (10Gb for XP in NTFS, 95Gb for Vista in NTFS, 30 Gb for Ubuntu in ext3, and 97Gb storage in FAT32)
Segate 500 Gb SATA3 hdd-just installed today for storage only in NTFS.
Diamond Radeon X550 video card
LG GSA-H22L Super-multi DVD-rom
Lite-on LH-20A1P Super-multi DVD-rom

When I downloaded the .iso file I did run it through winmd5sum and it checked out fine. Burnt the image in InfraRecorder to a CD-R at the lowest speed avaliable to me (8x). Rebooted the machine and booted from the cd.  Ran the disk check on the cd and it came back good.  Tried to load from both the install and the safe graphics modes.

---

### Post by robert.e.dean.jr on 2008-01-06
Oh should have mentioned that I have had the same results with OpenSuse 10.3 and Fedora 7.0.

---

### Post by Partyboi2 on 2008-01-06
Try burning at even a lower speed x4 or less. If that does not work you could try the alternate cd which is a text installer.
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by robert.e.dean.jr on 2008-01-06
> **Partyboi2 said:**
> Try burning at even a lower speed x4 or less. If that does not work you could try the alternate cd which is a text installer.
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

8x was the lowest speed that InfraRecorder would allow my DVD drive to burn at.  I will give the text installer a shot.

******Update*******
Just finished downloading the alternate cd.  Checked the download with winmd5sum and it was good.  Currently burning the image to a CD-R.  InfraRecorder will still only burn at 8x for the slowest speed.  Will update once the disk is finished burning and I attempt to install.

---

### Post by robert.e.dean.jr on 2008-01-07
Finished burning the image to disk.  The winmd5sum was good. Booted machined from the disk.  Ran the disk check and got the following:

Integrity test failed
The  ./pool/restricted/n/nvidia-kernel-common/nvidia-kernel-common_20051028+1ubuntu7_all.deb file failed the MD5 checksum verification.  Your CD-ROM or this file may have been corrupted.

I will try this disk in another computer and run the disk check again and see if I get the same results.

---

### Post by Partyboi2 on 2008-01-07
Try using another burn program. imgburn is a good one
[http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by robert.e.dean.jr on 2008-01-07
Tried the disk in another computer and got the same error as before.  While I know that this does not completely rule out a hardware issue I am correct in thinking that it may be a software or driver issue?  I am now thinking that it may be a conflict between my video card (ATI) and the Ubuntu included video driver (nvidia).  What, if anything, can I do to confirm and fix this or find out if it something else?

---

### Post by robert.e.dean.jr on 2008-01-07
I will give imgburn a try.

---

### Post by robert.e.dean.jr on 2008-01-07
Burned the image to the disk using imgburn at 1x.  Booted the machine from the cd.  Ran the disk check came back fine.  Decided to run memtest just to make sure that I don't have a bad stick of RAM.  I will update once memtest finishes, and if no errors will try installing 7.10.

---

### Post by robert.e.dean.jr on 2008-01-07
Ok let memtest run for 7 hours and 30 minutes no errors. Rebooted the machine and load from the live cd. Everything quit responding after the desktop loaded.  I could see the icon to install, but the mouse and keyboard would not respond.  I have burnt a new copy of the text installer at 1x in imgburn. Ran the new disk through disk check and it came back as valid.  

I did receive an error that a usb device was not accepting the address error 71. Ok appears that the text install is going to work.  

Does anyone know of some good instructions on how to use the text install as I am a first time Linux user.

---

### Post by robert.e.dean.jr on 2008-01-07
Got Ubuntu to install, but it hangs while starting up after inputting username and password. It does not even get to the desktop. 

Grub appears to load just fine, no errors are shown.

Any ideas on what to try?

---

### Post by bharadwaj on 2008-01-07
> **Partyboi2 said:**
> Try burning at even a lower speed x4 or less. If that does not work you could try the alternate cd which is a text installer.
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)
Are you sure whether the problem is with the 4x or writing speed issue of CD cause i don't think there would be any reason for that to happen. Instead burning the alternate CD would fix the problem even my system doesn't suppoert live CD I had to install from alternate CD

---

### Post by robert.e.dean.jr on 2008-01-08
Ok live cd bad!!  I was able to install from the alternate cd.  However when the install completed and I rebooted, as instructed, all I could do is input my username and password. The desktop did not load.  I had to do a hard reboot with the same results.  After I did the second hard reboot I was able to get the desktop to load, but after about 5 minutes the system froze.  

I was talking to some co-workers today, I work at a computer help desk at a college, they said that it could be a conflict with my Diamond (ATI) X550 video card.  Not sure if it is or not but I am going to try removing the video card and use my onboard graphics.  If this seems to solve the issue I might be asking for suggestions on a 3rd party graphics card that works good for both Linux and Vista, I do not think that I will have to worry about XP.

Also would the order of the partitions matter? Right now the way I have my hard drive partitioned it is XP, Vista, a FAT32, and then Linux.  I would think if this is the issue that I would not have been able to boot to Linux, but I do not really know.

---

### Post by robert.e.dean.jr on 2008-01-08
> **bharadwaj said:**
> Are you sure whether the problem is with the 4x or writing speed issue of CD cause i don't think there would be any reason for that to happen. Instead burning the alternate CD would fix the problem even my system doesn't suppoert live CD I had to install from alternate CD

While the live cd did not work at all, I did have an issue with the alternate cd when it was burnt at 8x using InfraRecorder, 8x was the slowest burn speed that was avialble to me.  When I used imgburn and burnt the live cd at 1x I still had the same problem, but when I burnt the alternate cd at 1x the problem disappeared.  So I would say yes that the write speed does play some part in this issue, but not the sole culpurit.

---

### Post by Partyboi2 on 2008-01-08
> **bharadwaj said:**
> Are you sure whether the problem is with the 4x or writing speed issue of CD cause i don't think there would be any reason for that to happen. Instead burning the alternate CD would fix the problem even my system doesn't suppoert live CD I had to install from alternate CD
The write speed can cause problems, not always but somtimes. If it was me having the problem, I would rather someone tell me to try burning at a slower speed which could fix the problem, then having to download 693 mb specially if I was using dial up. If the burning at a lower speed didn't work then I would look at using the alternate cd. This is only my opinion. :)

---

