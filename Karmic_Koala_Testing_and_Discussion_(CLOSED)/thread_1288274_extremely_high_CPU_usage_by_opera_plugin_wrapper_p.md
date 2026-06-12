---
title: "extremely high CPU usage by opera plugin wrapper process"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by legolas_w on 2009-10-11
Hi
I am wondering how opera plugin wrapper uses +80% of cpu time even when opera is idle. Anyone see same problem?

I am using Karmic 32 bits, core2due cpu and opera 10.00.

Thanks

---

### Post by hikaricore on 2009-10-11
I noticed the same here.
It wasn't apparent at first since i have a dual core and it wasn't really slowing me down..

[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/opera.jpg[/IMG]

It floats between 85-100% for no obvious reason.

---

### Post by Leighman on 2009-10-11
I occasionally find this after Flash videos.  I'm sure it has something to do with that.
Using the latest 10.1 snapshot

---

### Post by legolas_w on 2009-10-11
Are you guys experieng similar problem with FireFox as well?
sometimes firefox 3.5.3 shows the same problem.

---

### Post by hikaricore on 2009-10-11
No issues with ff, it rarely uses above 5% cpu max.

---

### Post by ronacc on 2009-10-11
this is caused by badly written flash files (usually adds) , it has been a problem for some time with opera plugin wrapper.

---

### Post by gnothi on 2009-10-12
I had that problem with Opera on Jaunty. It was caused by the *flashplugin-nonfree* that's installed from the repositories.

My solution: I dowloaded **install_flash_player_10_linux.tar.gz** from [_Adobe.com_](http://get.adobe.com/flashplayer/) and copied the **libflashplayer.so** file into my **/usr/lib/mozilla/plugins** folder (where both Opera and Firefox will find it), then I completely removed *flashplugin-nonfree* (and its installer) using Ubuntu's software package manager. I killed the (over)active *operapluginwrapper* process with System Monitor.

Problem solved. :)

---

### Post by OwnSurname on 2009-10-22
Seriously, I mean, that crappy piece of **** took 2.4 GB of memory, out of the blue. It froze my machine for seconds. If it's bad written flash, then they should fix / prevent it. I think I'll wait for KK, and then if the problem is still there, I'll try the fix proposed by legolas_w.

---

### Post by OwnSurname on 2009-10-22
Also, I found out the culprit, at least for me:

[http://www.slideshare.net/ksrpaniraj/c-programming-by-dennis-ritchie](http://www.slideshare.net/ksrpaniraj/c-programming-by-dennis-ritchie)

coudl someone else try the page out? I'm on 9.04, Opera 10.00 build 4585, and 64bit architecture for both. Check it out what happens when I open the page ... sigh ...

---

