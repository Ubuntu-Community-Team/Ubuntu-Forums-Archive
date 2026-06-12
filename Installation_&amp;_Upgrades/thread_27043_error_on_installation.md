---
title: "error on installation"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by dilusion on 2005-04-14
Im relatively new to linux, our tutor handed out ubuntu cd's and I have been trying to install it on my machine, the Live CD works fine, but when I try and install, on installing the base system, I get

(roughly 20% through, validating)

The debootstrap program exited with an error (return value 1)

Check /var/log/messages or see virtual console 3 for details.

/var/log/messages doesnt exist =( what am i to do ?

---

### Post by Klin'Targ on 2005-04-14
Well virtual console 3 is viewable by pressing ctrl+alt+f3
You could probably find the error message there. Without more info, my only guess would be a scratched/badly burned cd. 
If you have access to a linux machine, you can test the cd by running ```
md5sum /dev/cdrom
``` A badly burned cd will usually give an input/output error at some point during the process. If you can find the md5sum of the iso the cd was burned from and the above command gives the same output, you can be certain that the cd is good.

---

### Post by Nargile on 2005-05-14
Have the same problem. Already ran checksum test on the cd and it's correct. Also, my flatmate got the 4.10 install bundled with a pc-magazine so we tried that, but with the exact same error. Tried to read what it did just before it died, and i THINK it was validating passwd. It dies at the exact same spot on both install-cd's. 

I think it must be a hardware-thing. The computer i'm installing on is a PII-MMX 450 with 128MB RAM, which i'm intending to run as a server for uni-projects. It's been running both slackware and fedora core 3 in the past, which worked well. I also tried running the install with different options(expert, server, custom etc), but nothing helps.

---

### Post by TheOldGuy on 2005-06-04
Add me to the list with the same problem.  Used MD5 and sums are ok.  I've burned CD-R and CD-RW discs on two different computers using Nero and DVDDecrypter.  Burned at 1x.  Even downloaded the iso a second time.  Live distro works fine as do other live distros: Knoppix and Phlak.  Also tried Warty and got same "Failed getting Release file" error.

Ctrl-Alt-F3 log gives me these messages:

tar: Cannot create directory './usr/lib/gconv': Read-only file system
tar: ./usr/lib/gconv/ANSI_x3.110.so: No such file or directory

System is a PII @400 Mhz; Maxtor 30 Gig; 320 Megs RAM; single operating system.

Although I've played with a few live CDs, this is my first attempt at installing Linux to a system.  All the live distros I've tried have worked fine.  Knowing virtually nothing about Linux, I don't know what other information might be helpful.

---

### Post by Mustard on 2005-07-10
I'm having the similar problems on an older system, as those mentioned above. I'm trying to install on a  500 Mhz Celeron, 128mb, 10 Gb drive.  It's giving me errors on installation that are not consistent, as the point at which the error occurs is changing each time I attempt to do the install again.  At first I thought it was the CD, but I have since burnt a brand new install CD (doing so at the lowest possible write speed), so as to comply with the request in the error message to use a CD written at a lower speed.  Some help with this issue would be good.  All the systems mentioned above and the one  I am working on all seem to be low end systems.

---

