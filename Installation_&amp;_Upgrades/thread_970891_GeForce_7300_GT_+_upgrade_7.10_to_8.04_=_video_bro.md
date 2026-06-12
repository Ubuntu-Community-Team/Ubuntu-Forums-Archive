---
title: "GeForce 7300 GT + upgrade 7.10 to 8.04 = video broken"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by Stason on 2008-11-04
Finally got my hand to upgrade to the LTS, i.e. 8.04 from 7.10. While my native 1360x768 is now supported by the built-in drivers, but naturally compiz do not work. Removed old Envy and installed new one. Envy did report to install and configure everyning, but after reboot I get that nasty lowres stuff. Tried to install latest Nvidia driver manually - same thing. Rolled back to the backup, but any pointers for my second attempt would be appreciated. Thanks.

P.S> Is it also normal that 8.04 is around 700Mb fatter than 7.10?

---

### Post by Stason on 2008-11-05
bump

---

### Post by justacreep on 2008-11-06
I have the same video card on a desktop I'm trying to install Ubuntu on. After install I have a solid black screen. If I find a fix I'll update this thread. Let me know if you find anything it would be appreciated.

---

### Post by justacreep on 2008-11-06
Stason,

I got mine working!

boot into the shell and run this command:
sudo dpkg-reconfigure xserver-xorg

Enable buffering then take all the defualts. After reboot you'll come to prompt telling you that you are running in low graphics. Select "configure" from that prompt. Select the nVidia 7 series driver from the menu. After you get in go to System> Preferences> Appearence; select the "visual effects" tab and select extra. You get another prompt telling you that you need the restricted driver. Select "enable" from that prompt. 

That worked for me :)

---

### Post by Stason on 2008-11-07
Have used Envy to get the restricted drivers or they came with Ubuntu? Are we talking about 8.04 Hardy?

---

