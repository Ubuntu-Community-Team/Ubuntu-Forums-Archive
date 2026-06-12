---
title: "How to do an automatic mount"
date: 2016-04-09
forum: Installation &amp; Upgrades
---

### Post by stan28 on 2016-04-09
When I reboot Ubuntu and immediately go to Firefox, it tells me that my profile is not loaded.  I simply have to go to my first hard drive on the Unity bar, click it and that solves the problem.  I am guessing the clicking mounts the hard drive so Ubuntu can see it, and then Firefox has it available.  If I am right about what is happening, I have a question:  How can I simplify this so my first hard drive automatically mounts when I reboot?

Thanks!

---

### Post by Impavidus on 2016-04-09
I assume you've got a dual boot system and share your firefox profile with another system, using a symlink from the usual location of the profile to some directory on the other partition. That's fine, many do so.

The normal way to mount partitions automatically on boot is using fstab. If this leads to mounting it somewhere else than where it used to be, you may have to fix the symlink to the profile directory.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by stan28 on 2016-04-15
Thanks for your response.  I have multiboot, but use ubuntu almost exclusively now.  I keep Windows to do things I can't figure out how to do in Ubuntu, and to get around Ubuntu bugs/problems, like an error in an Epson printer driver.

I looked at the first link you gave me, and started playing with fstab.  I needed to go to the firefox profile to figure out where it was looking for my various versions, via Nautilus and CTRL-H, and did some experimenting. It took quite a while, but this is the line I added to fstab to get things to work:
LABEL=Storage1 /media/s/Storage1 ntfs defaults 0 0

s is my user ID.  Storage1 .. n are my HD's.

I don't understand enough about files and labels to figure out what I did, but i got what I wanted.  Again, thanks!

---

