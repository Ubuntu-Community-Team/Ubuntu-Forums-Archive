---
title: "Still looking for help..."
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by xi'an on 2007-11-07
I asked this question before - I think it was in a different forum - but haven't received a reply so I'll try again here.

My system now is dual boot Fedora 7/Windows XP.  I want to replace Fedora with Ubuntu 7.10, keeping XP as it is.

How do I do this?  I would describe myself as a somewhat experienced beginner, but really would benefit from very specific directions for how to do this.

Thanks for any assistance.

---

### Post by Pumalite on 2007-11-07
Install on top of Fedora. Go Manual and point to the right partition.

---

### Post by xi'an on 2007-11-07
Thanks, Pumalite.

Alright, now to expose my ignorance: how do I recognize the right partition?

---

### Post by Pumalite on 2007-11-07
In Terminal from Fedora:

sudo fdisk -lu

---

### Post by xi'an on 2007-11-07
Thanks again.   I'll give it a try.

---

### Post by Pumalite on 2007-11-07
It might be 'su' 'password' in Fedora. (I never used it.)

---

### Post by xi'an on 2007-11-07
Okay.  I tried what you suggested, but I got the message "fdisk: no such command"

I'm using the LiveCD for installation.  I ran it as far as the partitioning step and chose 'manual'.  Here is the current partitioning that it displayed:

/dev/sda1   fat32   /media/sda1       10487MB       5700MB
/dev/sda5   fat32   /media/sda5       47188MB       7500MB
/dev/sda6   fat32   /media/sda6       47188MB      17500MB
/dev/sda3    ext3   /media/sda3           106MB           23MB
/dev/sda4                                     145085MB       unknown

Assuming the fat32 are all Windows partitions, sda3 is grub?  and sda4 is where Fedora lives?

What do I do from here?  

Thanks yet again.

---

### Post by Pumalite on 2007-11-08
It seems you chose fat32 for everything. The ext3 of 100 MB I don't know ( boot?, /swap?)

---

