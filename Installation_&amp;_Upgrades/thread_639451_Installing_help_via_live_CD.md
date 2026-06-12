---
title: "Installing help via live CD"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by djdnc on 2007-12-13
Attempting to install via live iso cd, everything seems to work fine until I get to the part asking me for my location. I click on my location but then nothing happens. The screen looks like there may be more at the bottom but while I can move the box around it will not let me move it up far enough to see the bottom of that location screen. (in other words it looks like the screen goes off the bottom and maybe there is something else I am suppose to click to get to the next part-but I cant see it). I have tried to adjust the screen size/resolution but that did not help. I am running a 3d banshee video card. Any advice?

---

### Post by src2206 on 2007-12-13
Do you already have other OS installed? I would suggest that you create two free spaces (one at least 8 GB for Root and the other smaller for SWAP, about twice the size of your RAM) in your HDD where you want to install Ubuntu. Keep those unformatted. You may use free Partition Manager like GParted to do that. Now install Ubuntu and choose manual Partitioning. Choose the Larger partition to mount Root and the smaller to mount SWAP and see if your problem is resolved.

---

### Post by logos34 on 2007-12-13
> **djdnc said:**
> may be more at the bottom but while I can move the box around it will not let me move it up far enough to see the bottom of that location screen. (in other words it looks like the screen goes off the bottom and maybe there is something else I am suppose to click to get to the next part-but I cant see it). I have tried to adjust the screen size/resolution but that did not help.

go back to the desktop.  right-click and move the top and bottom panels to the sides.  That will clear just enough space to see the buttons at the bottom of the installer screens.  Either that or run

sudo dpkg-reconfigure xserver-xorg and choose another graphics driver (like vesa)

---

### Post by djdnc on 2007-12-14
I figured out the problem. The system cmos had to be changed so that the hard drive detection was set to auto and so that the system booted from SCI instead of just C.

---

### Post by logos34 on 2007-12-14
> **djdnc said:**
> I figured out the problem. The system cmos had to be changed so that the hard drive detection was set to auto and so that the system booted from SCI instead of just C.

huh?  you said you were having a video problem, i,e, seeing bottom of the installer screen.  How did changing the bios settings on the hard disk fix things?  You're booting from the install cd, not the hard drive.  You weren't even at the partitioning stage yet where the issue of the hard disk comes up.  Baffled...

---

