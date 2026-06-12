---
title: "Install Hangs"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by rurapenty on 2005-04-15
I am new to linux and installing Ubuntu for the first time.  I get throught the first part to the install and eject the cd.  My machine reboots and bigins installing Ubuntu.  During this part of the installation my screen goes blank and a "-" appears in the upper left corner of my screen.  The keyboard will not respond and the only way out is a hard reboot.  When I reboot it will begin loading Ubuntu and lock up with the "-" again.  I have tried to hit "ESC" when Grub is loading and been able to start the machine in "Recovery" mode with a prompt.  I found another post which, with similar "-", and tried to do the following:

dpkg-reconfigure xserver-xorg

It returned xserver-xorg not installed

i also tried to edit the xorg.conf file using
nano /etc/X11/xorg.conf

It opened a new file rather than the conf file.  

There are 2 things i can think odf that might be a problem, i have a usb keyboard and I am no using the oboard i810 drivers video.  i am going to try a ps2 keyboard tonight and then try with the onboard video.  
 ](*,)  ](*,) 
What am I doing wrong?  How do I get to where I can install and boot correctly?

I have used the same install cd on another machine and it work perfectly, so i know its not that.  

Machine specs:
P3  900
256 mb ram
radeon 7000

---

### Post by heimo on 2005-04-15
Couple things that I'd try. You probably don't have everything installed correctly, so this may help:
 
```

sudo apt-get install ubuntu-desktop

``` 
If that goes smoothly, you could try *startx *to see if Xorg starts. If not, try reconfiguring xserver-xorg.
 
You can get helpful information from logs in /var/log/

---

