---
title: "Getting a blank screen after install with Intel GM HG chip"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by mmattax on 2010-07-30
I have attempted to install Ubuntu 10.04 on a new DELL Latitude E5510 to no avail. I get a blank screen throughout the Live CD. I tried the alternate install CD, the install goes smoothly but when I boot up I get a blank screen for Grub and the OS. 

I can hear the startup sound so I know Ubuntu is booted. I then try CTRL + ALT + F1 to get into a console, but have not been able to do so. 

The laptop has a Intel i5 core processor and has an Intel GMA HD graphics chip.

I assume that my graphics chip is not supported out of the box, how can I get Ubuntu up and running? I have also tried Fedora and openSUSE and get the same display problems.

---

### Post by Revolutionary101 on 2010-07-31
Sorry to be the bearer of bad news but...

It looks like the i series processors with graphics on the CPU (aka codename Arrandale) seem to be having problems with Ubuntu 10.04 and other Linux distros. This link will show you that you are not alone:

[http://ubuntuforums.org/showthread.php?t=1523067](http://ubuntuforums.org/showthread.php?t=1523067)

This is, what seems to be, a Linux kernel issue. These means that the Ubuntu team has no way to change it until the Linux kernel is updated and supports the graphics on these processors.

---

### Post by Fiery Spirited on 2010-08-18
I have a newly  purchased Dell Latitude E5510 with an i5 and did a clean install on it with 10.04. I  did not encounter any problem with the graphics. The kernel I am using  is 2.6.32-24-generic. 

Could it perhaps be some BIOS setting that is preventing your system from functioning properly?

---

### Post by sparcz on 2010-09-03
I got an E5510 yesterday (Sept 2010)and created an installation cd from the latest download from Ubuntu. Can't make it work at all! I have tried every possible combination of options, the screen goes black sooner or later and then I am stuck. Can't even enter a shell to examine what's wrong !!!

---

### Post by onetanzania on 2010-11-12
same to me i have installed the new 10.10 ubuntu notebook remix in my laptop dell latitude e5510 i have two problem first  **failed to get i915 symbols, graphics turbo disabled error on boot **then the screen goes black but i can here welcome sound. 
Any ideas how to solve this issue:confused:
thanks

---

