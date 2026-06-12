---
title: "Installation ubuntu 6.10"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by gopalb123 on 2007-01-02
Hi. I just installed Ubuntu onto my PC (alongside XP) and now when I turn my PC on I have a problem.

its bring unreadable screen, i have ATI card...i cant read any thing and i do not go further..
i'm new in linux...i dont konw how to fix this problem...can any body help me..

---

### Post by cotcot on 2007-01-02
Then I guess you can login in terminal (it is the rescue mode; normally the option 1 or 2 lines lower in the grub selection menu).
From there do : ```
sudo dpkg-reconfigure xserver-xorg
```
This will allow you to select hardware components in order to make a new configuration file for the graphical server. Please read about this first. 
Here is a usefull link [http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by gopalb123 on 2007-01-02
Hi,

No i login normal mode not in rescue mode...after installation of ubuntu alternet 6.10 it boot normal...then i put user name "OEM" and password..but it will apear in low color depth and cant read in screen..i try it several time..but result is same...

i just know how to spell LINUX....Please help me....


thanx

---

### Post by gopalb123 on 2007-01-03
Hi cotcot

i go through the your instruction....but i 'm not sucsses.....when i type "sudo dpkg-reconfigure xserver-xorg" and press enter, the msg. show your XSERVER is fatal error...please reboot...should i reinstall ubuntu? or, any other alternative has.....?

regards
gopal

---

