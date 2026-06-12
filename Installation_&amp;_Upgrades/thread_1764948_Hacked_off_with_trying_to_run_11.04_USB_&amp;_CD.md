---
title: "Hacked off with trying to run 11.04 USB &amp; CD"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by fatriff on 2011-05-22
Hi all,

OK, this shouldn't be as difficult as it is being and i've never had issues in the past.. i've managed to run almost every distro out there from USB, I've got the ISO and i've got unetbootin & startup disk creator and I've tried the terminal method..

1st I burned the image with brasero.. Wouldn't boot, a flashing cursor just remained on the screen for about 10 seconds then went into normal grub..

Then I tried unetbootin.. It only copies 5 files onto the usb stick..

/media/4BAC-F3B1/ldlinux.sys
/media/4BAC-F3B1/menu.c32
/media/4BAC-F3B1/syslinux.cfg
/media/4BAC-F3B1/ubnfilel.txt
/media/4BAC-F3B1/ubnpathl.txt

Which is next to useless, I can't do anything to get it to write the actual iso.. It just skips that part out.

Startupdisk creator won't even allow me to select the iso as it says.. Locate your Mint iso for writting.. Even though I locate the ubuntu iso it just remains a blank box..

Goto the download page on the ubuntu site and you click SHOW ME HOW and it only gives instructions for Windows.. Why??? 

I am using Mint 10 but even still, I should still be able to get this working..

---

### Post by fatriff on 2011-05-24
Sorted the problem out, The torrent listed on the alternative downloads for the X64 is corrupt (I downloaded it 3 times).. I downloaded the main one from ubuntu and it worked 1st time.

---

### Post by Quackers on 2011-05-24
It is a good idea to check the md5sum of any downloaded iso file. It can save a lot of time.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

