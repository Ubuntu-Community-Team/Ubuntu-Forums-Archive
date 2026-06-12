---
title: "Installation Problems"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by sheilah on 2011-11-23
Hi,  I appreciate any help anyone can give.  I'm trying to install Ubuntu 11.10 on an Acer that currently has 9.1 on it.  I downloaded the file, copied it to a cd but it wouldn't auto install.  I went and changed the BIOS order to put CD at the top followed by USBs.  No luck booting from the CD.  I wasn't sure if I was burning the cds correctly, so I got a usb and used the utility in 9.1 to burn to the usb for an installation.  That got me a little further in that the system read the usb and tried to boot from there but then gave me the following error message:  

SYSLINUX 3.63 Debian-2008-07-15 EBIOS Copyright (c) 1994-2008 H. Peter Anvin
Unknown keyword in configuration file.
boot:
(blinking cursor)

I then went and did the check sum to make sure the hash on the file matched the hash on the website, and it did.   I'm not at all technically inclined so I am absolutely clueless as to what to try next.  Any help you can give me would be super appreciated.  I want to get the laptop up and running for my son by the time his birthday rolls around so that he and his friends can play minecraft at his party.  Thanks again.

---

### Post by darkod on 2011-11-23
What exactly did you use to "burn to the usb"? Since you already have a running 9.10 it's best to use the Startup Disk Creator application. Format the usb as FAT32, open Startup Disk Creator, select the downloaded 11.10 ISO and the usb stick for destination and that should be it.

---

### Post by CodeHeroes::CodeHero on 2011-11-23
Could you please give some more information about the laptop model and the bios version?

If you're unsure if you burned the CD right or prepared the USB drive right you can look at the ubuntu download page [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) directly below the download link.

And could you also please tell me which programs you used to burn the CD and to prepare the USB drive?

Edit: Too slow -_-

---

### Post by sheilah on 2011-11-23
For the usb stick I used the USB Startup Disk Creator.  As for the CD, I used the Image Burning Setup that comes with 9.1.  I used both a basic cd-r 700mb as well as a dvd-rw but no luck with either.  USB definitely got me the closest.

The laptop is an Acer Travelmate 8204 with these specs: [http://www.notebookreview.com/default.asp?newsID=2783](http://www.notebookreview.com/default.asp?newsID=2783)

thanks for your help

---

### Post by sheilah on 2011-11-24
Just a quick update.  I have ordered the cds from the ubuntu site in case what I've burned isn't quite right.  But since I'm pretty confident the file I downloaded is ok, I'd like to try to burn a cd with a different program while I wait for the ones from ubuntu to come.  Can anyone suggest a good program for burning cds?

---

### Post by darkod on 2011-11-24
Imgburn is free and very good. Don't burn them at more that 8x or 10x speed.

---

