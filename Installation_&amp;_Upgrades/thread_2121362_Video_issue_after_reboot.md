---
title: "Video issue after reboot"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by c.pfarher on 2013-03-01
I installed ubuntu 12.10 remix...but I have some problems:

When I reboot, it doesn´t show grub and the system boot directly to ubuntu (my PC is UEFI - see thread [http://ubuntuforums.org/showthread.php?t=2107873&page=1](http://ubuntuforums.org/showthread.php?t=2107873&page=1)).... although i don´t delete the windows partition... (ubuntu boots ok and show me de desktop correctly) but it´s boot ok and I don´t have problem with the video....

As ubuntu live don´t recognize the ethernet and wireless card of my notebook, I use a script for download the .deb files in other computer and then installed for recognized the ethernet card with success... for this, I install linux-backports-modules-cw-.. When the instalation was finished,  I reboot the pc and now I have internet, but ubuntu boots in console mode (no graphics mode ;( )... 

I execute startx command, but It show me an error.

I attached some files here for try to solve the problem: 
 Xorg0.txt (10.2 KB) => this is the Xorg of system installed in hard drive, and it´s where is the video problem.

 Xorg0.txt.zip (6.2 KB) => this is the log of Xorg with live CD where video was ok.

Thank you!

---

### Post by c.pfarher on 2013-03-07
I run X -configure and then copy de Xorg file generated to /etc/X11/xorg.conf, and now it´s work! :)

---

