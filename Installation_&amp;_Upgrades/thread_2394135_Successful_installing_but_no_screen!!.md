---
title: "Successful installing but no screen!!"
date: 2018-06-13
forum: Installation &amp; Upgrades
---

### Post by mbzadegan on 2018-06-13
Hi everybody,
I have **Lenovo-miix-310**. I booted ubuntu(**18.04-desktop-amd64**) live and when grub opened I switch to install OS in my tablet. It boot OK and enter to ubuntu without error and run installing procedure automatically without any error. It finished installing successfully but when I rebooted, I have no screen in my display at all!! How can I resolve my issue? :confused:

---

### Post by mbzadegan on 2018-06-13
Finally I findout my issue! when I push the power button (double push) it show my desktop in the portrait mode and not landscape (because my device is tablet).
I run terminal and run this command to rotate screen in 90[COLOR=#545454][FONT=arial]° [/FONT][/COLOR][COLOR=#000000][FONT=arial]clockwise:

**[FONT=courier new]xrandr -o right[/FONT]**

and it show my desktop OK![/FONT][/COLOR]:cool:
How can I run this command automatically on every login?

---

### Post by mbzadegan on 2018-06-13
Does anybody know How can I boot ubuntu in landscape display mode?

---

### Post by ubfan1 on 2018-06-13
The xorg man page [https://www.x.org/archive/X11R7.5/doc/man/man5/xorg.conf.5.html](https://www.x.org/archive/X11R7.5/doc/man/man5/xorg.conf.5.html)  says:
In the monitor section of sorg.conf

**Option ***"Rotate"  ***"rotation"** This optional entry specifies the initial rotation of the given monitor. Valid values for rotation are "normal", "left", "right", and "inverted". (RandR 1.2-supporting drivers only)

---

### Post by mbzadegan on 2018-06-14
> **ubfan1 said:**
> The xorg man page [https://www.x.org/archive/X11R7.5/doc/man/man5/xorg.conf.5.html](https://www.x.org/archive/X11R7.5/doc/man/man5/xorg.conf.5.html) says:
In the monitor section of sorg.conf

**Option ***"Rotate" ***"rotation"** This optional entry specifies the initial rotation of the given monitor. Valid values for rotation are "normal", "left", "right", and "inverted". (RandR 1.2-supporting drivers only)

I can not find any **[FONT=&quot]xorg.conf[/FONT]** by the [FONT=&quot]**#find / -iname xorg.conf**[/FONT] command! Why?

---

### Post by ubfan1 on 2018-06-14
Look at the answer [https://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file](https://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file)
Basically, stop the X server, then generate an xorg.conf with sudo X -configure in your current directory.  Then you edit it.
Unless it's needed, the xorg.conf is not even generated these days, most things default correctly.

---

### Post by mbzadegan on 2018-06-14
> **ubfan1 said:**
> Look at the answer [https://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file](https://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file)
Basically, stop the X server, then generate an xorg.conf with sudo X -configure in your current directory.  Then you edit it.
Unless it's needed, the xorg.conf is not even generated these days, most things default correctly.

I inserted **3** to end of kernel line of **grub.cfg** to active run level 3 for booting without X. I run** X -configure** but error multilines and did not create any **xorg.conf**
How can I create **xorg.conf** without booting in runlevel 3?

---

### Post by mbzadegan on 2018-06-14
I hold down **alt + ctrl + F3** and enter to command line mode but when I run **sudo** **service xorg stop **it error me that did not load xorg! How can I stop X?

---

### Post by mbzadegan on 2018-06-17
> **mbzadegan said:**
> I hold down **alt + ctrl + F3** and enter to command line mode but when I run **sudo** **service xorg stop **it error me that did not load xorg! How can I stop X?

Isn't any idea for stop the **X **service?

---

### Post by ubfan1 on 2018-06-17
Find which services are running
sudo service --status-all
locate the display manger, probably either lightdm or gdm and stop it.
X itself if not a "service", but you also may kill the X server -- locate it with 
ps auxww
and locate the /usr/lib/xorg/Xorg line(s) and use the kill command on the pids 
sudo kill xxxx
or
sudo kill -9 xxxx  
if the first one doesn't work.

---

### Post by mbzadegan on 2018-06-18
I found only gdm3 process but when I kill it my system was hanged and blinking among desktop and commandline mode!!
BTW, I use unity desktop and not use LXDE or GNOME.
Isn't any other way?

---

### Post by ubfan1 on 2018-06-18
You should be at a virtual terminal when you do kill the X server, and your screen should not be affected in any way.  Choose a virtual term with the function keys ctrl + alt + F3  (1, 2, or 7 may be in use, so avoid them).

---

### Post by mbzadegan on 2018-06-18
> **ubfan1 said:**
> You should be at a virtual terminal when you do kill the X server, and your screen should not be affected in any way.  Choose a virtual term with the function keys ctrl + alt + F3  (1, 2, or 7 may be in use, so avoid them).

Dear ubfan1, I tried to run console on TTY3 and I stop the gdm service that runs by root and this time my screen did not blinking and I seccess to kill this process only for 10 seconds! it started again by other process number. I think that the method of gdm process killing is not a good way to generate **xorg.conf. **&#8203;Have you other hints?

---

