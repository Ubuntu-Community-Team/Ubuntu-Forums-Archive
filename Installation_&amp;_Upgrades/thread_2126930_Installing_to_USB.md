---
title: "Installing to USB"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by RobZ51 on 2013-03-18
Would installling to an 8 GB USB work? I heard Live-USBs cant be updated which i need to do, so would a real installation to the USB work. And would it be much slower than installing to hard disk? Also will it work on most systems?

---

### Post by Andrew Bastin on 2013-03-18
Dude its not even possible because your PC's bootloader will change to grub.
and you will get a error as no such partition on grub-rescue after rebooting.
And is it even possible to change a fat32 partition into 4 or to be ext4

---

### Post by Cheesemill on 2013-03-18
Yes, it's perfectly possible to do this, 8GB will be pushing it for size though.

Just go through the normal installation procedure but make sure you install the bootloader onto your USB stick, not your machines internal drive.
There are plenty of posts on the forum discussing the pros and cons of a full installation vs. a Live USB with persistance, I'll try and dig up some links for you.

---

### Post by slickymaster on 2013-03-18
> **Cheesemill said:**
> Yes, it's perfectly possible to do this, 8GB will be pushing it for size though.

Just go through the normal installation procedure but make sure you install the bootloader onto your USB stick, not your machines internal drive.
There are plenty of posts on the forum discussing the pros and cons of a full installation vs. a Live USB with persistance, I'll try and dig up some links for you.

+1 on Cheesemill's post.

Just check this out:
[http://ubuntuforums.org/showthread.php?t=1910531&p=11618397&viewfull=1#post11618397](http://ubuntuforums.org/showthread.php?t=1910531&p=11618397&viewfull=1#post11618397)
[http://ubuntuforums.org/showthread.php?t=1908107&p=11606773&viewfull=1#post11606773](http://ubuntuforums.org/showthread.php?t=1908107&p=11606773&viewfull=1#post11606773)
[http://ubuntuforums.org/showthread.php?t=1885392&p=11546560&viewfull=1#post11546560](http://ubuntuforums.org/showthread.php?t=1885392&p=11546560&viewfull=1#post11546560)

---

### Post by FabulousCabbage on 2013-03-18
As long as your computer can boot from USB I can't see why this wouldn't work, the speed it would run at would really depend on what USB drive you're using (assuming you're using USB 2.0), if you're using USB 3.0, it could possible run faster than most harddrives.

I would advise uninstalling all the packages you don't want straight away, this would benifit the 8GBs pretty well.

---

### Post by RobZ51 on 2013-03-19
Im currently installing it. And im using a Cruzer Fit USB so the speed is about 20MB/s read and 4.5MB/s write. I unplugged my HDD to be sure i dont mess up.

---

### Post by RobZ51 on 2013-03-19
It seems to work great, but i will go buy a 16gb USB because 8gb isnt enough.

---

