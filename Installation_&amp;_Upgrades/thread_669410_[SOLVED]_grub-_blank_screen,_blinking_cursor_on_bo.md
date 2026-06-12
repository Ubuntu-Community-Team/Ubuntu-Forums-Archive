---
title: "[SOLVED] grub- blank screen, blinking cursor on boot"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by a_posse_ad_esse on 2008-01-16
This seems to be a fairly common problem, but I am unsure if my situation is complicated by RAID-0.

My disk structure is set up thusly:

hda- DVD-RW (master)
hdb- 80 GB disk (slave)
hdc- 160 GB disk (master)
hdd 40 GB disk (slave)

hdb is holds the /boot partition, and is partitioned like so
500 MB /boot
500 MB swap
39 GB /
40 GB RAID-0

I successfully created the RAID device, but am unable to boot.  I only get a blank screen with a blinking cursor.  I have tried booting from the livecd, mounting /dev/hdb1 and running grub-install or setting grub up manually, all without success.  

Is there something else that I can do?  I've read most of the posts about it, but may have missed something...  Thanks

---

### Post by a_posse_ad_esse on 2008-01-16
I've just tried re-installing, and came up with the same result.  Is this a problem with grub?

---

### Post by rappin05 on 2008-01-16
I dont think the problem is raid because im having the same problem and i dont have raid

---

### Post by a_posse_ad_esse on 2008-01-23
I've figured it out I think. 

/dev/hdc is being viewed by GRUB as hd0 because it is the first master disk.  I changed menu.lst to (hd0,0) and it works fine.  Strange problem, but I guess it makes sense in a way.

---

