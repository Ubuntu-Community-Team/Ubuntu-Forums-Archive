---
title: "Gutsy hangs at 15%"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by cat5e on 2007-11-21
Hi all - I'm a relative nOOb, but have been using ubuntu for about a year on 3 machines. I'm trying to install gutsy gibbon on an IBM Thinkpad T30 and it consistently hangs at "Installing System, 15% - Detecting file systems...". I've tried using a CD burned at 1.x speed, run the installer multiple times, etc. I really like and enjoy ubuntu and would like to switch to this computer but so far am stumped. Any ideas?

---

### Post by Sef on 2007-11-21
1) Did you md5sum the disk?

2) Did you check the disk?  (Below start live cd/install)

3) Use the alternate cd.  It sometimes works where the live cd fails.

---

### Post by dabl on 2007-11-21
Most of these "install hangs at xx%" cases turn out to be a bad CD, which can come from (a) the blank media or (b) the burner/burn process.

So, things to try are:

(a) different blank media, and
(b) different burner

You are correct to keep the burn speed down to 4X or slower.

:)

---

### Post by cat5e on 2007-11-21
thanks for the suggestion, I finally got it working by taking them both into account. I used the gparted live CD to delete the partitions on the hdd and just formatted the whole thing to ext3. The I used the alternate cd to do the install. It came off without a hitch!

Thanks for the help!

---

