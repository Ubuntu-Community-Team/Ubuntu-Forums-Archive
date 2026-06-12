---
title: "Live CD Boot"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by estel on 2006-06-04
I downloaded the torrent of 6.06 amd64; md5sum checked it, and burnt it from my existing 5.10 environment (though I primarily use Gentoo - but don't have K3B there atm).

Rebooted, got into the Ubuntu CD screen, chose the first option.

The list gets to "Configuring some drivers" (or something) and stalls (though that line is marked "ok")

After a veerrryyyy long while I get a prompt asking to Choose the runlevel. Anything from 1-5 just say "No processes left in this runlevel" and I have to manually reboot. This prompt is in term 8, term 1 says that the kernel booted successfully.

What's wrong? :(

---

### Post by estel on 2006-06-04
[http://forum.ubuntu-fr.org/viewtopic.php?pid=318908](http://forum.ubuntu-fr.org/viewtopic.php?pid=318908) seems to have the same problem.
I tried with the noacpi options too, but it didn't get me anywhere. However, after trying to get it to verify the CD content, it did encounter a mismatch - a crucial failing?

---

### Post by rcarring on 2006-06-04
Try to download the iso image using ftp, not torrent.

---

### Post by estel on 2006-06-04
I'll go and recheck the md5sum for the iso... if that matches isn't it easier to reburn assuming a CD error?

---

### Post by asnesio on 2006-06-05
I get stucked to this same "Configuring some drivers" message on the Live Cd/Desktop i386 version. Already downloaded ubuntu/(k)ubuntu/xubuntu by torrent, ftp, http, checked md5sum on all of them and still get stucked in this same "Configuring some drivers" message. Also tried "noapic nolapic" stuff but didnt have any result. It is really odd because I can get it to install on my machine under VMware using windows XP and on my father's PC that is as old as mine machine. I can install Ubuntu Breezy without any problem and could even make a distro upgrade from breezy to dapper without any further complication(After upgrad dapper runs perfectly though). My machine installs and runs Fedora Core 5, Ubuntu Breezy and Windows XP Sp2 smoothly. I´m pretty sure that there is no hardware malfunction like memory/video card/Hard Drive (tested them already).

My machine:
Ahtlon Thunderbird 1.2Ghz, 512mb PC133, 80Gig Harddrive, ATI Radeon 8500 64mb, ASUS A7A266 motherboard (I know it´s old, but It plays my animes very well :P).

By the way, I searched other ubuntu forums (Spain, France) and noticed that this problem is very common. Looks like a "bug" with the dapper installer with some machines. "configuring some drivers screen of death"? 
Any help is welcome. I m really trying to go for "linux only" this time with ubuntu and want a fresh install(don´t want to make the breezy to dapper upgrade approach because with my ADSL connection takes 7-8h to upgrade).
Thanks. ^^

---

### Post by rcosentino on 2006-07-16
With me it´s the same. My hardware:

. Placa mãe Intel D865 Perl
. Pentium 4 - 3.0Ghz
. 512 mb RAM DDR400
. GeForce MX4000 - 128mb AGP8x
. Gravador de DVD 16x LG Dual Layer

---

### Post by rcosentino on 2006-07-18
The solution is change your CD or DVD-ROM drive. With me it´s work.

---

