---
title: "Installing Ubuntu 11.04 on Dell Studio 1555"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by lz1dsb on 2011-08-21
Has anyone tried that? I have a Dell Studio 1555 running 64-bit Ubuntu 9.10 for about 2 years with almost no issues but I plan to upgrade it straight to 11.04 64-bit (using fresh install because I also want to format the HDD and partition it in a different way). 
What I'm reading in the web is though a bit discouraging as there seem to be a lot of issues with 11.04 running on this particular Dell model. Quite a shame as Dell is supposed to provide good experience on Linux since they had been selling laptops with Ubuntu preinstalled (or they used to...). Could you share your experience on that? I would appreciate if you could guide me to online resources.

---

### Post by steve11911 on 2011-08-22
Might be worth your time to burn a live cd or two and try them before doing a full install.The link below indicates a successful install on 10.04LTS (IMHO a good choice)

[http://john-hunt.com/2010/08/09/ubuntu-lucid-10-04-on-dell-studio-1555/](http://john-hunt.com/2010/08/09/ubuntu-lucid-10-04-on-dell-studio-1555/)

Ubuntu forums has a section dedicated to Dell hardware:

[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

---

### Post by lz1dsb on 2011-09-01
Thanks for this suggestion. I might as well give it a try on 10.04....

---

### Post by lz1dsb on 2012-01-16
I've finally decided to install 11.10 on my Dell Studio 1555. 
So far I haven't encountered any major issues. Like with 9.10 I had to install the additional video drivers (ATI) and the drivers for the wireless chip (Boradcom BCM4312). 
So anyone out there with the same specs... give it a try ;)
With this upgrade I was even able to solve a long lasting issue with 9.10. I wasn't able to burn disks. Now this works out of the box ;))) 
I'll now close this thread.

---

### Post by VMehrishi on 2012-01-23
> **lz1dsb said:**
> Has anyone tried that? I have a Dell Studio 1555 running 64-bit Ubuntu 9.10 for about 2 years with almost no issues but I plan to upgrade it straight to 11.04 64-bit (using fresh install because I also want to format the HDD and partition it in a different way). 
What I'm reading in the web is though a bit discouraging as there seem to be a lot of issues with 11.04 running on this particular Dell model. Quite a shame as Dell is supposed to provide good experience on Linux since they had been selling laptops with Ubuntu preinstalled (or they used to...). Could you share your experience on that? I would appreciate if you could guide me to online resources.
Hello,
I am New to Ubuntu, And I also Have a Dell Studio 1555 Running Windows Vista 32-bit home premium, I want to Install Ubuntu 11.10, could you please help me install ubuntu?

---

### Post by lz1dsb on 2012-01-26
Sure. Here's what I did.
1. I downloaded the the latest Ubuntu image from [www.ubuntu.com](www.ubuntu.com).
By default they offer to you the 32-bit image. But you're having Dell 1555 like mine, so why not using a 64-bit image. I use such an image. And  a 64-bit image in general should be more efficient on a 64-bit machine ;) So why not use one. I also remember to read somewhere that on a 32-bit image only up until 3GB of RAM is recognized. But I'm not sure. I've never run a 32-bit image on my machine.
2. After downloading the image I created a live USB. On the same site it's shown how to do that. You could also do it in Windows. You'll have to download additional application I think.
3. Start the live USB and wait for it to load {Don't forget to set your BIOS settings so that the laptop is set to boot from a bootable USB. For Dell Studio 1555 you can press F12 while the USP is pluged in and the system is booting. It will open a menu where you can choose from which media to boot}. After that just click on the desktop icon to install Ubuntu. You can also test-drive Ubuntu running it from a Live USB. You can install applications and and change settings. The next time you start your USB Ubuntu live USB it will be all there.
4. If you want you can set how you would like your hard drive to be partitioned. 
5. After installing you'll have to install additionally the Broadcom and ATI drivers. The program is called Additional Drivers. You can search for it. You should have a functioning internet connectivity because the Additional Drivers program should search in the Internet for available drivers and than download and install them. Then a reboot of the machine will be necessary.
6. Login into your new Ubuntu system and enjoy the open source world. It's an amazing experience... Sometime you'll have to tweek a bit, but it very rewarding. 

Hope this helps...

Boyan

---

