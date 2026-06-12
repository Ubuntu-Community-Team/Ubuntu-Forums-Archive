---
title: "how to Get the 60Hz Refresh Rate with intel 915gav mb"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by kamrananvaar on 2008-01-01
hi
my monitor only support a 60Hz refresh rate- it works fine in win xp but as soon as i try to install linux- ubuntu,pclinuxos, mint it blanks out sometimes i get to the live session ,whereas sometimes halfway through the installation the monitor flickers and goes into standby mode .I have tried safe mode in pclinuxos2007 but same thing happens , how do i limit it to a refresh rate of 60hz and resolution of 1024x768
thanks

---

### Post by logos34 on 2008-01-01
- try safe mode in ubuntu
OR
- load desktop and got to system>prefs>screen res.>set refresh

OR
- open a terminal on the desktop (if you can) and type:

sudo dpkg-reconfigure xserver-xorg

choose 'vesa' video driver.  You can accept defaults for most of the rest.  Toward the end there is a display setting section--enter your monitor's vert. refresh rate.

OR 

get the text-mode alternate install cd

---

### Post by kamrananvaar on 2008-01-01
i have tried safe mode does,nt work
also i would like to try it out on live cd b4 installing
is,nt there anything i can do b4 live session kicks in

---

### Post by logos34 on 2008-01-01
try F6 and enter vga= boot option
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I think there's a way to add refresh to that, like you do with modeline...looking into it

---

