---
title: "&quot;OpenGL&quot; not supported says Google Earth, how to debug?"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by leemckusic on 2006-09-26
I upgraded from 5.10 to 6.06, 

I resolved complete loss of X display by leaving the xserver-xorg package at 10 (not the 10.4 that seems to be still broke on my system 2 weeks after the initial release xserver-xorg problems.

The current video problem is GoogleEarth fails on startup with "OpenGL not supported". 

GoogleEarth documentation says "make sure your OpenGL video card drivers are installed and working." 

So the problem is to figure what exactly in the OpenGL program chain is not working. So far:

lsmod shows the mga driver is loaded

sudo dpkg-reconfigure xserver-xorg offers me the mga driver and seems to set up everything reasonably.

Reading /var/log/Xorg.0.log seems to show the mga driver loading...

----------------- And OpenGL and GoogleEarth woked under 5.10 fine. Reinstalling GoogleEarth results in exactly the same error.

----------------- Any assistance appreciated, I need GoogleEarth to move forward on an urgent software project.

---

### Post by em3raldxiii on 2006-09-26
Perhaps this is a silly question, but which video card do you have installed, and which drivers are running?  Is it a nVidia card with the stock dapper drivers?

---

