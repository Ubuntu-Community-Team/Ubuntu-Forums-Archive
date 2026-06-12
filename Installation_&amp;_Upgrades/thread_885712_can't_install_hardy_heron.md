---
title: "can't install hardy heron"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by Jan| on 2008-08-10
USB 1-1: device not accepting address 2 error -71
/build/build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: usb_submit_uurb (CTRL) failed
Buffer I/O error on device sr0, logical block 343131
Buffer I/O error on device sr0, logical block 343131
SQUASHFS error: sb_bread failed reading block 0xa7033
SQUASHFS error: unable to read cache block [29c0ce75:1bf7]
SQUASHFS error: unable to read inode [29c0ce75:1bf7]

and then I get to (initramfs) prompt

iso passed MD5 and integrity check, burned at 1x

---

### Post by spiderbatdad on 2008-08-10
This isn't the first time I have seen an iso that passed md5sum check and resulted in a bad cd, though it is the second time. Did you also check the md5sum on the cd after you burned it?
Anyway, that looks to be the problem.
Actually...maybe a disk read error. I can't tell. You might try clearing the cmos by powering down and removing the battery for 15 minutes or so. Some towers have jumper to move to clear cmos...though the previous method should work too.

---

### Post by Jan| on 2008-08-10
well I would need the MD5 sum of every file on the CD to check it, it's not like an ISO file...

I will reburn and see if it does the same thing again or not

---

### Post by Jan| on 2008-08-12
> **spiderbatdad said:**
> This isn't the first time I have seen an iso that passed md5sum check and resulted in a bad cd, though it is the second time. Did you also check the md5sum on the cd after you burned it?
Anyway, that looks to be the problem.
Actually...maybe a disk read error. I can't tell. You might try clearing the cmos by powering down and removing the battery for 15 minutes or so. Some towers have jumper to move to clear cmos...though the previous method should work too.
[SIZE="5"]after a few tries I conclude that Ubuntu doesn't like my system. even with 2 brands of CD-R discs I still can't install.
[/SIZE]
AMD Athlon 64 3200+ "Winchester " Socket 939
ASUS A8V DELUXE
> BIOS Version A M I - 11000514 
  BIOS Date: 11/14/05 10:31:52 Ver: 08.00.09 
  BIOS Date: 11/14/05 10:31:52 Ver: 08.00.09 
BIOS Date 11/14/05 
BIOS Vendor American Megatrends Inc. 
Version 1017.002 
Release 11/14/2005 

ASUS V9999GT (GeForce 6800GT)

---

### Post by mordak13 on 2008-08-13
I've had similar issues on one system I have with all Ubuntu based distros, Xubuntu, Ubuntu, Mint, gOS, and even a Debian DVD. I can't install any of these on this PC and it worked before with 8.04r1 and Mint 5r1. 3 different cd/dvd drives so I doubt that's the issue for me. My hard drive is almost new. I'm thoroughly frustrated. I think it may be an issue with my hardware that recently cropped up who knows.

---

### Post by CrazyG on 2008-08-14
I am having similar issues -my Hardy Heron LiveCd (2 of them, using 2 different downloads of 8.04.1) passes the MD5Sum and the system integrity check, but gives me similar errors when I try to run it as LiveCd.  I am having trouble burning DVD+Rs at the moment too, don't know if it is my DVD burner or some other issue.  I am using brand Verbatim CD-Rs for the LiveCD and Verb. DVD+Rs to manually back up my system before doing clean install of HH.  

I have ordered a HH CD from Shipit, and will also be looking at possibly replacing the DVD drive.  I am not very knowledgeable about Linux, and don't have much time to mess around with it at the moment.

Just in case this helps anybody else, I only have 1 optical drive, NEC 3520 DVD drive.  Currently running a somewhat borked 64-bit Dapper.  Used Nautilus's CD-burning software to make LiveCDs, as well as Gnomebaker and K3B (I use Gnome, not KDE).

---

### Post by cariboo on 2008-08-14
Have any one of you tried the the mini iso, it is a net installation, the cd installs just enough to make a network connection then downloads and installs the packages. The 8.04 disc gives you the choice of a full install, a server install and a cli install. You can get the mini iso here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Jim

---

### Post by CrazyG on 2008-08-14
Thanks, Cariboo.  I will try this in the next week in between spells of energetically weeding my garden :).  I will post my results in case anyone is interested.

---

### Post by mordak13 on 2008-08-15
I traced my install problem to a bad ram stick. I removed it and the install went perfectly. I think someone suggested this in a similar thread about the same type of issue.

---

### Post by Jan| on 2008-08-17
well my ram passed memtest86+ long ago. I will try the minimal cd as crazyg suggested.

---

### Post by fsando on 2008-08-23
Could this have something to do with ntfs?

I tried the above link (adding 'all_generic_ide' to the kernel parameters) The only difference is that errors are hidden behind the desktop background, if you leave the desktop they are still scrolling by.

I have installed Ubuntu 8.04 (and upgraded to 8.04.1 later) over my XP system. Recently I discovered that my XP partition was a fat32. I converted it to ntfs, then today I tried the live cd and got those errors. I wanted to give it to a friend to save her windows system and just wanted to check out the procedure myself. She later got the very same errors.

Another thing is that it doesn't behave consistently from one boot to the next.

First time I tried it (ie. cold boot) went through the process the normal way, when it reach the desktop it threw a lot of errors about gnome config. I had to force a reboot. 

Next time (a hot reboot) I got very few lines of those errors and they scrolled by very very slow. Then it booted fine into the gnome desktop.

Third time I booted (hot reboot) it went through the errors (very fast scrolling) for 15 minutes and my impression is that it goes through my ntfs partition (19Gb) throwing an error on every block. At the end it booted fine into the desktop.

Next time I made a cold boot from the live cd it went through the initial steps but stalled just before the error part. I then made a hot reboot and got the fast scrolling errors going on for a long time (didn't let it go all the way to the desktop this time).

What have me wondering is:
1) I have installed ubuntu several times on this machine the last 1 1/2 years the only significant change in this period is that I recently converted my windows partition to ntfs.
2) that the behavior is inconsistent from one boot to the next.

---

### Post by CrazyG on 2008-11-20
My RAM was ok, but I had a bad DVD drive.  After replacing it with a cheap LG drive, Hardy installed without a hitch.

---

