---
title: "No login screen after update"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by craigflynn on 2008-02-17
Hi all, 
I performed an update on my system last night though adapt and on rebooting this morning  I am presented with a command line login and have to startx manually. Does anyone have a clue as to how I get the process automated again so I boot into KDE4 as usual ? Also when i try to shut down the icons are missing from the shutdown window except logout, if i chose this KDE closes down and takes me back to the command line, pushing the power button then triggers the full shutdown. Please, any idea's on this or how to investigate ?

Cheers
Craig

---

### Post by craigflynn on 2008-02-23
Sorry to bump but does anyone know ? Im really trying to avoid a reinstall

---

### Post by leehach on 2008-02-23
I'm just learning Ubuntu, so what I'm about to say is very imprecise, but FWIW:

I had the same set of problems on GNOME rather than KDE, and solved it by getting my xorg.conf in order.  Try running ```
sudo dpkg-reconfigure xserver-xorg
```  I did this, and everything started working because I added refresh rates for the monitor.  See my post at [http://ubuntuforums.org/showthread.php?p=4390410](http://ubuntuforums.org/showthread.php?p=4390410).  Note that in your case it might not be the monitor refresh rate, but I think the lesson I learned is that if *anything* is wrong with your graphics settings, X won't start, and when you start it from the command line, you don't get the Shutdown/Restart options, which I assume are configured to appear during the init process if it starts normally.

This problem was hard to track down, because it seems there a million different things that can cause it, so some of the solutions seemed pretty hard core in terms of editing any number of configuration files or startup scripts.  But this solution in my case turned out to be very simple, and your problem seems to be the same.

---

### Post by craigflynn on 2008-02-23
Thanks for the input but that didn't solve the problem. There is also a message about no resume image being available at start up, this is shown on the command line screen before i enter username. & then startx ? Does this make any sense to anyone ?

Craig

---

