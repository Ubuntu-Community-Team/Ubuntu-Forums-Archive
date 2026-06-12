---
title: "Just get Black Screen..."
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by roclafamilia on 2008-01-13
when i try to install ubuntu it starts to load and then the screen just goes black...it stays black and does not change, i let it sit there for like 20 minutes...

here is my hardware
Intel E6600
Asus P5W DH Deluxe
4GB ram
Nvidia 6600GT
160gb SATA hard drive


i think its the video card but im not sure how to fix it.

---

### Post by i.gerardus on 2008-01-13
I have exactly the same problem, but the difference is in the past ubuntu did work! I had to remove as my university didnt support linux, but now they do. I think there is fault with the cd I am using. I am going to go buy the ubuntu book for myself this evening, it has the real cd with it and loads of info

---

### Post by Partyboi2 on 2008-01-14
Try booting with nosplash and remove quiet.
To do this when you are at the main menu press F6
at the end of the line you will see
```
splash
```
change it to ```
nosplash
```
and delete ```
quiet
```
then press enter.
Removing the quiet option will allow you to hopefully see where the boot process is stoping.
also have you tried to boot with safe graphics mode? (option 2 at the main menu)

---

### Post by roclafamilia on 2008-01-17
so i can boot in safe graphics mode but how do i make it so that it boots from the hard drive in safe graphics mode?

---

### Post by cecure on 2008-01-17
1

---

### Post by roclafamilia on 2008-01-17
i am booting using the 2nd option in the boot menu like the other user stated before. i can boot up, i am actually on the live cd right now, but getting it to boot from the hard drive is the problem. im installing it on another harddirve right now to see if it was the hard drive.

---

### Post by cecure on 2008-01-17
if you have ubuntu installed go to a terminal and enter the following:
Code:

sudo gedit /boot/grub/menu.lst

find where your ubuntu install section is and add
Code:

xforcevesa

to the line that begins with kernel.

save and reboot
good luck

---

