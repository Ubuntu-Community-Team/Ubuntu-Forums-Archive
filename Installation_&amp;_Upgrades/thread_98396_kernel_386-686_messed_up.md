---
title: "kernel 386-686 messed up"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by porsher_puddles on 2005-12-03
i just upgraded my kernel via synaptic from 386-686. and x won't start because it can't load the nvidia driver,what do i have to do to fix this i can boot into my previous kernel ofcourse.
i can't seem to find the answer.

---

### Post by teaker1s on 2005-12-03
make sure you also install the restricted-module to match or it wont boot look [here]("http://ubuntuforums.org/showthread.php?t=85917")

also depending on the age of the graphics card my nvidia suddenly went from current to legacy supported

---

### Post by porsher_puddles on 2005-12-03
now i really broke things !!!
i typed this at this at terminal:sudo apt-get install linux-restricted-modules-`uname -r`
and it says i have the latest version
i already had the nvidia drivers installed and working on my 386 kernel.
i typed at the terminal: sudo gedit /etc/X11/xorg.conf.
and changed my nvidia to vesa in device drivers now when i get to startx in the bootup nothing happens i get black screen, now what do i do ?

---

### Post by teaker1s on 2005-12-03
if you have an nvidia card use 'nv' see if it boots 'nvidia' has more features and therfore can cause more problems

---

### Post by porsher_puddles on 2005-12-03
the problem i have now is i can't get any kernel to boot so how can i change my xorgconf back to nv or nvidia? if i try to boot in recovery mode i get root.ubuntu : if i type in gedit /etc/x11/xorg.conf it says something like unable to load gtk, how can i change the file back?

---

### Post by az on 2005-12-03
[QUOTE=porsher_puddles]the problem i have now is i can't get any kernel to boot so how can i change my xorgconf back to nv or nvidia? if i try to boot in recovery mode i get root.ubuntu : if i type in gedit /etc/x11/xorg.conf it says something like unable to load gtk, how can i change the file back?[/QUOTE]
either 

nano /etc/x11/xorg.conf
of
vi /etc/x11/xorg.conf

or

dpkg-reconfigure xserver-xorg

That will redetect your hardware.

To get back into the desktop from recovery mode type:

init 2

---

### Post by porsher_puddles on 2005-12-04
Thanks guys all is well i have the new kernel up and running and the old one works again too.
thanks for your help

---

