---
title: "Help with patch"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by ntaforge on 2008-08-25
I need help patching a file

noah@ubuntu8laptop:~/wifi/rtl8187b-modified$ patch -pl < /home/noah/wifi/rtl8187b-modified/2.6.24.patch
The program 'patch' is currently not installed.  You can install it by typing:
sudo apt-get install patch
bash: patch: command not found
noah@ubuntu8laptop:~/wifi/rtl8187b-modified$ 

and then when I try apt-get install

noah@ubuntu8laptop:~/wifi/rtl8187b-modified$ sudo apt-get install patch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package patch

What do i do!

---

### Post by raul_ on 2008-08-25
Try sudo apt-get install patchutils

---

### Post by ntaforge on 2008-08-25
noah@ubuntu8laptop:~/wifi/rtl8187b-modified$ sudo apt-get install patchutils
[sudo] password for noah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package patchutils

Sorry

---

### Post by raul_ on 2008-08-25
How long ago have you installed Ubuntu? Have you enabled extra repositories?

According to packages.ubuntu.com, the package's name is "patch" so you should be able to install it

---

### Post by ntaforge on 2008-08-25
I just installed it and I'm new to linux

how do you enable that?

---

### Post by raul_ on 2008-08-25
check that you have all repositories enabled in System > Administration > Software sources.

---

### Post by ntaforge on 2008-08-25
GOT IT! Thanks RAUL!

---

### Post by raul_ on 2008-08-25
Cool :popcorn:

---

### Post by sreagvle on 2008-10-22
Hey,

When I type sudo apt-get install patch I get:

[I]Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter[/I]

I don't have the CD handy. Anyone know why it wants the CD? Can I not download patch? The same thing happens when I try to install using Synaptic Package Manager.

---

### Post by Cousteau80 on 2008-10-22
> **sreagvle said:**
> Hey,

When I type sudo apt-get install patch I get:

[I]Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter[/I]

I don't have the CD handy. Anyone know why it wants the CD? Can I not download patch? The same thing happens when I try to install using Synaptic Package Manager.

Try disabling the cd in the software sources list. System > Admin. > Software Sources. I think it's under Third-party...

---

### Post by sreagvle on 2008-10-23
The cd isn't in the list of Third party software sources. I can find the patch program in the synaptic package manager, it's only when I try to install it that I'm asked for the cd.

I've installed the latest version of patch under my home directory so it's not a problem any more, but I wonder why it wants the cd?

---

