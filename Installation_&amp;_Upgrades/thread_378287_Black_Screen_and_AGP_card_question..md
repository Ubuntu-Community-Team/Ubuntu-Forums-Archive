---
title: "Black Screen and AGP card question."
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by f22cb9 on 2007-03-07
This is my first time ever installing something ubuntu and I got some trouble. I have the black screen after the splash, so I tried a few things but nothing has worked. I notice however in xorg.conf it says something to the effect I have a a graphics card in the PCI slot, but I have a AGP card. I was wondering if there was anything I need to change and what I would change it too? I have been trying to install ubuntu 6.10.

---

### Post by f22cb9 on 2007-03-07
Sorry, to make it clearer I'm talking about the  BusID, is there any changes I need to make to it or what should be in there for an AGP card?

---

### Post by bulldog on 2007-03-07
I have a 6800Ultra AGP card and it's listed as follows in Feisty.
Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800 Ultra]"
    Driver         "nvidia"
EndSection

In Dapper it's listed as,
Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Hope it helps you a little.

Did you try to reconfigure your xorg.conf?
```
sudo dpkg-reconfigure xserver-xorg
```
Have you installed drivers for your graphics?

---

### Post by f22cb9 on 2007-03-07
No, I havent, how would I go about? I thought I could use the nv option during installation. I am completely new to this. Thanks for the help.

---

### Post by bulldog on 2007-03-07
To install the nvidia driver you can type in a terminal or in a console ```
sudo aptitude install nvidia-glx
```

Maybe you have to set the "nv" to "nvidia" manually in your xorg.conf```
gksudo gedit /etc/X11/xorg.conf
```
Safe the file when you're done and reboot to see if it works out.

---

### Post by f22cb9 on 2007-03-07
When should I type in the code? and how would I get to a console. Can i just F6 the first option for install, remove the splash part and replace with break=bottom, then when it gives me the command line, I use the install code you gave? SOrry it is' vague, I'm having a little trouble with the lingo. Also i don't have ubuntu installed yet, i'm getting the black screen during the install process, right before going to the login screen (i belive it's the login screen that comes next...) Thanks bulldog!

---

### Post by bulldog on 2007-03-07
When this problems are with the install,you can't do anything I suggest to you :) 

This can only happen after you installed ubuntu.

It's a known fact that the live cd isn't working very well for everyone,I'm afraid.
If it's not to much inconvenience I should suggest to download the alternate install cd instead of the live cd.
This install is in text mode and it's less demanding to your system.
It's basically as easy as the live cd,but  without the eye candy.

---

### Post by f22cb9 on 2007-03-07
Darn, I was hoping it would. I give the alternative cd a try once i figure where it is to download. Thanks for all the help bulldog.

---

### Post by f22cb9 on 2007-03-08
*UPDATE*

I was able to get it to install! I replaced the splash - quiet  with break=bottom, then at the comman line I typed chroot /root nano etc/X11/xorg.conf. Changed "vesa" to "nv" saved and then BINGO!

Now I think I need to update the driver because my graphics isn't quite what is was in XP.


*EDIT*
I updated the driver and man did it make a difference! I am soo excited  to be using ubuntu, next to tackle is Beryl...

---

