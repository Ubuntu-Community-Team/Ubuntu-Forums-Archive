---
title: "Hardy 8.04 upgrade causes Nvidia trouble"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by toekneevee on 2008-05-23
Upgraded to Hardy 8.04 from Gutsy 7.10 (which ran great). After enabling the restricted Nvidia driver and rebooting, Ubuntu runs in low graphics mode. I am unable to find current driver or resolution greater than 800 x 600 through the configuration screens.  I was using the Nvidia driver with 7.10.  

Dell Inspiron 531, Athlon 64 X2, 4 GB RAM, Nvidia GeForce 8300 GS

Any assistance would be greatly appreciated. 

Thanks.

---

### Post by tamoneya on 2008-05-23
have you tried using envy to install the drivers?

---

### Post by toekneevee on 2008-05-23
Yes.  Same trouble.

---

### Post by RATM_Owns on 2008-05-23
Did you try
```
sudo aptitude install nvidia-glx-new
```
?

---

### Post by toekneevee on 2008-05-23
No success.  When I go to NVIDIA x server settings it says I do not appear to be using the NVIDIA x driver and to  run nvidia-xconfig as root.  When I do that, I get the following...

tony@tony-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first CorePointer in the config input list.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.

tony@tony-desktop:~$ 

Any other suggestions?  Thanks for the help.

---

### Post by RATM_Owns on 2008-05-23
SOLUTION:
```
sudo nvidia-xconfig
```

EDIT: But I read somewhere that graphical apps should be run using gksudo so...
```
gksudo nvidia-xconfig
```

---

