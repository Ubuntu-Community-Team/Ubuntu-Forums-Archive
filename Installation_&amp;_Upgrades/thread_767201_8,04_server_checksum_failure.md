---
title: "8,04 server checksum failure"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by FranzJ on 2008-04-25
I downloaded and attempted to install 8.04 server on a HP Netserver 800 and the installation failed. I checked the disk and got the error ./dist/hardy/main/debian-installer/binary-i386/Packages failed MD5 checksum verification. I have downloaded the image three times for different servers, changed image burning software and the brand of discs. The checksum error occurs in the same location on each burn. Anyone else have this problem with the server edition? The desktop version seems to work fine with no errors.

---

### Post by campnewport on 2008-04-29
I have also had this problem.  It happens using either by direct download or torrent.  I am trying a clean install on an empty hard drive and it happens no matter what speed, disc type or computer I use.

---

### Post by cashin on 2008-05-01
I didn't check the md5 after downloading, but the checksum failure happened when I checked the CD at the installation bootup screen. I tried the following which worked for me.

1) Burn the .iso image, but set the disk to multi-session (i.e. can add more content after burning)
2) Add the actual .iso file to the disk.
3) Install

I didn't check the installation disk after that, but the installation works though there was a delay when the installation was "checking the mirror".

Hope it helps, cheers

---

### Post by ztirffritz on 2008-07-24
are you adding the Contents of the ISO file, or the actual ISO file to the CD?  I am having the same problem, but I don't see how you can burn the ISO to CD AND fit the ISO file on the CD.  CDs only hold 700 or so MB, and the ISO is 500+ MB.  I can't fit it on there twice...

---

