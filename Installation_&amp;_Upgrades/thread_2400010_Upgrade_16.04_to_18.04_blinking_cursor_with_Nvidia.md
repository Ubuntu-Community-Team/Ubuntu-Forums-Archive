---
title: "Upgrade 16.04 to 18.04 blinking cursor with Nvidia"
date: 2018-09-01
forum: Installation &amp; Upgrades
---

### Post by kraizeg on 2018-09-01
Hi all:
I have had a problem during upgrade last day, the upgrade says succesfull but when reboot i find a problem, it runs well untill the proccess GDM, where it becomes blinking and ctrl+alt+f5 is freeze for about 2 minutes. triyin to solve this, i couldn´t login in tty anymore! :(
here is the proccess i have done succesfully, maybe would help someone:

Initialice grub, reboot and when the scrren logo is out, press Shift key (right)

Go to terminal, first:
Mount file system with: 
$mount -o remount,rw /

Activate ethernet:
$ifconfig -a
$sudo ifconfig eth1 up 
in my case etp0s15 was the name of ethernet adapter
$sudo dhclient eth1

Introduce DNS
$sudo nano /etc/resolv.conf
type the next line in the editor:
nameserver 8.8.8.8
ctrl+o save, ctrl+x exit
$sudo /etc/init.d/networking restart

$ping [www.google.com](www.google.com)
ctrl+c for stop
if ping is ok now we can download the drivers in my case, i have Nvidia:
install these libraries with apt-get install:
libglvnd0, xserver-xorg-core, and libgl1-mesa-glx

My old driver 100% functional on 16.04 was v340, but it doesn`t work on 18.04, v390 is ok.
$purge nvidia
install with $apt-get install nvidia-390

Reboot.


Now tty is ok and desktop is there!
Yuju!
Loging in see a big resolution, 640x480 as well, and no options to change it.
Changin resolution of display is as easy as:
open tty:
$sudo nano /etc/default/grub

Uncomment this line and change the value you want to:
GRUB_GFXMODE="800x600"
and update grub:
$sudo update-grub

Reboot.
hope to be usefull
kind regards

---

### Post by kc1di on 2018-09-01
Try adding nomodeset to the boot line after quiet splash
like in the post [http://https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu/](https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu/")

once you have the desktop up and running you can reinstall the correct nvidia driver for your card. 
I recommend installing inxi ```
sudo apt install inxi
``` also it's a great tool for troubleshooting systems and give a good overview of your system. 
good luck

---

