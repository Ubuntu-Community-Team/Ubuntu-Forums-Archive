---
title: "Installation problems + Q's"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by Zonkou on 2007-08-21
Hello, I am trying to instal Ubuntu 7.04 (the most updated) on my new laptop that I got yesterday, that has vista home premium on it.

My Specs:
Inspiron 1520, Intel Core 2 Duo T7300, 2.0GHz, 800Mhz, 4M Cache
2GB, DDR2, 667MHz 2 Dimm
256MB NVIDIA GeForce 8600M GT
160G 7200RPM SATA Hard Drive

the error im currently getting, ive tried to research it on these forums, but i am a COMPLETE noob when t comes to Linux and Ubuntu, so the directions are...a little too advanced for me.

the error :

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)


Other questions I had were, that I only have 1 harddrive, is it still possible to have two operating systems work properly and easily on one harddrive?  Also, the school computers that I use for class when im at school give us a GUI menu at the start-up of the computer that allows us to pick the different operating systems (xp, linux, unix, etc.) I was wondering how that is possible and if someone knows how to do that as well?  I know its a lot, but you guys seem to be on the ball on this stuff and VERY knowledgable.

Thank you.

---

### Post by Pumalite on 2007-08-21
You HAVE TO resize your partition with the Vista partitioner. Besides that, your problem: /bin/sh: can't access tty; job control turned off
(initramfs) has been extensively discussed in this forum. Check this thread: 
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

---

### Post by Zonkou on 2007-08-21
I made sure to come here and get direction on how to install Ubuntu first, so I made sure to resize my partitions, to allow room for ubuntu. 

Can ya also answer my other questions :)

---

### Post by Pumalite on 2007-08-21
You can have both OS in one hard drive. Once you install Ubuntu and Grub in the MBR, in a working system, you obtain a Grub menu to boot either OS.

---

