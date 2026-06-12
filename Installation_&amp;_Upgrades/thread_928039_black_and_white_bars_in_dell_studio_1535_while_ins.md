---
title: "black and white bars in dell studio 1535 while installing ubuntu"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by kizofilax135 on 2008-09-23
So I am trying to install ubuntu in my laptop, first I tried booting from the cd and installing from the "try ubuntu" but I couldnt get to the desktop, the screen got white and then with white and black stripes (horizontally)

I tried with wubi and it installed but when I tried to log into ubuntu it was the same behaviour


System

DEll studio 1535 intel core 2 duo

Video: intel 965GM graphics

THe laptop comes with vista so Im trying to get it to dual boot


Please help!!  

ThaNks

---

### Post by Kalimotzxo on 2009-01-30
There is an update that fixes this.  The easiest way to get it working is to load the install disc, hit F4 when ubuntu is loaded (The screen where you can select "Try without modifying my computer").  Select safe graphics mode.  This forces the vesa driver.

Then go through the install as normal.

Run:
sudo apt-get update
sudo apt-get upgrade

Go get some coffee and come back about 20 minutes later.

edit /etc/X11/xorg.conf and change the word "vesa" to "intel"

restart the computer and you should be in business.

I know it sucks not to have it working "out of the box" but this particular problem is caused by a specific LCD Dell used to make the 1535.

---

### Post by lazar689 on 2009-11-23
> **Kalimotzxo said:**
> There is an update that fixes this.  The easiest way to get it working is to load the install disc, hit F4 when ubuntu is loaded (The screen where you can select "Try without modifying my computer").  Select safe graphics mode.  This forces the vesa driver.

Then go through the install as normal.

Run:
sudo apt-get update
sudo apt-get upgrade

Go get some coffee and come back about 20 minutes later.

edit /etc/X11/xorg.conf and change the word "vesa" to "intel"

restart the computer and you should be in business.

I know it sucks not to have it working "out of the box" but this particular problem is caused by a specific LCD Dell used to make the 1535.

The very same behavior for my Dell 1535 with Intel 965 video controller

After 3 days of looking around for new ideas, incidentally I connected a projector to review my presentation and after reboot, I selected "Ubuntu" ......with the projector connected.

I was able to see on the wall the install steps, including formating the private partition on my disk......same time I see vertical black and white strips on my screen :popcorn:
Ya, I got my Popcorn and switched my computer OFF.
:KS
And this moment I am in thoughts for "How to redirect the Projector output to my main screen".

---

### Post by lazar689 on 2009-11-23
My Dell 1535 with Intel video controller is up and running Ubuntu 9.10.
I used "nomodeset" switch for the install.
Gorgeous 1280x800 screen

---

