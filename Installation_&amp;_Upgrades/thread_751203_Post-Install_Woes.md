---
title: "Post-Install Woes"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by neutrino51 on 2008-04-10
I just got done installing Ubuntu, and had some trouble getting off the ground. I couldn't get the live cd to boot, so i finally installed it with the alternate cd. After that, i kept getting the black screen after grub, but I removed "splash" from menu.lst, and finally was able to get to a login screen. However, now i can't actually login, because after about 15 sec or so, the login screen locks, and i cant type or move the mouse. The clock in the bottom right also stops, so i figure its crashed out. Any ideas?

---

### Post by dstew on 2008-04-10
Sounds like a display driver issue. Can you boot into recovery mode (grub menu item)? That should get you a command line. If so, login and enter```
sudo dpkg-reconfigure xserver-xorg
```That gets you a text-based program to reconfigure the xserver, the software than runs the graphical interface. Answer the questions the best you can. Usually the default answers are correct. When you get to the display section, choose the **vesa** driver. For the highest resolution, choose the resolution you actually use. 1024 x 768 I think is typical.

When you are done reconfiguring, enter the command ```
startx
```to start the xserver. If you get a display, look in System --> Administration --> Restricted Drivers Manager to see if a restricted driver is available for your display.

---

### Post by neutrino51 on 2008-04-17
Ok, finally got a break from work and tried that, but there is no option for resolution or for picking a driver at all in the text-based setup.

---

### Post by |{urse on 2008-04-17
ctrl + alt + f1
will get you to a login
then 
sudo nano /etc/X11/xorg.conf
scroll down to the device identifier section
change your driver to "vesa"
press ctrl + x to save
sve modified buffer? = y
sudo init 6
may do the trick without manually changing your resolution

---

### Post by neutrino51 on 2008-04-17
Well, its using vesa now, since its all super fuzzy and not widescreen, but it still totally locks without letting me type in my username or move the mouse. I tried changing it to "nv" for my nvidia card, which lets me see the login screen at my normal res, but it still locks down after a few seconds. Also i couldn't get to a login with the ctrl+alt+f1, but i was able to change it from recovery mode.

---

### Post by |{urse on 2008-04-17
Sweet a little progress ^^
now go download ENVY 
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

that should get everything snazzy again.

---

### Post by |{urse on 2008-04-17
Oh reread your post and i see that your mouse is frozen @ login. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67734/+viewstatus]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67734/+viewstatus")

Now im gonna ask you to do something NAUGHTY! unplug your mouse and plug it back in, if it works then it works but you'll have to do it every time you reboot. :( which will sooner or later lead to a ps2 port being fried.

try rerunning a reconfigure on your xorg and make sure if its a usb mouse it is set appropriately so.

---

### Post by neutrino51 on 2008-04-18
Ok, so i went and disconnected my keyboard and mouse totally, and hooked up an old ps2 keyboard and ps2 mouse, and at login i can now type and move the mouse, however, it still hard locks no matter if i login or not after about 10 sec. I even went in and disabled all the usb ports on my mobo (P5W DH Deluxe) with no change, still locks up at/after/during login. No matter how fast i login, i never actually get to a desktop, it locks at an orange screen with only a mouse pointer on it. If i just wait and don't login, it also locks, but at the login screen as before instead of an empty orange screen.

---

### Post by |{urse on 2008-04-18
we've covered all the usual angles, save for making sure your mouse is correctly congigured in your xorg.conf, but lets skip that since youve tried 2 different mice i'd assume ur xorg.conf is correct. I'd say perhaps bad ram or .. hm have you tried a reinstall since your initial load?

---

### Post by neutrino51 on 2008-04-18
Ya, I've tried re-installing as well. Also if i try to boot to the live cd and remove the "splash" argument as well as setting safe graphics mode, it does the same thing - boots through all the processes and then locks down at the orange login screen. In an attempt to make things better, i removed my x-fi card since i had heard it can cause issues sometimes, and still the same thing happens, on the install or the live cd. I doubt its bad ram either, since I've been/still am running vista x64 on this box for about a year and a half, and a couple months back had OSX86 running on it on a HD thats not in it anymore.

---

### Post by neutrino51 on 2008-04-18
OK! So finally some progress. Your mention of RAM got the ol' gears spinning, and i disabled a "memory remap option" in my bios thats supposed to make 64 bit os's happy since i have 4GB of RAM, and in fact works just fine with Vista x64 and Leopard. Well, i went in there and disabled it, and hooked up the ps2 mouse and keyb, disabled "splash", and chose safe graphics mode and, woo hoo, x64 live cd is now booting. Gonna muck around and see if i can actually get it fully functional now.

---

### Post by Shazaam on 2008-04-18
From what I have read you might try this (even though it applies to Feisty)....

[http://becomingaccie.blogspot.com/2007/07/installing-64-bit-ubuntu-feisty.html](http://becomingaccie.blogspot.com/2007/07/installing-64-bit-ubuntu-feisty.html)

Quote from page.....
```
2- Feisty's Live CD won't run on a 4Gb machine
Solution: This is a known issue. The solution is to disable the "Memory remap" function on the BIOS, install Feisty, run Feisty still with the "Memory remap" disabled and blacklist intel_agp:
- In /etc/modprobe.d/blacklist add the line:

blacklist intel_agp

Afterwards reenable the "Memory remap" feature and boot Feisty. The 4Gb will be there.
```

---

### Post by neutrino51 on 2008-04-18
Well, i got everything installed, and added the blacklist entry as well. Even with the memory remap turned off, using only ps2 mouse and keyboard, running vesa drivers and "splash" turned off in menu.lst, it STILL locks down at the login screen. I was able to do the install via the live cd, but now that i'm booting off the HD, no luck.

---

### Post by neutrino51 on 2008-04-18
So i went into the CMOS and reset EVERYTHING into defaults, and disabled memory remap. Now she finally boots with vga mode and "splash" disabled, and i can login and use the system. I'll try to get it working with some actual video drivers, and try to narrow down what it was that was holding me back in the CMOS config.

---

### Post by neutrino51 on 2008-04-19
Ok, so i finally have it narrowed down. I have everything turned back on except for one. The PEG settings in my CMOS have to be set to auto, or i get the login crashing problem. Also, whenever i hook up my wireless bluetooth keyboard and mouse, it also gives me the login lockup problem. Without either of them, it boots and works fine with restricted drivers and all. However, if i add just one, it resorts to the lockups. The keyboard and mouse work when i boot to prompt recovery mode, just not when i try to use gnome (i get the lockups).

---

