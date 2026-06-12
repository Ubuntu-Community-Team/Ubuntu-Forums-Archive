---
title: "Karmic Live CD Corrupt?"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by A Feyn Man on 2009-11-25
I'm doing a complete wipe and install from jaunty to karmic and having issues. When booting the live cd and installing, I get a black creen for a while then the following error:

SQUASHFS error unable to read data cache entry [number]
SQUASHFS error unable to read page, block [number]
SQUASHFS error unable to read fragment cache entry [number]
SQUASHFS error unable to read data cache entry [number]
rinse, repeat.
 
I then popped in the alternate disc and was fine until after partitioning the drive and beginning to install the base system. I got many errors like:

ubuntu(number)_(otherstuff)_i386.deb file corrupted
repeat with other _i386.deb files

I then stopped, restarted and did the Check Disc Integrity function and it returned:

./pool/main/r/rsyslog/rsyslog_4.2.0-2ubuntu5_i386.deb file failed MD5 checksum verification. Your CD-ROM or this file may have been corrupted.

Any Ideas?
System: Vaio, core 2 duo 2.1GHz, 4GB ram, intel X3100 graphics

---

### Post by jaylsi on 2009-11-25
Your live CD is probably corrupt. Before you burn another one, try clean it first. I had this message during installation. I used fingers to gently rub it with water and dry it with paper towel. If that does not work, you need burn it in a higher quality blank disc.

---

### Post by fancypiper on 2009-11-25
Also, burn at the slowest possible speed.

---

### Post by A Feyn Man on 2009-11-25
Define better quality disc please. Just a better brand?

---

### Post by jaylsi on 2009-11-25
Yes better brand. I think Sony and Verbatim are good. You could burn another one to see if it works. Even with the worst quality, the success rate should be >50%.

---

