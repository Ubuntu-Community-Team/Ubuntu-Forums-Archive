---
title: "&quot;Create USB Startup Disk&quot; permamently kills thumb drive?"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by nexus_2006 on 2010-02-01
I had a 2GB memorex thumbdrive that was about 4 years old.  I used the utility in 8.10 to make it into a live install disk, and it worked well.  I have not been able to use it for anything else, ever. Gparted wiped the partitions and formatted a nice clean ext3 part on the drive, but it won't mount.  Tried formatting again as a fat32, the GF's computer will not recognize the device at all.  Probably the drive just died, or this utility makes the USB drive a startup disk permamently.

What I'm asking, basically, is if I use the new 4GB USB drive I bought today as an install disk using this utility (I'm running 9.04 right now), will the new drive be trash after that?

thanks

---

### Post by sanderj on 2010-02-01
First of all: congrats with your 100st post "Beans: 100". ;-)

About your post: I've experienced the same. I had a hard time really, really cleaning and formatting the USB stick after a failed Ubuntu-live-install. 

So: try a few different clean & format methods, and your old stick will probably be OK.

And you don't have to worry about killing a new stick.

---

### Post by dabl on 2010-02-01
It's probably a goner.  However, I would give it one more chance, and use "dd" to lobotomize it, and then try formatting it FAT32 again.

[http://kubuntuforums.net/forums/index.php?topic=3090824.0](http://kubuntuforums.net/forums/index.php?topic=3090824.0)

Be _very very_ certain that you know the device number of the USB stick -- get it from ```
fdisk -lu
``` before you run "dd".  If you get it wrong, you could lobotomize your hard drive instead, losing everything. :(

Assuming for this case that the USB stick is /dev/sd**f** in your system, then

```
sudo dd if=/dev/zero of=/dev/sdf bs=512 count=1
```

will overwrite the partition table and render the USB stick "as new".  Then use GParted, when it prompts choose "ms-dos" for the new partition table type, make a single partition (the whole stick) and then format it FAT32.  Then run some tests and see if it's going to hold up.  If not, it's dumpster food.

---

### Post by nexus_2006 on 2010-02-01
Thanks for the replies so quick.  I'll try the recovery method mentioned with a live CD and my HDD disconnected.  I'm 99% confidant I can do it properly (been using *NIX as mt primary OS for about 5 years, thanks for the 100 post congrat), but I want to be 100% sure, just spent 4 hours using gparted to move and resize my partitions.  At least now I know that I won't kill a new USB drive this way.  I'll post the results later.

---

