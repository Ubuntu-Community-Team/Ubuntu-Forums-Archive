---
title: "Novice Ubuntu user trying to install."
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by Bwdsmart on 2008-02-03
I have downloaded the most recent ISO file and burned it to a disk and i boot from the image. After i boot the image i get the options to install/run, install oem and all the other options on the main menu. i select the top option to install/ run from the cd and i hear the cd spinning up. after a while of loading i get a window saying i must configure my moniter because i am in a low detail display mode or somthing. so i set up my display and click continue. after that this apears on a black screen with a consol below it.

*starting deferred execution scheduler atd   [ok]
*starting periodic command scheduler crond  [ok]
*checking battery state...   [ok]
*running local boot scripts (/etc/rc.local)      [ok]

then a blinking consol.... any help would be greatly apriciated.

---

### Post by Partyboi2 on 2008-02-04
Try using the 2nd option at the main menu I think it is safe graphics mode.
If that does not work, try this:
When you get to where the system stops press
Ctrl+Alt+F2 to get to a terminal
then type
```
sudo dpkg-reconfigure xserver-xorg
```
and choose the driver for your graphics card. If unsure choose the vesa driver. Answer the rest of the questions that are on the screen. If unsure just select the default ones that are displayed. When finished type
```
startx
``` If this works this should allow you to install ubuntu, but you may need to install the correct driver when ubuntu is installed.
Another way is to try the alternate cd
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by hardyn on 2008-02-04
how new an iso?  are you trying out the hardy iso?  this is maybe not advisable at this point.

---

### Post by Bwdsmart on 2008-02-04
it is the most recent x64 version from the website. ill try entering that information into consol and see if that works, thanks for the help. ill be back soon to let you know if that worked out.

---

### Post by Bwdsmart on 2008-02-04
well i attempted both those options and they both end with the same consol i posted before. I can't enter anything into it. anything i type just sends me to the next line. 

the only thing i have found that i can do is press ctrl+alt+del and it brings me to a blank screen and ejects the disk.....any other ideas guys. sorry for being so difficult ive never used any type of linux before and have no idea what im doing.

---

### Post by Bwdsmart on 2008-02-05
i tried the 32bit image and tried to install it, i dont the same message and i get a consol with ubuntu@ubuntu:~$ 


what do i do from here? i think it is working but im not sure how to command it? i figured it would be much more simple.

---

### Post by Partyboi2 on 2008-02-05
> **Bwdsmart said:**
> i tried the 32bit image and tried to install it, i dont the same message and i get a consol with ubuntu@ubuntu:~$ 


what do i do from here? i think it is working but im not sure how to command it? i figured it would be much more simple.
what happens when you try and start gdm?
```
sudo /etc/init.d/gdm start
```

---

### Post by Bwdsmart on 2008-02-05
ill give that a try. I dont even know what that is(this is hte first time ive ever booted a linux based os) so if there is anything i hvae to do other then go click some things let me know. 

just out of curisity am i supposed to be getting a consol? or should i just boot to a desktop and be able to install from there?

---

### Post by Partyboi2 on 2008-02-05
If you are using the desktop live cd you are meant to get to a working desktop, where you click on the install icon. After you have successfully installed ubuntu and rebooted you will get to a gui login screen which is a brown color, where you would enter your username and password which then loads your desktop. The last command I posted is to start gdm and hoepfully give you a desktop. (just type it in after the ubuntu@ubuntu:~$ ) Just out of curiosity is the 32bit you download the desktop version or the server version?

---

### Post by Bwdsmart on 2008-02-05
both are desktop, im trying the alternate right now, if that fails im gona try the gdm command

---

