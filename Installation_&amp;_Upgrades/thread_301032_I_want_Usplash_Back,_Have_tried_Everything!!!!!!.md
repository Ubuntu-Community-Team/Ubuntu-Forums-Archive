---
title: "I want Usplash Back, Have tried Everything!!!!!!"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by Chazall1 on 2006-11-16
My usplash was working fine in Dapper with Kernel 2.6.15-25, I did a kernel update to 2.6.15-27 and lost my usplash. Tried several how to's and could not figure it out. I upgraded to Edgy and have tried everything. I installed Startup Manager (SUM) thinking I could resolve this issue. When I went to start (SUM) the GUI pops up for a brief moment and that is it, will not run.
When I go to /usr/lib/usplash and look at the file usplash-theme-ubuntu should I see an image on top of this folder. When I try to open the file with Gimp, I get no file. I have not configured my system very little from the system defaults. This has driven me nuts for the past few weeks.

Need Help with usplash!

---

### Post by Jimmy_r on 2006-11-18
Firstly, the reason why gimp is unable to open usplash-theme-ubuntu is that it is a .so file. That means it is converted to a format the computer can read, and it is as it should be.

Secondly, can you open a terminal and do these commands:
```
cd /usr/lib/usplash
ls -l
```
and post the output of the last command.

Thirdly, It appears as I have a bug in SUM.
Please do these commands:
```
cd ~/.sum/
./sum.py
```
And post the output.

---

### Post by ethan961 on 2006-11-18
Maybe try ```
sudo update-alternatives --config usplash-artwork.so
``` It will give you a choice between usplash modules. Press the number of the line that says ```
/usr/lib/usplash/usplash-theme-ubuntu.so
```(it may be the only choice). It worked for me when I wanted my usplash changed back to the default. But if that does not work, try ```
sudo aptitude install galternatives
``` and then type ```
gksudo galternatives
``` and select "usplash-artwork.so" and make sure that the option ending with "usplash-artwork-ubuntu" is selected. 
I can't think of anything else that might help at the moment, so I hope that works! :)
Hope I can help, 
Ethan

---

### Post by Chazall1 on 2006-11-19
I sent the Usplash and SUM outputs. I looked at galternatives, everything was fine. I have a Intel 82865G Integrated Graphics Controller (rev 02) 
(prog-if 00 [VGA]) on a Dell Dimension 3000 with 1 gb ram, Intel(R) Pentium (R) 4 CPU 3.00GHz, L2 cache 1024 kb

Something is not configuring from Grub to activate the usplash properly. My screen is not totally black, the 17" Dell LCD monitor is luminated to a small degree, Not Pitch Black, with a flashing curser at the top left of the screen that moves down 1/4 the way and I get the loginscreen. Time about 40 sec for boot. I have just realised, that sence my upgrade from 6.6 to Edgy, my swap partition will not mount on boot and restarts. I have to go into gparted to Swapon.

---

### Post by ethan961 on 2006-11-20
I have heard a lot of funny things about dapper-edgy upgrades, maybe this is one of those funny things. Is usplash even installed? Galternatives should show if it is--but maybe not. Try ```
sudo aptitude install usplash-theme-ubuntu 
``` and then ```
sudo dpkg-reconfigure usplash
```. Does Grub's menu.lst say "quiet splash" for the non-recovery kernel?
I have not heard of anything like this, though it seems that no usplash is loading since you can see a cursor during boot.
Ethan

---

### Post by Chazall1 on 2006-11-27
I have been working on this for weeks,(on and Off) I had upgraded to Edgy and had no Usplash, just a black screen with a blinking curser in the upper left corner. I have a Dell Dimension 3000, with a i82865G graphic card and a Dell E176FP monitor. Its all in the resolution, Here is what I did:

1.  sudo gedit /etc/usplash.conf set the resolution to 640x480
then run  sudo update-initramfs -u

2.  sudo gedit /boot/grub/menu.lst
FIRST: Check the line that looks like this   #defoptions=quiet splash    I had made changes to the setting from what I read, This is the default setting
SECOND: go to the end of Kernel line and it sould be   ro quiet splash

    sudo update-grub

3.  sudo dpkg-reconfigure linux-image-$(uname -r)

This worked for me, I did not think I would ever see Usplash, Hope this works for you!!!!!!

---

