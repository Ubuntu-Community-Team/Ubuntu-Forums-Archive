---
title: "USB install problem"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by copracr on 2010-02-05
Hi all.  I installed 9.10 on a usb drive at a desktop at work and it was up and running great.  then the other day i plugged it into my laptop at home.  Now it no longer boots up on the work pc.  I did updates both times.  I'm back home now and its still working fine on the laptop.  What gives?

laptop - acer 5920g
desktop - newer dell optiplex

I'm still really new so be basic with your responses for me,  thanks.

---

### Post by Herman on 2010-02-05
Did you install any special hardware drivers, especially any drivers for the video card in the laptop?

Ubuntu has had the ability to set itself up automatically in most computers since Hardy Heron was released featuring the then new  [Xorg 7.3]("http://www.ubuntu.com/getubuntu/releasenotes/804overview#head-34da8c8d2432823a293ea6a0639fe8b9a24c0f77")  Xwindow system from [X.Org Foundation]("http://www.x.org/wiki/").

Recent version of Ubuntu offer the user the opportunity to install 'hardware drivers' though, but it's not compulsory to accept them. Once we accept the hardware drivers then unless you know how to reverse the changes it's only configured for one computer.

Maybe somebody knows a workaround for this?
Before Hardy Heron we used to just run 'sudo dpkg-reconfigure xserver.org' to scan for hardware and set up Ubuntu for the computer it was in but it used to be a fairly long process.

---

### Post by Herman on 2010-02-05
Do you mean it really does not boot at all do ? Or does it boot but has a black screen?

---

### Post by copracr on 2010-02-05
I did install nvidia drivers when i booted up the laptop.  I also installed all the recommended updates.  I'll try uninstalling the nvidia drivers and try again.  

When I plug the usb drive in,  I get the bios screen,  then "starting grub", then that screen with the small ubuntu symbol hangs for a while until it goes to a black screen.

---

### Post by Herman on 2010-02-05
I fell for that one too, except I installed ATI drivers because Google Earth kept nagging me. I simply re-installed because I was in a hurry when I discovered it wouldn't let me have a display in a different computer.
Surely there's an easy way to reconfigure the X-server in that kind of situation, or there should be more of a warning before installing the hardware-specific drivers.
Or an easy way to uninstall the drivers. 
When I get time I'll try to learn more, unless somebody can come along and enlighten us. :D

???

---

