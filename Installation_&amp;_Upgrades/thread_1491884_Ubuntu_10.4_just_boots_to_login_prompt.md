---
title: "Ubuntu 10.4 just boots to login prompt"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by Ceejay34 on 2010-05-24
I installed 64 bit Lucid Lynx last week. There were some issues with the grub boot manager and my windows boot manager but that was solved thanks to some great help from the guys at the forums. However, about half the time i would boot to reach only a login prompt. If i used CTRL ALT DEL i would then reboot usually into the GUI.
 
So now i only reach a login prompt all the time. How do i get the the GUI to run automatically?

---

### Post by julio_cortez on 2010-05-24
It happened to me a couple of times with Kubuntu but I think it's more or less the same:

Are you able to login using your username and password?
If so, does the GUI load if you (once logged in) type **startx** in the command line?

On a different note, you may want to try
**sudo dpkg-reconfigure  xserver-xorg**
and see if it works ;)

---

### Post by Ceejay34 on 2010-05-24
Yes i can login with my username and password no problem and Ubuntu welcomes me when i do.
I saw startx as a remedy before and tried it then i get a message that screen 0 has already been started or some such ( I cant try it right now cause i am in windows at the moment). An hour ago Ubuntu did start up to the desktop again, I dont really know why it does or does not do that, but i will try your suggestions and get back here thanks for replying

---

### Post by dino99 on 2010-05-24
need some info about your hardware as it seems to be a video driver issue, try to boot in recovery mode or add video=vesa on the boot line. is it a fresh install or a dist-upgrade ?

---

### Post by Ceejay34 on 2010-05-24
Right I am back in the real world here (Ubuntu) so it did just start up properly so I cant test your suggestion i will try it next time it does that

---

