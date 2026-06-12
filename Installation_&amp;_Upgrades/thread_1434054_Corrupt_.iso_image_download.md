---
title: "Corrupt .iso image download"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by d.vanheeckeren on 2010-03-19
Hi there, I didn't see this in another thread...  It seems that every time I download the 32-bit server iso image, the download is corrupted.  I've downloaded it twice, and it's corrupted in the same place.  After the first download, I suspected just a bad cd so burned another one, and all three (two from first download, third from second download) are bad in the same place.  I suspect it's somehow a problem with the way my computer is downloading, because I don't see this problem mentioned in your forums.  Any suggestions?

And now that I think about it, will 64-bit run on an AMD Athlon XP 2100 (1.733GHz)?

---

### Post by hansdown on 2010-03-19
Welcome to the forum d.vanheeckeren.

Two Things; 1: Burning the disc at the slowest speed is desirable.

            2: The mirror you are downloading from, or the torrent, may be bad. Change the mirror, or torrent.

---

### Post by d.vanheeckeren on 2010-03-19
I don't have that option on the 'enhanced download page', so I'll try from a mirror, and I'll also set the burn speed to lowest and keep you updated.  Thanks for the help!

[EDIT]

should I try disabling the firefox download manager?

---

### Post by srs5694 on 2010-03-19
Also, Linux software repositories, including those for Ubuntu, usually include a file called MD5SUMS or something similar. This file includes a type of checksum value, called an md5sum, for each file on the site. In Linux, the md5sum program calculates md5sum values; in Windows, you can try a tool like [md5summer](http://www.md5summer.org/) (I've never used it; it just turned up first when I Googled "md5sum windows"). In any event, you can check the md5sum of the file you've got and compare it to what the repository site says it should be. If the values differ, you shouldn't bother burning a disc, since you know the download was bad. This won't help if you've got a burn problem, though (a batch of bad discs or a problem with your optical drive, say).

---

### Post by hansdown on 2010-03-19
> **d.vanheeckeren said:**
> I don't have that option on the 'enhanced download page', so I'll try from a mirror, and I'll also set the burn speed to lowest and keep you updated.  Thanks for the help!

[EDIT]

should I try disabling the firefox download manager?

Download manager should be fine.

Burning at the slowest speed, is probably your best bet.

It cuts down on file corruption.

---

### Post by d.vanheeckeren on 2010-03-20
ok, downloaded from mirror, checked md5 before burning, burned with slowest allowed burn speed (24x) and had burning software verify data after write, and it all went well, the cd is installing on the server machine as we speak.  Thanks for the help!!  As I'm a Windows administrator and trying Linux for the very first time, I'll probably be asking a lot more questions, especially advice on ubuntu equivalents of windows server software. :D

---

### Post by hansdown on 2010-03-20
Hey, that's great d.vanheeckeren.

Glad you got things going.

---

