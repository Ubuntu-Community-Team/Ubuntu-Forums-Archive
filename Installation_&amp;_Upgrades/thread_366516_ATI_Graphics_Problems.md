---
title: "ATI Graphics Problems"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by Poisond on 2007-02-20
[FONT="Georgia"]Hi guys,

I just installed Ubuntu and am having problems changing my resolution.

I have an ATI X800 card and a Dell 2407WFP.

I ran the "sudo dpkg-reconfigure xserver-xorg" command that seems to work for some people but it isn't working for me.

I tried running also "sudo aticonfig" but it says command not found.

I also downloaded a driver file from ati's website but when I double click it, it says "could not open, archive not supported". Its an rpm file "fglrx_6_8_0-8.33.6-1.i386.rpm"

When I tried sudo dpkg-reconfigure xserver-xorg I chose simple mode, it detected my card and monitor because it know the model names of both of them. I set it to 1900 x 1200 (monitor native resolution) but to no avail. On the resolution screen under the System tab I cannot change 640 x 480 to anything else.

Please I am open to any suggestions, currently I am running at "640 x 480 and the Refresh rate is -17133(weird). 

Thanks.



[/FONT]

---

### Post by erkki70 on 2007-02-21
> **Poisond said:**
> [FONT=Georgia]Hi guys,
I just installed Ubuntu and am having problems changing my resolution.
I have an ATI X800 card and a Dell 2407WFP.
I ran the "sudo dpkg-reconfigure xserver-xorg" command that seems to work for some people but it isn't working for me.[/FONT][FONT=Georgia]
When I tried sudo dpkg-reconfigure xserver-xorg I chose simple mode, it detected my card and monitor because it know the model names of both of them. I set it to 1900 x 1200 (monitor native resolution) but to no avail. On the resolution screen under the System tab I cannot change 640 x 480 to anything else.
Please I am open to any suggestions, currently I am running at "640 x 480 and the Refresh rate is -17133(weird). 
Thanks.
[/FONT]
hi,
read this post for instructions:
[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

> 
[FONT=Georgia]I also downloaded a driver file from ati's website but when I double click it, it says "could not open, archive not supported". Its an rpm file "fglrx_6_8_0-8.33.6-1.i386.rpm"[/FONT]
To convert .rpm use alien:
[http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien)

> [FONT=Georgia]I tried running also "sudo aticonfig" but it says command not found.[/FONT]
You probably need to install this package first...

Good luck :-)

---

### Post by Apoorv on 2007-02-21
If you have the ATI Radeon Xpress 200, the just type the following, one by one, in the terminal.

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


Then, after this  type 

sudo gedit /etc/X11/xorg.conf

In this, change

```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Xpress 200 (RC410)"
Driver "ati"
BusID "PCI:1:5:0"
EndSection
```

to


```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Xpress 200 (RC410)"
Driver "fglrx"
BusID "PCI:1:5:0"
EndSection
```

And reboot. Problem solved.

---

### Post by Poisond on 2007-02-21
Thanks for finding that thread for me errki70, worked perfectly!

---

### Post by faeloh on 2007-02-24
I tried the series of commands that was put down, and when i typed "sudo apt-get install xorg-driver-fglrx", it gives back "E: Invalid operation xorg-driver-fglrx"

---

### Post by Poisond on 2007-02-24
HI Faeloh,

Not sure why it didn't work for you as I am totally new to this also.

I had also used this link and it worked for me: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Even though it says nvidia scripts1 in the url it will still work for ATI cards.

Scroll down to the Instructions section and start.

Let us know if you have any luck.

---

