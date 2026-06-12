---
title: "gnome starting problems - Feisty"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by Nora on 2007-09-07
Hi!

I have recently installed Ubuntu Feisty on my PC on a second hard disk.
Everything works fine except that sometimes gnome is somehow blocked after booting. Either only the two empty bars appear at the top and at the bottom of the screen and nothing else. Either everything appears but nothing works, I can't open a terminal or launch any program.
In that case I have to reboot or turn the computer off and on again which is not a very ,,tender'' thing to do. 

Any idea, why it might happen and how I can sort it out?

Thanks!

---

### Post by ghantoos on 2007-09-07
did you try to press Alt+F2 to get the "Run Application" window,

then enter gnome-terminal or xterm to open a terminal?

Cheers,

Ghantoos

---

### Post by Nora on 2007-09-07
I'm afraid the whole gnome freezes in these cases. 
But I'll try to do what you suggested.

Thank you...

---

### Post by Nora on 2007-09-08
I tried everything (Ctrl+alt+backspace, ctrl+alt+f1, alt+f2 etc) but when it freezes it doesn't react to anything. 
If I boot in recovery mode, and start gnome manually (/etc/init.d/gdm start) then it works fine except for the error message "Couldn't initialize HAL". 
I've read on the forum that others had similar problems, but I couldn't find any solutions...

I would be grateful if somebody could explain the phenomenon and help.

---

### Post by Pumalite on 2007-09-08
[http://ubuntuforums.org/archive/index.php/t-198277.html](http://ubuntuforums.org/archive/index.php/t-198277.html)

[http://ubuntuforums.org/showthread.php?t=362727](http://ubuntuforums.org/showthread.php?t=362727)

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/68574](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/68574)

[http://blog.ubrio.us/gnome/ubuntu-error-hal-failed-to-initialize-udev-address-already-in-use-solution/](http://blog.ubrio.us/gnome/ubuntu-error-hal-failed-to-initialize-udev-address-already-in-use-solution/)

---

### Post by Hashte on 2007-09-16
Try to **reinstall ** *gnome-panel* in Synaptic :D

---

