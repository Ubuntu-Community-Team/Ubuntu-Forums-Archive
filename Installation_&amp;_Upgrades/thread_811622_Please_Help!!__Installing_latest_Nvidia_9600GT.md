---
title: "Please Help!!  Installing latest Nvidia 9600GT"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by smarks on 2008-05-29
I am having trouble installing the latest driver for my video card. The file is saved on my desktop.The driver i have installed now is the 169. but i want the latest one which is the one im trying to install.

Ubuntu 8.04 Hardy Heron
Driver: NVIDIA-Linux-x86-173.08.pkg1.run

I go into TTY and type 
login: root
PW:*****
/etc/init.d/gdm stop
then
sh /home/smarks/desktop/NVIDIA-Linux-x86-173.08.pkg1.run
sh: Can't open /home/smarks/desktop/NVIDIA-Linux-x86-173.08.pkg1.run

Please Help if anyone can this has been bugging me for weeks and no one seems to be able to help. 
Also when im booting up just before my login screen my background has tons of little choppy marks and it wont let me login so i have to reboot several times then it finally works. this happends all the time, im thinking its the driver but idk.

---

### Post by nic2 on 2008-05-29
You need to install the build-essential packages - use the Synaptic Package Manager or type the following command in a Terminal:

sudo apt-get install build-essential

---

### Post by smarks on 2008-05-29
smarks@smarks:~$ sudo apt-get install build-essential
[sudo] password for smarks: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
 

Any other ideas

---

### Post by nic2 on 2008-05-29
Have you downloaded the driver from [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")?

---

### Post by smarks on 2008-05-29
the one i downloaded is called NVIDIA-Linux-x86-173.08.pkg1.run. 
I got it here [http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

---

### Post by nic2 on 2008-05-29
Did you run the command as root (e.g. sudo sh NVIDIA-Linux-x86-173.08.pkg1.run)?

---

### Post by smarks on 2008-05-29
Ya everytime I would get this

smarks@smarks:~$ sudo sh NVIDIA-Linux-x86-173.08.pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.08.pkg1.run

---

### Post by smarks on 2008-05-29
I had the file executable. I have permission. im typing in the right path. i dont understand why in TTY i can't open it. I can open it in konsole but it says i have to run in TTY

---

### Post by nic2 on 2008-05-29
If I go on the original command you typed in your first post, you have used _d_esktop and not _D_esktop.  Please confirm this and try again.

---

### Post by smarks on 2008-05-29
wow amazing. that worked. i rebooted but now my res is stuck on 800 x 600.

---

### Post by nic2 on 2008-05-29
Same problem here - this is how I came accross your thread ... if and when I come accross the answer, I will let you know (if you could do the same for me).  

Good luck

---

### Post by smarks on 2008-05-29
for some reason when i try to configure the card theres no Geforce 9 series. highest is 8

---

### Post by smarks on 2008-05-29
thanks for your help. im atleast glad im over that first hump. Ill let you know if i find anything.

---

### Post by ma245 on 2008-05-29
for configure NVIDIA 9600 GT

Ctrl+Alt+F1

sudo /etc/init.d/gdm stop

sudo sh NVIDIA-Linux-x86-xxx.xx-pkg1.run

sudo /etc/init.d/gdm start

sudo gedit /etc/default/linux-restricted-modules-common

DISABLED_MODULES=”nv”

this is all:KS

---

### Post by smarks on 2008-05-29
No F-ing way it works. looks soo clear and nice now. when i try to run x server settings it says 


You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by nic2 on 2008-05-29
> **ma245 said:**
> for configure NVIDIA 9600 GT

Ctrl+Alt+F1

sudo /etc/init.d/gdm stop

sudo sh NVIDIA-Linux-x86-xxx.xx-pkg1.run

sudo /etc/init.d/gdm start

sudo gedit /etc/default/linux-restricted-modules-common

DISABLED_MODULES=”nv”

this is all:KS

Tried it yesterday after reading about it in another tread - unfortunately did not work for me

---

### Post by smarks on 2008-05-29
Im also getting this

desktop effects could not be enabled

---

### Post by smarks on 2008-05-30
This is weird. after i install the video driver and then reboot. It trys to load load graphics and my res is 800X600. I am think its somthing with the xorg.conf file

---

### Post by smarks on 2008-05-30
nic2 are you sure you tried this. This is what the lower half of mine looks like incase urs is different.

sudo gedit /etc/default/linux-restricted-modules-common

# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="nv"

Cus i reinstalled ubuntu and redid everything and that solved the 800x600 problem agin.

---

