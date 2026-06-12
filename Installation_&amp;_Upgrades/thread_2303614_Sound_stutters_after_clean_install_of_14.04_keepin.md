---
title: "Sound stutters after clean install of 14.04 keeping 12.04 home mount point"
date: 2015-11-20
forum: Installation &amp; Upgrades
---

### Post by brendonwp on 2015-11-20
I installed 14.04 onto a new SSD, keeping my home partition from my 12.04 install on my laptop on the mechanical hard drive.  Most of my settings came across fine, and my wine installs upgraded in place quite gracefully too.

Any music or video playback stutters every two seconds more or less, not breaking up but repeating a millisecond or so.  I thought it might be that Unity was a bit demanding for my hardware, because the mouse and keyboard "stick" every now and then. The mouse jumps slightly, and while typing a letter sometimes appear twice and then disappears when I go back to correct it.

I've switched off a lot of Unity graphic effects, tried the XFCE desktop, and googled for solutions but these issues just won't go away.  
 
My hardware is a Dell n411z, with quad-core i5 (2.3GHz), 6GB RAM and Intel HD3000 graphics onboard.  I added a 128GB Kingston SSD in addition to the 500GB mechanical HDD that came with it originally, using a caddy bought from Newmodeus.

---

### Post by brendonwp on 2015-11-21
The problem doesn't appear when I boot Xubuntu from a live USB drive, and it doesn't appear before my psensor windows pops up either.  My guess is that something is loading in the background and causing a conflict that results in this weird behaviour.  The installation is almost identical to my desktop, that runs fine.   
The only thing that comes up after boot is a "System Error", that shows that VirtualBox has crashed.  It states that "libffi6 and libpng12-0 are obselete".  When I look on synaptic, the packages have an exclamation mark next to them, although the installed and latest versions seem to be the same.
Any advice?

---

### Post by brendonwp on 2015-11-21
Managed to upgrade and update the two libraries, but the stuttering remains. Advice on identifying apps loaded after startup, or where to look for assistance, would really help.

---

### Post by kostkon on 2015-11-21
Probably you would need to clear some of your configs so that new can be created, for example, [reset your Unity]("http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html") and also your PulseAudio config by deleting the folder *~/.config/pulse*. You could also try resetting Gnome. All these changes will remove any manual configurations you've made, like desktop themes, icons themes, etc.

In both cases, make sure you log out and log back in.

---

### Post by brendonwp on 2015-11-21
Thanks, I'll give this a try as soon as I have some time. I've also installed bootchart, but the output is very detailed and I cannot make sense of it easily.  So I uninstalled until I have time to go into it in detail.  If I need to use it again..

Found the issue: for some reason each time psensor polled the CPU temperature it caused the "stuttering".  Increasing the poll time to 5s increased the stutter to every 5s.  So I removed it, and now my system is fine.  It works fine on my desktop, but on the laptop it was a problem.  Thanks kostkon, I'm closing this as solved.

---

### Post by kostkon on 2015-11-21
Problem solved :KS

---

