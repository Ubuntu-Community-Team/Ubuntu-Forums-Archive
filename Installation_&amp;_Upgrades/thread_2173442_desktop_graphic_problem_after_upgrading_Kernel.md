---
title: "desktop graphic problem after upgrading Kernel"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by MrAli on 2013-09-09
i am using ubuntu 12.04.3 64bit. i knew in updating from 12.04.2 to 12.04.3, the kernel does not upgrade, so i decided to upgrade kernel using following commands:
```
sudo apt-get install --install-recommends xserver-xorg-lts-raring
sudo dpkg-reconfigure xserver-xorg-lts-raring
```
know, my desktop faced with some graphical problems as you can see in following screenshots:

[[IMG]http://upit.cc/t/a66e605d.png[/IMG]](http://upit.cc/i/a66e605d.png)

[[IMG]http://upit.cc/t/41d1fdff.png[/IMG]]("http://upit.cc/i/41d1fdff.png")

[[IMG]http://upit.cc/t/20c6d48d.png[/IMG]]("http://upit.cc/i/20c6d48d.png")

i ran glxgears test and saw the average FPS decreased from about 370 to about 120 but amasingly the desktop responsiveness and speed has been improved. 

do you know what is the problem and how can i solve that?
My laptop graphic card is NVIDIA Geforce 8400m GS, CPU: Intel Core2due.

---

### Post by MrAli on 2013-09-10
i want to add that this problem most of tim shows utself in web browsers such as firefox and chrome.
in desktop environment, most of time i do not have any problem but sometimes name of files and window titles become corrupt that shows the problem only affect fonts in the desktop itself. 
please guide me to solve the problem.

---

### Post by deadflowr on 2013-09-10
Is that the full command you ran to upgrade to the lts-raring stack?
If so, it seems to be missing a few things.
The command should be
```
[COLOR=#333333][FONT=monospace]sudo apt-get install --install-recommends linux-generic-lts-raring xserver-xorg-lts-raring libgl1-mesa-glx-lts-raring[/FONT][/COLOR]
```

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by MrAli on 2013-09-11
i ran your suggested command right now and nothing new installed. 
```

sudo apt-get install --install-recommends linux-generic-lts-raring xserver-xorg-lts-raring libgl1-mesa-glx-lts-raring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic-lts-raring is already the newest version.
linux-generic-lts-raring set to manually installed.
libgl1-mesa-glx-lts-raring is already the newest version.
libgl1-mesa-glx-lts-raring set to manually installed.
xserver-xorg-lts-raring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by deadflowr on 2013-09-11
Are you using the out of the box/default installed graphics drivers(nouveau), or did you install the nvidia drivers?

---

### Post by MrAli on 2013-09-11
i am using nouveau.

---

### Post by Mephisto Pheles on 2013-09-12
nouveau killed my 12.04.3 upgrade on xubuntu, I kept getting kernel panic crashes after the update. 
Didn't have a clue so I researched some, should be a hardware problem, only ... my Linux Mint runs perfectly,
the only difference was that Mint used the nvidia drivers and xubuntu didn't use proprietary drivers.

 Even the ubuntu 12.04.3 fresh install DVD crashes with kernel panics. No way for me to even install it.

 After installing latest nvidia drivers, xubuntu is running smooth again and has been for several days in a row.

I'll pass on installing ubuntu regular, probably too heavy for my old box anyway.

---

