---
title: "problem with gui and x11 server"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by vigya on 2008-11-23
i have an NVIDIA gefoecre8400 graphics card and was having some problem with the display, as in, my screen would hang. so i got the required driver and tried installing it on my desktop.

now, it said that i needed to disable x server to install it. so i went to the synaptic package manager and removed all x11 packages. all others that were clubbed with it also got removed. 

den i installed the driver from terminal.

it said it required to compile an nvidia kernel, which it did.the driver was also installed.

but now when i restart my pc, as i donot have an xserver, i dont get a desktop.


i still have my os running and some packages installed in it. so i dont want to reinstall my os.

how do i get back my gui??

can d xserver and d nvidia graphics card run at the same time.

among the packages dat got removed with xserver, was also d gnome desktop i was using.

---

### Post by vigya on 2008-11-23
also, i dont have an internet connection on my hostel room pc. 
but i have d required driver downloaded with me.

---

### Post by Katzwinkel on 2008-11-23
Hello,
I've had a similar problem. I don't know the exact details, but the newer Ubuntu versions seem to have a problem with the NVIDIA-graphics card. But you can work around that without reinstalling the system:
1.)You have to enter the comand shell (maybe you will have to press ctrl+alt+F5 and then login with your user name and pasword to do this)
2.) type the comand:
sudo dpkg-reconfigure xserver-xorg
3.)in the menu you then get change the graphics-card-setting to "nv" ("vesa" could work also)
4.) there will be a lot of further options to change. try keepng the standard-settings for those (just press enter).
5.) restart x-server by typing:
sudo /etc/init.d/gdm restart
or just reboot your System

the x-server should be working again now (was the case with me).

---

