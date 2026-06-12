---
title: "can't install ubuntu, x server fails"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by spadge on 2006-08-27
this is my first time with linux, and I thought ubuntu would be the right distro to make the jump to. however, I am having some problems.

when I load the live cd, I press start ubuntu, and it will load. After it has loaded, a box come up saying 'x server failed'.

I am using a fairly able system(P4 3.2ghz, 512mb ram).
any help would be greatly appreciated.

---

### Post by kaamos on 2006-08-27
Hello!

The error is apparently caused by the live cd not recognising your graphics card/monitor correctly.

Steps to take once the error has occured.
1) just hit ok for the errors. This should get you a text login. If not, press ctrl+alt+F1
2) use the text editor "nano" to change your graphics settings in the file called "xorg.conf" with the command
```
sudo nano /etc/X11/xorg.conf
```
In the file there is a section "Device"
> 
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
        Driver          "**XXXXX**"
EndSection


Where XXXX is the name of the driver. For example, if you are using nvidia , it is "nv". Change the driver to "**vesa**". Press control+x to exit and save the file when prompted.
3) restart the graphics system with the command
```
sudo /etc/init.d/gdm restart
```

Note that once the system is installed you can then install the correct drivers for your card to get 3d acceleration/corrent resolution and such.

---

