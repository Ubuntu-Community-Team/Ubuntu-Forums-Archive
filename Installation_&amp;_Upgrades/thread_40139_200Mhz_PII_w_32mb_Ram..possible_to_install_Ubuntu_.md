---
title: "200Mhz PII w/ 32mb Ram..possible to install Ubuntu with ICE or XFce only?"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by haldrik on 2005-06-07
Hello Everyone:
I'm looking to install Linux on an old Win95 computer (dual boot) at the office with just 32 MB Ram and 200Mhz. I only basically need Xwindows (maybe ICEwm or other minimal desktop), Firefox, Thunderbird mail, and Abi-Word, and maybe SMB client to print to windows network printer.  I want to show my coworkers that Linux will run better on that machine than Win95 (which is slow as tar for even the smallest app). 
I've asked on other sites and been told to use Slackware or Debian, but I like Ubuntu on my real computer. 
Now the question: Is it possible to do a "minimal" install of Ubuntu on that computer and get decent results? (I've tried Vector Linux and it works rather fast, but for certain reasons, I'd like to switch it out). If so, which desktop or wm should I install, and can I skip the KDE/Gnome thing altogether? (I only have about 1.5 gigabytes of HD).
Thanks for your input!

---

### Post by az on 2005-06-07
The installer needs 32 megs of memory to install.  There are some systems where that is not enough and the installer locks up.  You will have to try it.

Other than that, look here:
[http://test.wiki.ubuntu.com/forum/installation/DiskSpace](http://test.wiki.ubuntu.com/forum/installation/DiskSpace)
[http://test.wiki.ubuntu.com/forum/installation/Minimal](http://test.wiki.ubuntu.com/forum/installation/Minimal)

---

### Post by wvslkr on 2005-06-07
I am running an old P233 and my advice is quite simply do not bother unless you
can or are willing to install more ram.

Even if the installer will complete with only 32meg X would be too sluggish to be usable
and probably wouldn't even run without plenty of swap.

I have 192meg and can run KDE or Gnome. If you plan on using X I would recommend
at least 128meg.  You might get by with a lighter wm on 64meg but I suspect it would
be too slow.

Hope that helps. :)

---

### Post by haldrik on 2005-06-07
Unfortunately, adding ram is not an option...it's an office computer in a university office, and I'm not allowed to add or take out anything.
I'm surprised to hear that X may not run at all...like I said, I have currently Vector Linux running and with Xfce it works ok, there are just some apps that do not run at all, including the app-installer, which is why I thought of trying a different distro. 
Supposedly Slackware can run OK on 16megs w/o xwindows and with 32 megs with a dirt minimal desktop, but it is notoriously tedious to install, and since it's not my equipment, I didn't want to risk it. Also maybe debian, but since Ubuntu is deb-based, I thought I'd try here first, esp. because installing Ubuntu was so easy for me last time, even on a laptop.

---

### Post by madmetal on 2005-06-08
hm.. my second pc is a celeron 366 w/64mb ram so i may try to install ubuntu with XFce.
as wvslkr said this may work good.

---

### Post by andlinux21 on 2005-06-09
[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]XFCE maybe your only hope my friend you should be able to get it working[/COLOR][/SIZE][/FONT]

---

### Post by haldrik on 2005-06-11
Well, I didn't manage to get Ubuntu installed. As predicted by one of the respondants, the installed really seemed to need a tiny bit more memory than I had available, and therefore crashed/froze each time I tried. Oddly, I finally tried doing a Debian minimal install and it worked. The XFce environment works like a charm, BTW... 
If it makes anyone feel any better, I just put another install of Ubuntu on a better-equiped desktop, so we are now a 3-Ubuntu-Box family!

---

