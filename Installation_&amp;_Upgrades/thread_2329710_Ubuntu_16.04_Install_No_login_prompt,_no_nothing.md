---
title: "Ubuntu 16.04 Install: No login prompt, no nothing"
date: 2016-07-04
forum: Installation &amp; Upgrades
---

### Post by UserJB on 2016-07-04
I scrapped the Ubuntu 15.10 install and installed Ubuntu 16.04 instead.  The installation process seemed to go okay.  There were no warnings or errors.  However, when I boot the machine, it gets to the pinkish/purple-ish screen and that's it.  No login prompt (though I did configure the install for automatic logins).  No GNOME panels.  Nothing.  There's a mouse pointer, and I can move it around.  If I disconnect the ethernet cable, it flashed "Disconnected from the network" or something like that, but nothing else is happening.

UPDATE: Actually, it appears I'm logged into the Ubuntu machine, but there are no icons displayed and not GNOME panels.  If I Right-Click with teh mouse, I get the usual menu for creating Folders, or documents, or launching terminals, but that menu is flashing on and off about once per second.

If I create a folder, then that folder icon appears on the desktop, but it is flashing on and off about once per second

What is going on?  The PC is an Intel I7 6800K, and the video card is Nvidia GTX 970.

What next?

---

### Post by kansasnoob on 2016-07-04
I suspect a graphics driver issue but we really need some hardware specs. If you can run a live desktop using any Ubuntu live DVD/USB you could post the output of these commands:

```
cat /proc/cpuinfo
```

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

```
free -m
```

---

### Post by UserJB on 2016-07-04
I'd like to do that too.  But I can't boot into the live CD and run those commands because of the problems I mentioned above.  The flashing icons, and everything else.  What should I do?

---

### Post by UserJB on 2016-07-04
UPDATE: I solved this problem by typing CTRL+ALT+F1 to get a login  window in text mode.  Then I did 'apt-get dist-upgrade' and restarted  the X server.

---

