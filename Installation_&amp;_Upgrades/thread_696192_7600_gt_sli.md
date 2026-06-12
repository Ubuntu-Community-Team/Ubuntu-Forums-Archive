---
title: "7600 gt sli"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by storybookhero on 2008-02-13
I have been trying to Install Ubuntu from the live CD 7.10 and I have yet to get to the actual desktop. when I boot from the live CD it asks me if   I would like to install etc... and soon brings up the load bar.. but when  the load bar is finished all I see is black. I can hear ubuntu's signature startup music..but no video. I have 2 geforce 7600gt vid cards in sli mode someone please help

---

### Post by Pumalite on 2008-02-13
[http://ubuntuforums.org/showthread.php?t=552985](http://ubuntuforums.org/showthread.php?t=552985)
It might not be your SLI. Try the Alternate CD.

---

### Post by storybookhero on 2008-02-13
my only problem with doing the alternate cd is that  I actually have to write the operating system to disk at that point. I'm trying to test out the live cd to see what features have changed and make my decision of wether to install it or not. is there any way to  activate a generic vga driver so that i can atleast get in to the OS?

---

### Post by Pumalite on 2008-02-13
Edit the boot parameters:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
Try:
 vga=0x317

---

