---
title: "after install and reboot screen resolution huge"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by bhintz on 2006-09-20
I am able to install to hard drive with no problem, but after the reboot my screen resolution is 640x480 and I cannot change it.  I have reinstalled twice and tried to deal with this in both Ubuntu, Kubuntu and xbuntu.  None of them will let me change it to a normal 1024 x 768.  I can specify the resolution when booting from the dvd and it work fine.  I am also unable to get kppp to work in any format and must use the "networking" program which only connects on external modem. This is an irritation, but the screen resolution makes the install unuseable.  

Any suggestions would be appreciated.  

Bob

---

### Post by dlehman on 2006-09-21
Go to System>Preferences>Screen Resolution and select the resolution you want and make it your default.  if you do not have the 1024 option you will have to edit your xorg.conf file 
```
sudo gedt /etc/X11/xorg.conf 
```
scroll down to the screen section and make sure that 1024x768 is on the mode line for your color depth 

hope this helps

---

### Post by bhintz on 2006-09-21
Hi, 

I have tried your command and get message

sudo: gedt: command not found

I tried some variations and still didn't get anything.  I have booted up the kubuntu version of dapper and am OK at the moment.  Yesterday, I couldn't get any useable at all.

---

### Post by bikeman123 on 2006-09-21
Yeah same problem here. Gedit is definitely on my pc so I don't understand.
PLease advise.

---

### Post by Japa on 2006-09-21
> **dlehman said:**
> 
```
sudo gedt /etc/X11/xorg.conf 
```

sudo gedit /etc/X11/xorg.conf it's gedit not gedt and make sure you use X not x

---

### Post by Omnios on 2006-09-21
Hi: You can try using 
press ctrl-alt-F1 to jump into command line and log in and enter
```

sudo dpkg-reconfigure xserver-xorg

```

 This is a turtle like graphics xorg-config. This will take you through set up mice and keyboard and use auto detect for this. There will be a monitor section with different resolutions that you can tick off to get them.

---

### Post by dlehman on 2006-09-21
I apologize for the confusion my typos caused it is gedit the default gnome editor, hope you get things working.

---

