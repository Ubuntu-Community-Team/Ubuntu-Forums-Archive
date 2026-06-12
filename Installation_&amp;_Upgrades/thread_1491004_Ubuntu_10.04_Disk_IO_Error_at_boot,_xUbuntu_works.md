---
title: "Ubuntu 10.04 Disk I/O Error at boot, xUbuntu works"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by bvande on 2010-05-23
First time post, because I've never had a problem in the past. I can't get Ubuntu 10.04 to boot for install (to my desktop), it displays the logo then hangs for about a minute and displays the alert dialouge saying "Boot disk error."

I've tried multiple CD-Rom drives, burned from multiple computers, with both the desktop and server downloads. I'm down about 10 CDs and 2 DVDs here :P  I've checked their integrity (md5) as well as checked the disk integrity from another computer (laptop) and everything passed.

I got xUbuntu to install effortlessly, so I don't know what's causing the problem for Ubuntu. I can even look at the contents of the Ubuntu Server CD from within xUbuntu -- so, I know the disk really should work.

My system specs are pretty basic:
2 x Xeon 2.0Ghz 
Tyan S2720 Motherboard
2 Gig (4x512) ECC PC266 RAM
250 Gig IDE Harddisk
IDE CD-Rom drive
(Disabled) 2 x 80gig SCSI
(Disabled) Floppy

Does anyone have an idea why xUbuntu worked and regular Ubuntu won't, and/or maybe what I can do to fix this?

Thanks in advance!

---

### Post by fredpal on 2010-06-02
bvande
 
Sorry... I don't have an answer, but have experienced the same issue... did you rectify by any chance?
 
Fred

---

### Post by JohnnyB98604 on 2010-06-02
Dang, same issue here...but I'm only down 3 CD's at this point.  I've verified the last two I've burned (I was lazy with the first one).  I get further each time I downloand the ISO and burn a new copy though.  So far, in my three attempts I have gotten as far as 65% before the installation fails.  I've got about 12 minutes left in my fourth download attempt at the ISO.  It sure is strange this is happening.

Further background:
I'm installing on a net book (avertec N1000)
Atom 1.6/160HDD (pretty straightforward netbook really)
I'm using an external CD/DVD running through USB

---

### Post by soluckytouselinux on 2010-06-21
whats up? i have had problems installing 10.04 desktop and getting error message when i try and install. said my dvd was not working, clean the disk. ????? i have installed many versions of Ubuntu, and rarely would i have a problem. This time i checked the disk integrity and it said there was one error on the disk. is there a way of verifying the download? i love using Ubuntu, and i have never had this happen. Help!!!!

---

### Post by JohnnyB98604 on 2010-06-22
My issue's been resolved.  I hadn't run the ChkSum against my CD's.  Eventually, I got a good download and burn...just dumb luck though.

Sorry, I wish that would've been more help.

---

### Post by ubiquity on 2010-06-24
> **JohnnyB98604 said:**
> My issue's been resolved.  I hadn't run the ChkSum against my CD's.  Eventually, I got a good download and burn...just dumb luck though.

Sorry, I wish that would've been more help.

I have a similar problem-- ubuntu boots, and I installed it fine but is too slow to use on an old Sony Vaio.  The machine will not even recognize the xubuntu boot CD, though.  I get the bios flash and a little read on the CD, then only a blinking cursor.  

I find it hard to believe it is a transcription problem, because nothing happens (rather than failure under weigh).  But I can go back to the Ubuntu CD and boot again and again.

---

### Post by soluckytouselinux on 2010-07-01
hi everyone. with the first disk that i downloaded and burned, i did a check disk after many attempts to install. sure enough, the disk had a error. went back and downloaded another copy, and now everything works fine. easy install. a five year old could do it.

---

### Post by RJARRRPCGP on 2010-07-02
The solution for bad CD burns:

Get Puppy 5.0.1 and burn CDs with PBurn.

It has an MD5 comparer. I can always know if the CD burn is good before booting it.

It actually scans the CD and compares the CD to the ISO!

---

