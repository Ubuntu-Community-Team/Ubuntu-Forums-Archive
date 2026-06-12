---
title: "Why can't I boot after installing? Please help :("
date: 2014-11-12
forum: Installation &amp; Upgrades
---

### Post by EvanPowers on 2014-11-12
I installed Ubuntu on to my windows 7 computer using a flash drive. I was asked if I wanted to install or try Ubuntu. I installed it. Now when I turn on my computer it takes me back to the same GRUB menu asking if I want to install or try Ubuntu. I already installed it???? I'm getting really frustrated here, someone enlighten me please :(

---

### Post by sammiev on 2014-11-12
Sorry to ask, have you removed the flash drive before booting?

---

### Post by EvanPowers on 2014-11-12
Thanks for the quick reply. I haven't removed or touched the flash drive since the original installation.

---

### Post by EvanPowers on 2014-11-12
I am "trying Ubuntu" right now. I see that I now have a second storage drive. Inside are a bunch of folders and vmlinuz. Is this file the culprit?

---

### Post by sammiev on 2014-11-12
You installed Ubuntu to a HD or to a flash drive?
How many drives do you have installed?
Where were you trying to install Ubuntu to?

---

### Post by yancek on 2014-11-12
If you used a flash drive to install Ubuntu you would have needed to set the boot priority in the BIOS to first boot from that flash drive.  If you still have the flash drive plugged in, it will boot from it forever and not boot anything on your hard drive until...you remove it or change the boot priority in the BIOS.  The vmlinuz file is the kernel, the core of the operating system.

---

