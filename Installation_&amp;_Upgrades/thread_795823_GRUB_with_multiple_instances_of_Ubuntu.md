---
title: "GRUB with multiple instances of Ubuntu"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by diafygi on 2008-05-15
Hey all,

I need some help understanding how to configure GRUB when I have multiple instances of Ubuntu and Windows installed. I used to just have XP and one Ubuntu, with a separate partition for my personal file. However, I wanted to start playing around with the Compiz-Fusion development version, so I cleared up some space and installed another instance of Ubuntu.

The second installation of Ubuntu recognized the other OS's just fine, so the grub menu appears with XP, Ubuntu 1, and Ubuntu 2. However, I will eventually delete the second Ubuntu install when I get done playing with compiz-dev. This worries me because I suspect my MBR is pointing to the second Ubuntu install. If I simply delete the partition, GRUB won't even start, right?

How do I reset my MBR to point to my first install of Ubuntu? And how to I reset the GRUB menu on my first Ubuntu install to find the second Ubuntu install?

I've attached a picture of my hard drive setup (via gparted). I'm running Hardy on both instances.

Thanks all!

---

### Post by EXCiD3 on 2008-05-15
If you delete the partition you can just reinstall grub using the LiveCD through this thread: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The command "find /boot/grub/stage1" will find the location of /boot/grub that will give you the correct grub after you delete the partition.

---

### Post by diafygi on 2008-05-16
> **EXCiD3 said:**
> If you delete the partition you can just reinstall grub using the LiveCD through this thread: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The command "find /boot/grub/stage1" will find the location of /boot/grub that will give you the correct grub after you delete the partition.

Thanks a bunch. I think you found what I was looking for.

---

### Post by EXCiD3 on 2008-05-16
No problem! I've been in the same situation several times myself. ;)

If this worked, mark your thread as solved by clicking Thread Tools at the top of the page also click the Thanks button (blue medal) on the posts that helped so that other users can find answers easier.

---

