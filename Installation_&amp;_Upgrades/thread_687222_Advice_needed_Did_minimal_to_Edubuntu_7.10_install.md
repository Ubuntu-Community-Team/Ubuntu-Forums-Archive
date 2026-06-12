---
title: "Advice needed: Did minimal to Edubuntu 7.10 install, runs slow."
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by breakdaze on 2008-02-04
Hello,

My old system is an AMD K62-550MHz CPU, 20Gb HDD, and 320 MByte RAM.

The Gutsy Live CD of course didn't work, so I picked the Gutsy minimal CD, then I installed dselect to then install the Edubuntu Desktop Metapackage.

Now it works, but it is quite slow.  I want to switch to a different Desktop Manager or whatever, but should I remove the Edubuntu / Gnome stuff, then add the IceWM or whatever, or should I do a fresh install?

Also, I decided to pick the i386 kernel, is this recommended?

Finally, I tried to get the restricted ATI driver (I have a Radeon 9500 - I think), to work but it crashes at the configure part.  Would the driver being installed help the windows and menus move faster?

Thanks,

breakdaze

---

### Post by Partyboi2 on 2008-02-04
You could remove your current desktop and install IceWM
[http://www.psychocats.net/ubuntu/icewm](http://www.psychocats.net/ubuntu/icewm)
or another one
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)
and see if that improves performance. If you are running with low memory a lighter desktop is probably the way to go.
With trying to get your ati driver sorted have you tried envy?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by breakdaze on 2008-02-05
> **Partyboi2 said:**
> You could remove your current desktop and install IceWM

I know I could, please see what I wrote above.  Are you saying it is recommended, or should I blow it all away and start over? Now I go in search of the command to remove Gnome but not X...  sudo apt-get remove gnome-desktop

I didn't try that yet for the driver, thanks for the info.

Am I better off using the i386 kernel or the generic?

Thanks,

breakdaze

---

### Post by Partyboi2 on 2008-02-05
not recommended only  suggested. Gnome desktop is a heavier desktop , but in saying that you should be able to run gnome ok on your spec's, Xfce is a lighter desktop and probably will be faster.
I am not sure what kernel will work best for you. I don't have problems with the generic.

---

### Post by breakdaze on 2008-02-05
I think my hard drive is the slow part, it seeks a whole bunch every time Gnome has to open anything, so there is lag.

With just the base system and X.org installed, can one run graphical apps (e.g. Firefox) right from the command line?  I'm thinking of trying to skip the Windows Manager and Desktop Environment and simply execute as needed from the shell.

Is this possible?

---

### Post by Partyboi2 on 2008-02-05
Midnight commander (mc) is a file manager program that runs in a terminal
```
sudo apt-get install mc
```For web browsers that run in a terminal you have
w3m which is installed by default
lynx
```
sudo apt-get install lynx
```links2 (looks like a good one)
```
sudo apt-get install links2
```retawq
[retawq home page]("http://retawq.sourceforge.net/")
There are probably others as well, but these are what I have come across so far.
Another option if this isn't quite what you are looking for is to install [xubuntu]("http://www.xubuntu.org/"), it works well on slower machines

---

### Post by kerry_s on 2008-02-05
sounds like your not doing the minimal install right.-> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

you got plenty of room to play.
mines a 450mhz 256ram, debian custom install.properly done you should have more than enough resources for anything.

---

### Post by breakdaze on 2008-02-06
**kerry_s**,

Yeah, I'm sure I didn't go about it correctly, I don't recall seeing a prompt where I type "server.'

Anyway, on your custom Debian install, what do you use for window management or desktop?

Do you think there is any advantage to using Ubuntu in a minimal install without Gnome or KDE?  I may as well download Slackware or Debian  or some BSD and play with those.

I actually don't care about a desktop, but I would like to use the web graphically.


**Partyboi2**,

I used to use the lynx browser back in '93 when all I had access to was a unix shell login running SunOs.  It is text only and pretty horrible on the modern web.


Thanks guys,

breakdaze


P.S.  I think I will do it over and try IceWM, it seems popular.

---

### Post by kerry_s on 2008-02-06
> **breakdaze said:**
> **kerry_s**,

Yeah, I'm sure I didn't go about it correctly, I don't recall seeing a prompt where I type "server.'

Anyway, on your custom Debian install, what do you use for window management or desktop?

Do you think there is any advantage to using Ubuntu in a minimal install without Gnome or KDE?  I may as well download Slackware or Debian  or some BSD and play with those.

I actually don't care about a desktop, but I would like to use the web graphically.


P.S.  I think I will do it over and try IceWM, it seems popular.


Debian works better on the old stuff, ubuntu drops alot of the older stuff.
i use " jwm " as my prefered wm, takes a bit of learning but very simple standard compliant wm. very flexable once you learn it.

i use the debian net installer to install the base and build up from there, with debian you just uncheck the all packages when it comes to that part to get a base install.
[http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso)

install base
log in as root
apt-get install xorg gdm synaptic (your-wm) (what-ever-else)
reboot(ctrl+alt+delete)
select your wm and log in
open synaptic and get what ever else you want

very simple. i use etch/lenny, in other words i install etch and then update to lenny. i need the kernel in etch as the 1 in lenny don't work good for me.

the line i used was->
apt-get install xorg synaptic jwm rox-filer leafpad

i don't use gdm for a login manager, as i am the only user and don't change to anything else. so i just setup a autologin and startx script.
i must warn you though, jwm in etch is the old 1, lenny has the good 1.

anyways the only way your going to learn is just to get your hands dirty. :lolflag:

---

### Post by breakdaze on 2008-02-07
Wow, thanks so much..

Just got side tracked for 24hr doing a side project - compiling my own custom kernel.  It works but I somehow didn't enable USB mouse and keyboard support, LOL.

- breakdaze

---

### Post by kerry_s on 2008-02-07
> **breakdaze said:**
> Wow, thanks so much..

Just got side tracked for 24hr doing a side project - compiling my own custom kernel.  It works but I somehow didn't enable USB mouse and keyboard support, LOL.

- breakdaze

yeah, those are the ropes when compiling. i don't compile anything anymore, it's just not worth it most of the time, not for a few miliseconds of speed.

---

