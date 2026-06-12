---
title: "Problem installing ubuntu"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by mentallo on 2007-03-05
This is the first time I am attempting to install Ubuntu and I don't know that much about Linux yet. When I try install Ubuntu after a few minutes it shows me message saying that Xserver couldn't start because of a problem with my Graphics card.

I have a 2 Graphics cards installed: 1 is onboard Intel (which I have turned off in Windows) and the other is a GForce FX 5500. I want to use the GForce.


Any help would be greatly appreciated.

mentallo

---

### Post by r4ik on 2007-03-05
press Control-Alt-F1 and try 

sudo dpkg-reconfigure xserver-xorg

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter
Set you're video driver to nv

When you're done, press Control-Alt-F7 to get back to graphical mode and then Control-Alt-Backspace to reset the X server (so your changes can take effect).

From:[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

When you have a visual get you're drivers here

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by mentallo on 2007-03-05
OK tried what you wrote but during the manual detection of the Graphics card it doesn't give me the choice of the Nvidia card I have installed just my Intel onboard one. I did set the Card type to NV though. Also as I progressed in the wizard and I got to the bit rate of my monitor and choose 24 it seems to through me out of the wizard and back to the command line. None of the keyboard button presses did anything after that.

I am not using the Alternate Cd install by the way but the normal one.


What should I try now?

---

### Post by r4ik on 2007-03-06
Have you tried "startx" (no guotes please)

---

