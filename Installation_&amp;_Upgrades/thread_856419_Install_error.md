---
title: "Install error"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by screaminj3sus on 2008-07-11
Every time I try and install Ubuntu 8.04.1 I get 

"The installer encountered an error copying files to the hard drive [Errno 5] Input/output error&#8221;

I tried burning at 4x speed and verified the disc and I have burnt like 3 cd's and it happens everytime. The MD5 on the iso I downloaded is correct as well. The only disc that works is my original 8.04 disc, NONE of the 8.04.1 discs I have burned work they ALL do this, but other distros and 8.04 work fine. is there something wrong with the 8.04.1 iso? because this is ridiculous. I even downloaded burned and verified the 64 bit version and still same error. I am using regular Sony CDR's

I want a working 8.04.1 disc so I don't have to download tons of updates every time I install.

---

### Post by wpshooter on 2008-07-11
Have you tried to download from a different source/server ?

---

### Post by screaminj3sus on 2008-07-11
> **wpshooter said:**
> Have you tried to download from a different source/server ?

I tried the torrent and the direct download from the ubuntu site. I'm trying a different brand cdr right now but I went through like 4 brand new sony cdr's, but I did find one memorex laying around.

---

### Post by screaminj3sus on 2008-07-11
Just got the official md5 sum from the ubuntu site and checked it, I have downloaded the 32 bit and 64 bit isos via torrent AND direct tried burning slowly AND using a different brand cdr, STILL same error at 40% I have also burned it with imgburn and infrarecorder.

Think I may try wubi with the iso I downloaded to see if it installs.

[[IMG]http://img509.imageshack.us/img509/3315/md5fq3.png[/IMG]](http://imageshack.us)

---

### Post by avtolle on 2008-07-11
Before trying the Wubi installation, be sure to defrag the drive; you might also want to run chkdisk to check the HDD out. Good luck

---

### Post by screaminj3sus on 2008-07-11
Well wubi installed perfectly, not sure why all the cd's fail.

---

### Post by cryolithic on 2008-09-09
I also have this problem, I have tried two different downloads, multiple cd-r and cd-rw's.  Also written the disks in two different drives.

I also attempted burning the image to a usb key and installing from there, same problem.

---

### Post by cryolithic on 2008-09-16
Downloading from a different mirror solved the problem.

---

### Post by Nubicles on 2008-09-24
I had the same problem trying to install 8.04.1 on my wife's computer.  I burned multiple ISOs to various media (CD and DVD), checking md5 sums along the way.  I updated the motherboard BIOS.  I tried multiple CD drives.  I resized and reformatted the partition.  I ran my hard drive vendor's diagnostic utilities (Seagate).  Everything seemed to check out, but no matter what, it seemed, it bombed at 37% with "Errno 5".  I was about to rip out the CD-R so I could use the same drive to both burn the ISO and do the install.

Once inside the computer I noticed an odd RAM module.  I pulled it out along with its counterpart in the other CPU's slot, leaving just two *matching* RAM modules for a total of 2GB.  I powered up and installed without any problems.

I haven't really investigated the root of the RAM issue further (bad stick, incompatibility, configuration, gremlins, etc.), but in any case it would be very nice if the "Errno 5" message included something about RAM as a possible culprit.

---

