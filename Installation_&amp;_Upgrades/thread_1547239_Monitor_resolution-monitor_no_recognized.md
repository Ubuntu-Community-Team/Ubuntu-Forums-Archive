---
title: "Monitor resolution-monitor no recognized"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by Stroman on 2010-08-06
I have 3 Ubuntu 10.04 installs running on 3 separate computers.  All were updated from the 9.03 (i think thats right description) version. Two of them work fine.  One version does not recognize the monitor (tried 2 different monitors) and has the resolution set to 856 x 600 maximum (I am not on one of them so that might not be exactly right resolution). What do i do to get the right drivers to run at higher resolution.  The problem is that the picture is too big for the viewing area.  I'm new to Ubuntu and obviously limited in knowledge, but am enjoying learning the system.  I also have the problem someone else posted where I installed Ubuntu in a computer with Windows XP already installed.  Ubuntu works fine, and Windows shows up in the boot menu, but when i try to boot to windows, i get the black screen with a flashing cursor.  Any help anyone can offer this old duffer will be greatly appreciated.
Stroman

---

### Post by TimEnid on 2010-08-06
how are the monitors connected? dvi? hdmi?

---

### Post by Stroman on 2010-08-06
> **Stroman said:**
> I have 3 Ubuntu 10.04 installs running on 3 separate computers.  All were updated from the 9.03 (i think thats right description) version. Two of them work fine.  One version does not recognize the monitor (tried 2 different monitors) and has the resolution set to 856 x 600 maximum (I am not on one of them so that might not be exactly right resolution). What do i do to get the right drivers to run at higher resolution.  The problem is that the picture is too big for the viewing area.  I'm new to Ubuntu and obviously limited in knowledge, but am enjoying learning the system.  I also have the problem someone else posted where I installed Ubuntu in a computer with Windows XP already installed.  Ubuntu works fine, and Windows shows up in the boot menu, but when i try to boot to windows, i get the black screen with a flashing cursor.  Any help anyone can offer this old duffer will be greatly appreciated.
Stroman
**Help!!**

---

### Post by Stroman on 2010-08-06
> **TimEnid said:**
> how are the monitors connected? dvi? hdmi?
 All DVI

---

### Post by TimEnid on 2010-08-06
> **Stroman said:**
> All DVI

type this in a terminal to bring up the ATI CCC
DISPLAY=:0 amdcccle

go into the the display setting and use the slider to adjust the size of the screen.

---

### Post by Stroman on 2010-08-06
Thank You,  I will try this when i get home.
Stroman

---

### Post by Stroman on 2010-08-06
Tried going into  terminal and typing Display=:0 amdcccle    got no results.   Need monitor settings of at least 1024 x 768 pixels.  Cannot get higher than 856 x 600 which makes picture too big for screen.  The monitor we are using is an Acer 22 in LCD.  I had the same trouble with a 14 in HP.

---

### Post by TimEnid on 2010-08-06
> **Stroman said:**
> Tried going into  terminal and typing Display=:0 amdcccle    got no results.   Need monitor settings of at least 1024 x 768 pixels.  Cannot get higher than 856 x 600 which makes picture too big for screen.  The monitor we are using is an Acer 22 in LCD.  I had the same trouble with a 14 in HP.

did the ATI CCC pop up when you typed that in?

---

### Post by Stroman on 2010-08-06
No,  it just dropped down a line and gave me a solid curser

---

### Post by cavalier911 on 2010-08-06
Follow my post here to generate an xorg.conf
to edit to force xserver to display 1024x768.
[http://ubuntuforums.org/showthread.php?t=1544285](http://ubuntuforums.org/showthread.php?t=1544285)

---

### Post by TimEnid on 2010-08-06
> **Stroman said:**
> No,  it just dropped down a line and gave me a solid curser

i just did it and got the Catalayst Control Center.
DISPLAY=:0 amdcccle

---

