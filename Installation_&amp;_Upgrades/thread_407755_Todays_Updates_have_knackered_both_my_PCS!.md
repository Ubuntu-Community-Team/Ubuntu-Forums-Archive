---
title: "Todays Updates have knackered both my PCS!"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by euan on 2007-04-12
What's going on???

Booted both my laptop and desktop, noticed there were updates available (it was uptodate as off yesterday).  Installed the updates, seemed to be mostly kernel headers, development stuff.  Libc etc.  PC2 did something strange.  The updater program locked up after being given permission to run the updates.  error message saying can't run XPermissions / /usr/bin/update.properties as root (or words to that effect)?

PC 1: laptop can't find the linux partition, had to boot into windows!
PC2: Desktop won't log into the desktop, screen goes blank then it returns to the login screen no message???

HELP!

---

### Post by GeDaMo on 2007-04-12
On PC2, check to make sure the disk isn't full.

---

### Post by euan on 2007-04-12
> **GeDaMo said:**
> On PC2, check to make sure the disk isn't full.

Pat on the back for you, PC2 has indeed ran out of space! :)  Still don't know about PC1 though... It should have loads of space available... :(

---

### Post by bulldog on 2007-04-12
Take a look in GRUB if you boot from the right partition.
Hit 'e' when you select the line which you want to boot.
You can edit GRUB before you boot,but you have to modify the menu.lst to make it permanent.

---

### Post by bourger on 2007-04-12
After today's upgrades (sure, kernel headers) all sound died in my system. 
```
alsaconf
``` goes OK, but ```
alsamixer
``` returns ```
alsamixer: function snd_ctl_open failed for default: No such device
```.
I had to boot in previous version of kernel (.27).

---

### Post by shootonj on 2007-04-13
I have installed all the updates today, not had chance to write down the error so I will post the errors later but I now can't boot up at all it fails completely. I have had to go to the previous version just to get on my computer. Has anyone else found this?

---

### Post by euan on 2007-04-19
sorry about the long delay, but indeed the grub menu.lst had been changed, and pointed to completely wrong partitions...  Very odd.

---

