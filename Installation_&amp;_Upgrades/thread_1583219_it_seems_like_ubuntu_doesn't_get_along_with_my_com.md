---
title: "it seems like ubuntu doesn't get along with my computer"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by speedy18us on 2010-09-27
hi guys. i recently have decided to install again ubuntu server on a computer, which will have some services like ftp, samba, apache, php, mysql, ics, etc. the configuration is: processor amd le 1200, 512mb ram ddr2, hdd 160gb sata 2, 2 network cards,  dvd-rw. i've have tried 10 times to install 3 different versions of ubuntu server (9.10 server i386, 10.04.1 server i386 and 10.01.1 server amd64) with 2 different hdd (the second one is a 40gb ata) and 3 different optical drives. i've even tested the rams with memtest. the system is perfect, it's 6 months old. win xp worked perfectly.

the installation gives me some errors, but each time is different and it pops-up after installing the base system packages. the screen turns red and says that it cannot continue the setup because of some packages.

the screens (the last time at least):
[http://img137.imageshack.us/img137/3366/27092010996.jpg](http://img137.imageshack.us/img137/3366/27092010996.jpg)
[http://img716.imageshack.us/img716/9963/27092010997.jpg](http://img716.imageshack.us/img716/9963/27092010997.jpg)
the first image is the forth (alt+f4) terminal, the second is the main

i've spend 2 days figuring out what the hell is wrong.

LE: i've md5 tested the discs and the discs are ok.

---

### Post by mörgæs on 2010-09-27
Have you tried an alternate install? 
Do you have wired internet access while installing in order to download upgrades?

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by thestagevu on 2010-09-27
Try xubuntu

xubuntu is for old pc !! 

So this should work :) 

Come back to me if it does work.

Thanks,

thestagevu

:):):):):)

---

### Post by speedy18us on 2010-09-30
i've tried 12 times. i've tried even with ubuntu 10.04.1 alternate, then i gave up and installed on another computer on the same drive, it worked perfectly. then i've putted the hard drive back into this "trouble" computer. after a few seconds it says "gave up waiting for root device"... :o what? and it droped me in a shell called busybox. i exit it and there it was the system working. i've changed the resolution of terminal and restarted. there it was again the error. and this time the exit command does nothing. what the hell is going on? on this system i cannot use ubuntu.

---

### Post by mörgæs on 2010-10-01
Can you install a minimal Ubuntu?
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
The smallest installation possible, don't pick anything from the selection list during the installation.


Which screen card do you have?

---

### Post by |{urse on 2010-10-01
Just a word of encouragement, once you work out the initial problems, ubuntu will be well worth your troubles.
:guitar:

---

### Post by |{urse on 2010-10-01
Also, can you give us your motherboard make and model? Have you tried installing to a barebones system and adding hardware after the install? I've had to do that a couple times for customers. Maybe if you 86 one of those nics first?

---

### Post by |{urse on 2010-10-01
Also, the "waiting for root device" error can be rectified this way,

[http://zeeis.me/ubuntu-boot-error-simple-fix-gave-up-waiting-for-root-device/](http://zeeis.me/ubuntu-boot-error-simple-fix-gave-up-waiting-for-root-device/)

Worked for me on both Lucid and Intrepid. If all else fails install to the hard drive on the other pc, return the hard drive to your target system then follow those instructions. Not a pretty way to install ubuntu but it will probably work.

---

### Post by speedy18us on 2011-05-06
sorry for replying so late, but i made a trade: my computer with another one. the problem was the old computer. i have installed ubuntu on my new machine since then. it works perfect with ubuntu server 10.10. thanks guys.

---

### Post by mörgæs on 2011-05-07
Good, please mark the thread 'solved'.

---

