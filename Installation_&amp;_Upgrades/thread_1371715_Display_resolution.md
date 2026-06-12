---
title: "Display resolution"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by zanyjazz on 2010-01-03
I have installed ubuntu on an iMac using Virtual Box. The display options available are 640x480 and 800x600. When I go into Administration, Hardware Drivers none are listed. My machine is online with Firefox working. According to the manual a list of drivers should appear. Can anyone help?

---

### Post by owenisred on 2010-01-03
Snap. I tried to fix this problem so many times - thankfully I got it. (When I say paste - ignore the part that says Quote:)

1. open terminal (Applications > Accessories)
2. Paste
> gksudo gedit /etc/apt/sources.list 
hit enter and type your password (if you are prompted) and enter again.
3. Scroll to the bottom of the text that appears and paste

> deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main 

Save it and close it.
5. open a new terminal
6. paste

> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79 
7. Wait fr the thing to download
8. New terminal paste
> sudo apt-get update 
9. Again add password if necessary
10 paste
> sudo apt-get install xserver-xorg-video-intel-2.4 
11. Enter password once more and wait till the thing finishes

thatll be you fixed

12. Close all programs 
13. Open Terminal and paste
> sudo /etc/init.d/gdm restart 
to reset ubuntu.

When i did it my monitor went crazy on reboot and I had to switch off at plug, but then on second reboot ubuntu's resolution was fine.

Hope I helped!
Owen.

---

### Post by zanyjazz on 2010-01-03
Sorry, done that, made no difference. Still get no proprietary drivers are in use on this system!
There is a little green screen with a lock in front of it, could this have anything to do with it?

---

### Post by zanyjazz on 2010-01-04
Is there a solution to this problem??

---

### Post by owenisred on 2010-01-04
Sorry my post didn't help you - your situation sounded identical to mine... but im just seeing your on a mac so yea its probably totally different. 

Idk this may work? See sharaq's first post

[http://ubuntuforums.org/showthread.php?t=1364460&highlight=resolution](http://ubuntuforums.org/showthread.php?t=1364460&highlight=resolution)

Probably not but you could ask people and see if it might work.

Apologies I can't help you further,
Owen

---

