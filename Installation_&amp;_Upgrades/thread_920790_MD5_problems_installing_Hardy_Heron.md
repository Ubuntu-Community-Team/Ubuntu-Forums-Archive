---
title: "MD5 problems installing Hardy Heron"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by jonz375 on 2008-09-15
I am getting a MD5 hash error on ../binary-i386/Packages while doing a CD Integrity test of 8.04.

Things i have tried thus far:
- Checked MD5 has on .iso file ... passes
- redownloaded .iso file, checked MD5 ... Passes
- Burnt .iso to disk using Roxio ... MD5 error while checking integrity
- Burnt .iso to disk using IsoRecorderv3 ... MD5 error while checking integrity
- Burnt iso to disk on another computer with Roxio ... MD5 error checking integrity
- Burnt iso to disk on another computer using IsoRecorderv3 ... MD5 error checking integrity
- Tried all discs burnt on a different server ... MD5 error while checking integrity

Long story short, I have burnt iso's from 2 different mirrors using 2 different computers, using 2 different utilities, and have tried installing it on 2 different servers... All failing with MD5 errors on ../binary-i386/Packages, yet the iso MD5 sum checks out fine.

Anyone have any suggestions? I would really like to start testing on 8.04, but am having a heck of a time getting it installed.


Thanks in advance!

---

### Post by Vivaldi Gloria on 2008-09-15
> **jonz375 said:**
> Anyone have any suggestions?

I saw this happen to someone and he solved it by downloading and using the alternate cd. To download it check the box for it here:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by fewjr on 2008-09-15
I'm just wondering, did you use the same brand of media to burn to each time? I just read a post where someone changed hardware, redownloaded the .iso, etc, but ended up figuring out that he had a bad batch of cd-r discs.

                                       fewjr

---

### Post by jonz375 on 2008-09-16
Not really sure why this release does not want to play nice with my servers... I am testing it on some older hardware(IBM xSeries330) and the hardware seems to be the culprit. 

I tried running the live Desktop CD and it loops continuously through a SQUASHFS error. I popped the CD in my laptop and it was able to finish the consistency check.

I am going to try installing Dapper and upgrading it to Hardy. Will post results!

---

### Post by zvacet on 2008-09-16
Probably to late,but anyway.Download same iso with torrent and point download to the folder with your existing iso.That way torrent will just check iso for coruppted files and replace it with good ones.After that run md5sum and after you burn iso on lower possible speed check disc integrity.If all goes well install.

---

### Post by jonz375 on 2008-09-17
Thanks for the replies!

It turns out that it was a hardware issue ont he server i was trying to install on... Still haven't figured out what the deal was. I tried booting the live desktop CD on the same server, and it failed to start. It appeared to be stuck in a loop complaining about the SQUASHFS.

I went ahead and installed 6.06 and upgraded to 8.04. The upgrade went smoothly. The box is up, patched and stable(so far :)).

I have about 6 copies of Hardy Heron on CD now :lolflag:

---

