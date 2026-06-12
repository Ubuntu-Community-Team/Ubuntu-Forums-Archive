---
title: "Problem with boot loader after installing"
date: 2004-12-21
forum: Installation &amp; Upgrades
---

### Post by kalebbo on 2004-12-21
Hello everyone, here is the point: after a year with Fedora, i decided to install Ubuntu 4.10 . So i started the install process, selecting language, location and other things. 
After that i entered the Partition menu. My old partition table was:
Primary partition:
hda1 /boot
hda2 /
swap

Logical partition
hda5 /home
hda6 /var

all formatted with ReiserFS 3.6.
So i decided to format all the partition but /home, marking it as "Keep config and use as it is" (or in english something like that).
So my new table is:
Primary:
hda1 /boot  flag loadable activated ext3
hda2 /   ReiserFS
Swap
Logical:
hda5 /home ReiserFS
hda6 /var ReiserFS

Then i finished the process installing GRUB on MBR and rebooted. 
And now is the problem: when i reboot, the system goes in loop when loading GRUB, writing without end the word "Grub" on the screen.
And the same is for LILO.
Can someone help me? If more info is needed, i'm here.
Thanks

---

