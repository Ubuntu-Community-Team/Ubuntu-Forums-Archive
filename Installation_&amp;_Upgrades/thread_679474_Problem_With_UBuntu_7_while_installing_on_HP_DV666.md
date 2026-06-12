---
title: "Problem With UBuntu 7 while installing on HP DV6662"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by abuamit on 2008-01-27
Hi,

 I have HP laptop Model No : DV6662SE 

Vista and xp already installed and dual boot is being managed by vista pro.

I tried to install ubuntu-7.10-desktop-i386 but i am not able to install it.

As soon as the live version is loaded fiest error i get is 

"The panel encountered a problem while loading "**OAFIID:Deskbar_Applet**" do you want to delete applet from your configuration"

I clicked on dont delete button. then i tried to run install but i get an error saying 

"**There was an error launching the application with details : failed to execute child process ubquity(Input/Output error )**" 


Please help me in resolving this issue.

My laptop config:
 Model No : DV6662se
 Intel core 2 duo
 2 GB Ram
 1.5 GHz
HD SATA Interface

Amit

---

### Post by jeffus_il on 2008-01-27
It's not a good sign that the livecd has problems. There are other ways to install, using the alternate cd or from windows using wubi [http://wubi-installer.org/](http://wubi-installer.org/)
You should first find out what is causing the livecd problem, since you hardware should not present a problem.

Could you open a terminal and run ```
dmesg
``` and post the output?

---

