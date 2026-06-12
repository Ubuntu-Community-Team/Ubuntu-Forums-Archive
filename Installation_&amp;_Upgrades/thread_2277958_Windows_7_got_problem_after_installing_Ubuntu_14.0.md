---
title: "Windows 7 got problem after installing Ubuntu 14.04 LTS"
date: 2015-05-12
forum: Installation &amp; Upgrades
---

### Post by dao.alinker.tz on 2015-05-12
Hello guys,

Let me post to ask a common question in this forum. Dual boot problem I am trying to install Windows 7 and Ubuntu 14.04 LTS (both are 64 bit versions). I installed Windows 7 first then Ubuntu. Everything was fine until I rebooted my Ubuntu after installation is completed. But as my computer boot up, linux grup is popped up and I chose "windows 7" to make some software installations. Here I got a problem like the image below. My computer screen goes like that but my windows 7 is still working (cuz I heard the windows log on song). I dont know what the problem is. Can anyone helps me please??? Thanks. PS* Ubuntu is fine whenever I log in.

[IMG]http://s30.postimg.org/y4ri3jvj5/IMG_2318.jpg[/IMG]

---

### Post by Mark Phelps on 2015-05-12
HOW did you install Ubuntu? Did you use the "install alongside" option, which allows you to use a slider to shrink down Win7?  If so, then it's likely that you corrupted Win7 in the process -- which is a common result of installing that way.

The problem you have is more typical of Windows video driver problems -- but driver are, after all, software, and if the filesystem gets corrupted, and that affects the drivers, you will get the problem you have.

The problem is further aggravated by your needing to reinstall the Windows video drivers, but you can't do that from Ubuntu.

What will most likely work is something know as a "refresh" -- in which you reinstall the Windows OS but leave your apps and data intact.  That requires Windows installation media.

---

