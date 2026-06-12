---
title: "Can't boot from E: (CD-R Drive)"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by tnxBob on 2006-09-05
I successfully (I think) downloaded Ubuntu "boot from disk."  BUT: can't boot from the disk; "Ubuntu 6.06 (Disc Tree)" opens, but that's as far as I can get.  If I open E: and click the Launch icon, I get this message:

E:\bin\launch.ini not found.

Note: I have Windows XP Home(SP2) on a Dell Dimension 4600.

I have no idea what to do about this.  But I sure do want a viable alternative to Windows, so any help will be most appreciated!!!!

---

### Post by Jussi Kukkonen on 2006-09-05
So you tried booting while the CD is in the tray, but it wouldn't boot or booted from the hard drive?

Have you set the boot order (in BIOS) so that CD is tried before your hard disk?

---

### Post by cotcot on 2006-09-05
Have you burned the CD as an iso ? (if you look at the CD content do you have 1 folder or many folders ? If you have only 1 reburn the CD with specified it is an iso.

---

### Post by tprasanthm on 2006-09-05
Even I cannot boot from the CD-R drive. as instructed, I put the CD in the drive and restarted my Windows XP (SP2) system running on a Toshiba Satellite 2400 laptop. However, the CD fails to run on startup and Windows XP is loaded up again without any changes. 

However, I guess the BIOS allows for checking CD's before loading since I do use the recovery CD of the computer at times when Windows does its usual troubles. Could someone please give step by step instructions on how to run this CD or troubleshoot on what the problem might be?

---

### Post by tnxBob on 2006-09-05
The disk is ok (and not a .ISO), "many" folders are there - Chrome, Components, Bin, ... and a bunch of *.dll.

If I insert the Ubuntu disk, the E: drive will "auto load and open" the "Ubuntu 6.06 (Disc Tree)" and it works.  From that page I linked to and downloaded AbiWord and others.  And I can open E: in DOS and run Start.Exe with the same result as above.

Note: Drive E: Properties shows "Ubuntu 6.06.1 i3," 698MB.

BUT: I can't load Linux.  I leave the disk in E: and reboot, all I ever get is the "Ubuntu Tree" screen. Something I read indicates that this "launch.ini" has to do with a Windows security issue in that the absence of it precludes "malware purveyors" from writing to a disk after sneaking into your computer.  Shouldn't/couldn't this "launch.ini" be included in Ubuntu's Bin file?  All this is well above my experience level.

btw, my first (and second and third) download try was to open with "RecordNow!,” I have v7.3.  Wouldn't work, no way, no how.  Found this that worked very smoothly (the first time!), it's donationware:

[http://isorecorder.alexfeinman.com](http://isorecorder.alexfeinman.com)

My sincere thanks to all who responded.

tnxBob

---

### Post by eccofire on 2007-05-10
Hello, 
Today i made a image .nrg (nero) from the original UBUNTU CD. 
Then i made a backup of my stored files in partition D in case anything goes wrong. 
I burn the image .rg in a new CD, then i had this directories:
e:\
.disk
bin
casper
disctree
dists
install
isolinux
pics
pool
preseed
programs

I restarted then my p.c., go to the bios and put the primary boot disc - cd/dvd
F10 - save and exit

and...nothing. it simply didn't worked, it goes to windows and it sucks. 

i need help!!!!!!!!!!!!!!!!!!!!!!!!!!!!! :)

thks for listening me

***: "pássaro de fogo"

---

### Post by eccofire on 2007-05-11
I passed the initial test, after all i had only to boot UBUNTU in a .ISO CD!!

Now the problem emerge when i tried to install UBUNTU. 
Cause i dont know how to define the "System Root File"...in step 5 of the installation. 

Anyone knows what it should be?  

Obrigado :)

---

