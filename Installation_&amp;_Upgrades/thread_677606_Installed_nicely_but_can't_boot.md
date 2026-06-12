---
title: "Installed nicely but can't boot"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by mahmud_simon on 2008-01-25
Hi I am a new ubuntu user and this is my 1st post. 
My problem is: **I installed system nicely from ubuntu 7.10 live CD. But when system restarts finishing installation, boot agent loads normaly and then the screen goes blank (Monitor light blinks) after showing msg "Starting....".  **
So whats the problem? Pls help.:confused:

My PC Configuration is as follows: 

**Processor:** Intel Pentium D 805 (2.66 GHz)
**Mainboard Model:** Intel D945GNT 
**RAM:**
*Module 1*  DDR2, PC2-5300 (333 MHz), 1024 MBytes, Kingston 
*Module 2*  DDR2, PC2-4300 (266 MHz), 256 MBytes, Kingston
**HDD:** Seagate 80GB (PATA)
**AGP:** Builtin
**Sound Card:** Creative Sound Blaster Live (4.1)
**TV Card:** Pinacle PCTV Pro

---

### Post by Rocket2DMn on 2008-01-25
Sounds like the system is loading, but the GUI is not showing.  This happens sometimes, but you can get to a terminal interface by hitting CTRL+ALT+F1 and logging in.  Once logged in, you can reconfigure X (the GUI).
The following command will ask you questions about your hardware, do your best to answer. You said you have an builtin video card, but is that like an ati or nvidia card built into a laptop?  If it's an ATI, when you're asked about video drivers, select "ati", or "nv" if it's nvidia.  Otherwise, if you think it's an onboard intel card, use "intel".  If for some reason none of those work, try again and select "vesa" which is more of a backup universal driver.  At the resolutions questions, use TAB to move around and SPACEBAR to select your monitor's max resolution and everything less.
```
sudo dpkg-reconfigure xserver-xorg
```
Then stop and restart gdm (GNOME)
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

Note that when you use "sudo" you will be asked for your password (at least the first time), but it won't show anything being typed out.  Be assured that it is accepting your password, it just doesn't show *'s or anything.

---

### Post by lisje on 2008-01-25
Does Ubuntu shows you the login screen after a long time of waiting? Because it could just be that the splash-screen isn't showing.

You can turn of your splash-screen by removing 'splash' in grub.

---

### Post by mahmud_simon on 2008-01-25
Rocket2DMn i followed ur procedure but noting happened. CTRL+ALT+F1 does not work. I got new problem now. One of my budddy told me to reinstall the system and i did and now system restart after showing the msg "Starting up ...". Ubuntu does not show me any login screen.

---

### Post by Rocket2DMn on 2008-01-26
Can you boot into Recovery mode from GRUB?  If so, do the reconfiguration command without using "sudo" since you will be logged in as root already.  Then reboot the computer.
If this doesn't work, you have a bigger problem than X not working.

---

