---
title: "Problems with GRUB after copying Ubuntu 7.10 drive image back to hard drive."
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by 0graham0 on 2008-04-11
Hello,

I recently imaged the SATA hard drive of an Asus F3sv, which was running Ubuntu 7.10 for amd64. When imaging I kept all the partitions intact. After copying the image back to a clean drive, I attempted to boot the computer and was greeted by a black screen with "GRUB" and a blinking cursor.

I then booted the computer from the ubuntu alternate install CD, and reinstalled the grub bootloader to /dev/sda1

Still, I am greeted by the same boot screen (GRUB and a blinking cursor).

Any help is greatly appreciated, thanks.

---

### Post by David Robertson on 2008-04-11
May not be helpful but ...

If your drives have different geometries and your imaging software doesn't understand the file system inside the partitions, it may not be able to fit the 'image' into the new  slightly different partition.

---

### Post by 0graham0 on 2008-04-11
thanks, i think i will just do a clean install and move data back over...seems like too many variables in backing up all those partitions

---

### Post by David Robertson on 2008-04-11
Your other choice would be to install and partition the way you would like, then use the install CD to copy all your old stuff into the right partitions. This holds any software changes you have made.

Personally I find a completely fresh install (then copy old data) solves a heap of problems.

---

### Post by David Robertson on 2008-04-11
The other thing I have found useful is copying /var/cache/apt/archives over to a new machine. It contains all those latest packages you spent ages downloading. Makes for a quick upgrade.

---

### Post by adrian15 on 2008-04-11
> **0graham0 said:**
> 
I then booted the computer from the ubuntu alternate install CD, and reinstalled the grub bootloader to /dev/sda1


Try to reinstall grub bootloader to /dev/sda.

adrian15

---

### Post by 0graham0 on 2008-04-11
I tried /dev/sda as well, with no luck. thanks for the advice, but i have conceded defeat and gone ahead with the clean install...oh well

---

### Post by prshah on 2008-04-11
> **0graham0 said:**
> 
Still, I am greeted by the same boot screen (GRUB and a blinking cursor).



You have to mark the relevant partition as "bootable", or an "active" partition. (Command "a" in fdisk).

---

### Post by adrian15 on 2008-04-11
> **0graham0 said:**
> I tried /dev/sda as well, with no luck. thanks for the advice, but i have conceded defeat and gone ahead with the clean install...oh well

Try to [reinstall grub with Super Grub Disk](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub) before the clean install, sometimes it work when traditional grub install does not work.

adrian15.

---

### Post by adrian15 on 2008-04-11
> **prshah said:**
> You have to mark the relevant partition as "bootable", or an "active" partition. (Command "a" in fdisk).

I doubt that grub hangs because it does not find any active partition. Grub should boot anyways. But you can try it (after trying to fix Grub with SGD as I have suggested you, pleeeaaseee) to see if it does any good so that everyone of us learn it.

adrian15

---

### Post by 0graham0 on 2008-04-11
Well, I went ahead with the clean install and then read all of the posts and decided to write the image to the drive again and try out your advice.

However, the drive works perfectly! I was using Norton Ghost 11 off of Hirem's Boot CD for the record. The first time I transferred the image back to the drive I ran into grub problems. I wiped the drive clean and transferred the image again and now it works perfectly.

Thanks for everyone's advice, I wish I could have provided a better laboratory to test out your theories...

---

