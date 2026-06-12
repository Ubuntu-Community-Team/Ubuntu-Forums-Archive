---
title: "start X Server"
date: 2004-11-05
forum: Installation &amp; Upgrades
---

### Post by Jos Walrave on 2004-11-05
Installed Ubuntu 4.10  successfully on my desktop and I was really satisfied with the result as well as the installation process.

So, very enthousiastic I also installed Ubuntu 4.10 (dual boot with winXP) on my laptop. Everything went well, except for starting the X Server. This laptop contains an Intel 82852/82855 GM/GME Graphics Controller. I also reconfigured [FONT=Courier New]/etc/X11/XF86Config-4[/FONT] to default to 16 bits and 1024x768. Also followed all the steps as described at the head of this file to apply these changes.

On other Linux distros I used [FONT=Courier New]Xconfigurator[/FONT] for configuration and [FONT=Courier New]startx [/FONT]to start the X server. What is the equivalent on Ubuntu?

I already used [FONT=Courier New]dpkg-reconfigure[/FONT] for xfree86, I also checked whether or not all xserver packages were installed ([FONT=Courier New]apt-get update,  apt-get install xserver-xfree86, xserver-common and xfonts-base[/FONT]).

Can anybody tell me what the equivalent for startx on Ubuntu is and whether or not I should reconfigure [FONT=Courier New]XF86Config-4[/FONT]?  

Any Ubuntu guru here who can help me with my introduction to this distro?

Many thanks in advance!

---

### Post by diebels on 2004-11-05
You have ```
Driver      "i810"
```in /etc/X11/XF86Config-4?
"gdm" starts X in ubuntu. See /var/log/XFree86.0.log for error messages

---

### Post by az on 2004-11-05
You installed everything or did a custom install?

sudo dpkg-reconfigure xserver-xfree86 
to configure X.

startx should work if you have x installed.  Gdm will start x, too, but it is a display manager, it manages your different window managers if you have several...

---

### Post by Jos Walrave on 2004-11-07
I didn't use gdm to start X. Will try this. 

I've applied all the other suggestions already. I will first try gdm and get back to you when I've the time for it  :cry:

---

### Post by Jos Walrave on 2004-11-08
I typed [FONT=Courier New]$ which gdm[/FONT] and [FONT=Courier New]$ apt-get install gdm[/FONT] and found out that gdm wasn't installed yet. I installed it, with [FONT=Courier New]$ apt-get install gdm[/FONT] and everything worked well. Seems that my configuration changes were OK. 

Still I wanted to know why the installation wasn't as smooth as on my desktop at home. So I installed Ubuntu again, but this time at home and everything went well. I only had to reconfigure the keyboard settings to [FONT=Courier New]us_intl[/FONT] en [FONT=Courier New]pc101 [/FONT]instead of the generic us and pc104. I already supplied the values in the installation phase, but they were not applied correctly. So now, I can e.g. also type " and e sequentially to create ë.

I am very pleased with Ubuntu, both on my desktop as on my laptop. The only error/ warning I get at boot time is about modprobe. I will post the specifics about this if I can't find a solution myself.

I think the moderator can close this thread  =D>

---

