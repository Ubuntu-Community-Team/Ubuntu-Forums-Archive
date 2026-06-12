---
title: "Install on Gigabyte U60 UMPC"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by MoridinBG on 2007-11-30
I'm doing my best for the past couple of hours to get Ubuntu installed on this device. As it has no CD (the drive would be bigger than the device itself (: ) I am tring to install from USB stick. Got it to boot from it (syslinux, etc... ) but I'm stuck on detecting the CD. When I try to mount /dev/sda1 on /cdrom it says there is no such device. "cat /proc/partitions" returns my two HDD partitions, as well the sda device with one partition: sda1. So it looks as if the USB stick is recognised.

The chipset is VIA VX-700, and it's USB controller is detected.

Also the image doesn't fit the screen. In the virtual terminals the last couple of lines are outside the screen. On external TFT panel it is the same. But if I boot from the NetworkInstall kernel the screen is perfect. And the device has only wireless networking. 


Any clues how to start the instalation?

---

### Post by MoridinBG on 2007-12-01
OK, I had to use a not so elegant solution, whicch I had used more than once befor for devices without CD (particualy a Toshiba Portege 3500 tablet PC, which would boot only from HDD or PCMCIA CD (not USB one)).

So I installed VMWare 1Ghz VIA CPU.... I don't want to talk about that....... Installed base ubuntu system (console only) so I had GRUB and working Linux system. I didn't install the full Ubuntu system, as it would take ages inside the vmware image, and as I feared it would make some hardware specific settings.

I made a separate /boot partition and this was important for my set up, as I have 30GB HDD, 8GB for backup, 10 for Windows (I am not sure yet how much of the hardware is supported with linux, so I will exterminate the Windows after I manage to get linux working), 10 for linux and there I had to install the console only system. And if /boot was on it later this would be a problem.

After getting a working grub I proceeded in more or less standart way. Created a 700MB partition for the Alternate Install ISO, copied it there, copied Installation vmlinuz and initrd to /boot

**NOTE: Don't use the once found on the alternate installation disk. I am using Kubuntu and when booted from it's vmlinuz and initrd the Installer was sure it wanted to copy the files from CD. And I had the problem described in the upper post that /proc/partitions was able to see my partitions, but I was unable to mount them**

I made the necessery entry in menu.lst, rebooted and the installer happily found the ISO image on the 700MB partition. The system is installing just now with no problem so far.

If anyone needs more specific instructions (this are just outlines of the process) just let me know.

---

### Post by sarelgrin on 2008-02-10
Hi MoridinBG,

I tried a more simple approach, I used Wubi (since I didn't know if the hardware is compatible, I needed the fastest and easiest way to check)

I was a little dissapointed to discover all the thing that didn't work correctly after the installer finished it's job. First of all the wireless network adapter wasn't detected and therefor didn't work. Second: the display adapter wasn't recognized as well and ubuntu assigned a generic display adapter to xorg.conf. Third, and most annoying, the touch screen didn't work correctly and I had to use the miniature touchpad instead.

I would really like to have ubuntu run on this great  piece of computing but, if the hardware has such critical unsolved issues I really don't see it happening.

you haven't written what happened after your installation, how did things go (wubi installs 7.04. maby if  you installed 7.10 you had more luck than I had...)

I will be glad if you could fill me in...

---

### Post by l3th0x on 2008-04-07
Hi,

The problem is with the screen, at the very end, I have to use vesa, instead of via or unichrome..it is a pity. If anyone, could help about this matter.

The rest, goes..

*********************touchscreen***********************************


Download evtouch from  [http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html#](http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html#) 

tar -xzf evtouch-0.8.7.tar.gz

sudo cp evtouch-0.8.7/evtouch_drv.so /usr/lib/xorg/modules/input/ 

Add in  /etc/X11/xorg.conf

Section "InputDevice"
Identifier "Touchscreen"
Driver "evtouch"
Option "Device" "/dev/input/touchscreen"
Option "DeviceName" "touchscreen"
Option "MinX"    "57"
Option "MinY"    "1979"
Option "MaxX"    "1990"
Option "MaxY"    "90"
Option "SwapY"   "1"
Option "ReportingMode" "Raw"
Option "SendCoreEvents"
EndSection 

and in Section "ServerLayout"

InputDevice "touchscreen" "CorePointer"

then , sudo vim /etc/udev/rules.d/10-local.rules
and write

SUBSYSTEM=="input", KERNEL=="event*", ATTRS{name}=="Touchkit HID-USB Touchscreen", SYMLINK+="input/touchscreen"

then,

sudo gedit /etc/modprobe.d/blacklist

# TouchScreen evtouch 
blacklist usbtouchscreen 

*********************************  *WIFI* ************************************************


[http://www.datanorth.net/%7Ecuervo/rtl8187b/](http://www.datanorth.net/%7Ecuervo/rtl8187b/)


tar xvfz rtl8187b-modified-dist.tar.gz
cd rtl8187b-modified
./makedrv
sudo ./install
sudo depmod -a

check /etc/network/interfaces 

auto lo
iface lo inet loopback

and then

sudo gedit /etc/init.d/wlan_det

write:

#!/bin/bash

cd /home/whenever you install your rtldriver/rtl18187b-modified

./wlan0up

exit

then,
chmod +x (sudo chmod +x /etc/init.d/wlan_det)

and,

sudo update-rc.d wlan_det defaults


************************************** SOUND******************************

rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-driver alsa

rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-kernel alsa


cd alsa
cd alsa-driver
./hgcompile
make
make install


reboot

******************************* CAMERA**********************************

Go well

I installed cheese and it is fantastic!!


hope, this helps..

regards.

---

### Post by sarelgrin on 2008-05-04
Thanx,l3th0x

Now I can finally use linux on my u60.

Windows SUCKS!!!!

---

### Post by sarelgrin on 2008-05-28
For all those interested: Gigabyte has released linux drivers and bios of it's gigabyte u60 (including: vga drivers, touch screen drivers and control application, alsa drivers and wifi drivers).


The compressed packages include instructions to the installation process.

It is very important to upgrade to the new bios (designated bios for linux).

Drivers and bios can be found on Gigabyte's site [HERE]("http://www.gigabyte.com.tw/Support/Notebook/Driver_Model.aspx?ProductID=2506")

---

