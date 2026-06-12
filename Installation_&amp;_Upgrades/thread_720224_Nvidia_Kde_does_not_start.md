---
title: "Nvidia Kde does not start"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by gos1 on 2008-03-10
Hi 
 
    i have a lap top with Nvidia GeForce Go 6100 graphics card And a 64 bit Amd 3500+ CPU. And When I try to install the latest Nvidia Drivers from the Adept-Installer The KDE does not start again giving errors about resolutions .

---

### Post by gos1 on 2008-03-10
Here is the error : 
 
     usplash : setting mode 1280x1024 failed
     usplash : setting mode 1152x864 failed 
     usplash : setting mode 1024x768 failed
 
  kinit : name_to_dev_t (/dev/disk/by-uuid/sda5(8,5))
  kinit : trying to resume from /dev/disk/by-uuid/some code here
  kinit : no resume image , doing normal boot 
 
  ubuntu 7.10 acd-laptop tty1
 
    acd-laptop login 
 
  Can anyone help me on this I ma using a Kubuntu 7.10 and used envy before to reinstall the drivers .

---

### Post by PmDematagoda on 2008-03-10
Boot Ubuntu in Recovery Mode, run:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then see if the GUI now works by running:-
```
startx
```

---

