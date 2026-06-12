---
title: "Ubuntu 9.1 no keyboard or mouse input after bootup (stuck at login)"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GermanMafia on 2009-10-15
Hello!

So I installed Ubuntu 9.1. So the first time it booted up I couldn't use the mouse or keyboard, I rebooted it (power button) and then got the bad environment block error. I got that sorted, but now we're back to where we started (no keyboard or mouse input). The cursor is hovering over the login, but no keyboard or mouse input register. I'm using an HP desktop, wireless Microsoft mouse and keyboard, and I tried using my Logitech mouse, but that doesn't work either. Any help would be much appreciated!

---

### Post by DoctorLes on 2009-10-25
I have a nearly identical problem on two computers.  One is an HP laptop with ATI graphics built in, running at 3GH, without any other OS on it.  It ran older Ubuntu versions but later ones I had similar problems like I have now; it took a long time to fix them and I can't &$#@ remember what I finally did that worked, but I'm pretty sure it had to do with the video drivers and the xserver.config file.    

The other box is an HP desktop with Nvidia graphics running at about 2.1 GHZ.  Both easily pass minimum requirements for running Ubuntu 9.1.  

I've tried installing proprietary drivers and all the usual tricks that I've read about on the net, but with no change in outcome. Sometimes the GUI splash screen has white and colored horizontal lines running completely across the screen, obscuring about 25% of the wallpaper view and login dialogue boxes.  

When I've booted in safe mode I have chosen "repair packages", and "attempt to fix X Server", etc. but with the same end results.  

I can run as a terminal but as soon as I try to run "startX" command it loads the splash/login screen without any apparent keyboard or mouse affect.  Yet, I can hit Control-Alt-Delete and it will reboot.  This makes me feel that the problem still has to do with the video drivers and xserver.config file.

There is also sometimes an error message in a box on the frozen GUI splash screen with an option to choose, but I cannot select any response using keyboard or mouse.  It says, paraphrasing, "User Switcher has quit unexpectedly" with options of "Don't reload" and "reload".  I don't think this is a valuable clue but I'm including it just in case. 

I don't mind spending time trouble shooting these things because I always learn something new and it's like solving a puzzle; gratifying in the end.  But I'm just out of clues right now.  

TIA,

DoctorLes

---

### Post by Zorael on 2009-10-25
> **GermanMafia said:**
> Hello!

So I installed Ubuntu 9.1. So the first time it booted up I couldn't use the mouse or keyboard, I rebooted it (power button) and then got the bad environment block error. I got that sorted, but now we're back to where we started (no keyboard or mouse input). The cursor is hovering over the login, but no keyboard or mouse input register. I'm using an HP desktop, wireless Microsoft mouse and keyboard, and I tried using my Logitech mouse, but that doesn't work either. Any help would be much appreciated!
Never reboot with le power button, read up on sysrq commands.

When I had this, it was caused by d-bus not starting, which in turned caused HAL not to start. First, do make sure you don't have broken packages by booting into recovery mode and pick fixpackages. Then pick resume and try again.

If it didn't work, once at the login screen hit alt+sysrq+R to enter raw keyboard mode, then ctrl+alt+f1 to get to a terminal. Login normally, and see if either is running.
```
$ pidof hald
*<should return a number>*
$ pidof dbus-daemon
*<should return one or two numbers>*
```
If they aren't started and you know you don't have broken packages, try starting them manually and see what they say.
```
$ sudo hald --verbose=yes &

$ sudo dbus-daemon &
```
If they are now started, just restart kdm or gdm or whatever you're using.
```
$ sudo restart gdm
$ sudo restart kdm
...
```
At first opportunity, try to download updates and do a full upgrade to see if this has been fixed. This can be done from a terminal (outside any graphical interface) if your network is wired and set up to use automatic IP assignment (DHCP). Obviously possible otherwise too, but difficult.
```
$ sudo dhclient eth0   *# replace eth0 with your interface identifier if different*
$ sudo aptitude update
$ sudo aptitude full-upgrade
```

---

