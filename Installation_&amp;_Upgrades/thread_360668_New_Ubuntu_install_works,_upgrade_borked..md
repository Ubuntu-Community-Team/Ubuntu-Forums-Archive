---
title: "New Ubuntu install works, upgrade borked."
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by Tahoe916 on 2007-02-13
I installed ver.10 from an iso, everything works great. Then I installed 200 some odd MB of updates and Beryl in one go, restarted my computer and it locks up at the loading screen, with the orage Ubuntu loading bar. Its like once it gets to the loading of Xserver it borkes out.

So I loaded it in the safe mode (whatever its called, Im an Ubuntu noober) and tried editing the config using dpkg reconfigure xserver-xorg, and changed the video driver to NV from NVIDIA (I have a GeForce GO 6800 Ultra) and it still locks up at the OS boot screen.

Any ideas? I'm willing to try anything. I can boot to the live CD, but I really have no idea how to fix this without just reinstalling and not updating or trying out Beryl.

Thanks guys, appreciate it.

---

### Post by Sqwishy on 2007-02-13
ok so by ver.10 i guess you mean 6.10...?
And i'm not sure what exactly happens, does it make it past the innitial loading screen and then trys to load X but it's all blue with an error?

---

### Post by Tahoe916 on 2007-02-13
Yes sorry, version 6.10, but after the upgrade I can choose 6.17.10 or 6.17.11 I THINK, I can't remember right now.

It boots up, then shows the Ubuntu screen with the logo and the orange loading bar. When the bar gets to the end it locks up and just hangs there, with some visual corruption. I'm stumped.

---

### Post by lojic on 2007-02-13
Pretty common experience in the forums. I've seen several solutions, but for me, booting into the old -10 kernel (hit ESC at the Grub countdown and choose the old kernel), and then installing the restricted modules in Synaptic (search for restricted in the name of the package - you should see that -10 is installed, but -11 isn't).

Oh, don't forget to provide a feedback vote here: 
[http://www.ubuntuforums.org/showthread.php?t=359752](http://www.ubuntuforums.org/showthread.php?t=359752)

Thanks!

---

### Post by Tahoe916 on 2007-02-13
I tried booting into 10, but I ge tthe same thing. I'm reinstalling 10 from the Live CD now and this time I'll try to upgrade without Beryl to see if that's where my problem stems from. PITA for sure, but I'm still new so I'm expecting setbacks like this where I dont know what I'm doing =P

---

### Post by Tahoe916 on 2007-02-13
So I think I figured out what is wrong, but I dont know how to fix it per se, if I set the video driver to NV or NVIDIA in dpkg-reconfigure -phigh xserver-xorg, it wont start xserver, just hangs. If I set it back to VESA, it will. But then I dont have a driver for my 6800GT correct?

Hrmph, getting frustrated lol.

---

### Post by Tahoe916 on 2007-02-13
Also my monitor is 1920x1200 and I can't get that resolution to show up, I can get 16x12 but either way its slow as balls. Need to get the NVIDIA driver I guess...I ran someones script last time when I was installing Beryl, but it didnt work as I had the same problems as before.

Any help is greatly appreciated.

---

### Post by mamarget on 2007-02-13
Sorry, I'm newby!
Can anybody help me how can I update to new version

---

