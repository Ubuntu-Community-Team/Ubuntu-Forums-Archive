---
title: "Xorg needs 95-99% of CPU | nomodeset after upgrading"
date: 2017-03-01
forum: Installation &amp; Upgrades
---

### Post by elo. on 2017-03-01
Hey,
 
I've got a problem which is hard for me to describe. First my specs: Toshiba Laptop Portege Z30 A 1CN with an i7 4600U and integrated GPU HD4400. 
 
Two weeks ago i've installed Ubuntu 16.04 x64 without any problems (no commands for booting needed or sth. else). 
 
Two days ago i've got the glorious idea to upgrade to 16.10 to test it again. (I've had problems with Ubuntu in the past too, but well...it worked flawlessly for 2 weeks...so why not give it a try? bad idea I know).  After the upgrade I needed to boot it with nomodeset because the blackscreen problem appeared. With the command booting was possible but..well, Ubuntu didnt work well. It was extremly! slow, Xorg needed about 95 to 99% of my cpu.
 
So I decided to fresh install 16.04. But know I needed nomodeset there too, even to install. After installing it too, and the problem with Xorg appeared there too. That was, for me ,the most confusing part. Its absoluetly unusable at the moment and I don't know what to do. I've checked some logs and noticed that something with the gpu-driver (noticed from gpu-manager.log) maybe is not correct "has intel? no" and an error a few lines before stating that a driver couldnt be loaded/accessed. 
 
I attached the log. If you need more just say it. I'm not that experienced with Linux till now, always got some problems so needed to flee from it again and again.
 
Hope you guys can help me :)
 
Thanks!

---

