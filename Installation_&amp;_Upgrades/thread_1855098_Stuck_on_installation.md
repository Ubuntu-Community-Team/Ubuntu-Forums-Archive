---
title: "Stuck on installation"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by private_lock on 2011-10-05
Hello!

I'm trying to recycle some old hardware for web-surfing via my TV ... As the ordinary kubuntu-live-cd runs really slow, I wanted to switch to lubuntu 11-04.

Running the lubuntu-CD, I get a live session. But starting the web browser cromium or the installer, it takes ages and then after about 10 minutes the screensaver (a bunch of glas fibers) kicks in ... no other window came up.

---

If I try the direct install from the boot menu, I'm stuck with a mouse pointer on an absolutely empty blue screen. It flickers white about once a second ... it's like a police cars alarm lights.

By accident I scrolled the mousewheel and it cycles between 4 virtual desktops. On rightclick there is a menu, where I can get a terminal and a webbrowser. But how do I start the install from there?

As long as the LXTerminal 0.1.9 is loading from the CD, the white flashes slow down significantly ...

Starting the webbrowser shows a full-screen window with one tab. But the mouse is frozen and I cannot go on from there.

---

Finally a sidenote: My TV-Set is very choosy about graphics modes. Often it complains about "unsupported mode". Therefore I had to run the CD-selftest and the RAM-Check with an ordinary monitor. It would be great to restrict these basic functionalities to very basic video modes.

Waiting for your comments
private_lock

---

### Post by private_lock on 2011-10-06
Well the Lubuntu-Live-CD seems to be buggy beyond repair :-(

Some times I could get cromium to ask me for my favorite search site. But after selecting one, it just broke down. In addition, it often took the network connection icon with it from the tray. (BTW: networking was OK, I could always ping google.com)

Clicking the desktop icon to run the installer, sometimes, the icon just vanished. Some other times, it made the whole panel with start menu and tray area disappear.

Well but the good news: I managed to install kubuntu 10.10, update it to 11.04 and install package "lubuntu-desktop" ... the whole process took up about 4 hours, but right now I'm running rekonq in Lubuntu :-)

So you may mark my initial problem as solved.

---

### Post by mastablasta on 2011-10-06
you can mark it yourself in thread tool in upper right corner.
 
i wanted to suggets trying LinuxMint LXDE but i see you got it working eventually and in a strange way. 
 
be sure to give all relevant data (CPU, GPU, RAM...) next time as people might respond faster and better.

---

### Post by private_lock on 2011-10-16
Today I've upgraded that machine to version 11.10.

On login to my administrator account I got an automatic dialog popup asking, if I wanted to upgrade. I said yes and provided my password. But nothing happend :-(

So I launched KPackageKit inside LXDE and triggered the version upgrade manually again, ignoring the about 160 individual package updates for the former 11.04. It took about 3 hours again, as the update was constantly using up to 450 MB of SWAP-Space. But it finally succeded :-)

The system specifications are:

1.3 GHz AMD Single Core CPU
256 MB RAM
30 GB Harddrive

---

