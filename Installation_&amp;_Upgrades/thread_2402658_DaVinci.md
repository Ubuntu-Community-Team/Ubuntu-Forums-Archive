---
title: "DaVinci"
date: 2018-10-03
forum: Installation &amp; Upgrades
---

### Post by eljonathan34 on 2018-10-03
I have Ubuntu 18.04 lts and try install DaVinci Resolve 15.1. I'm sure that did all steps, but the program not run.

---

### Post by jessieinnewy51 on 2018-10-03
[LEFT]I have had a similar problem and it was resolved with the Information provided BELOW.
 In my case I had the Problem with UBUNTU Version 18.04 after an upgrade from Version 17.10 and then I tried a complete New Installation of 18.04 which would not boot through to the Login Screen.
 In my Case it happened on a Desktop With the Graphics Card INTEL G33 in conjunction with Intel Dual Core, CPU E 5400,2.7Ghz,Motherboard Elite Group G31T-M

 
Easiest fix for me:

[LEFT]When you get to the Main Selection Menu on the screen follow the instructions below, (It appears that their is a Problem With Intel Graphics cards in conjunction with Gnome3, refer to previous Forum Discussion for Advanced information)
[/LEFT]
In Grub, choose "Advanced options for Ubuntu", then boot the latest "Recovery Mode" kernel. (4.15.0.29)
At the Recovery Mode menu, choose Resume. Ubuntu should boot more or less normally.
Log in.
Open a terminal window with Ctrl-Alt-T.
Enter the following: "sudo pico /etc/gdm3/custom.conf" 
 (Then Scroll Down, Down Arrow Key)
Uncomment (remove the hash symbol) from the line "#WaylandEnable=false" (Delete #)
Save your changes and exit pico. (CTRL "X")

Reboot.

If you want to re arrange the GRUB their is an Excellent GRUB Customizer within LINUX VOYAGER 18.04 that works well once you become familiar with it and remember to Save to the Master Boot Record.
GRUB Customizer can be Downloaded and Installed to UBUNTU 18.04 once you get it running.
Linux Mint 19 Xfce is extremely Slow nearly 10minutes to get to the Login Page on my Desktop but it looks like it Mint 19 has a Programming problem also.

Hopefully UBUNTU 18.10 will correct a few of these newly created software problems.
I nearly gave up on UBUNTU 18.04 and stuck to VOYAGER 18.04 but now I am Dual Booting with VOYAGER 18.04, MINT 19, UBUNTU 18.04
all are now working well.
[/LEFT]

---

