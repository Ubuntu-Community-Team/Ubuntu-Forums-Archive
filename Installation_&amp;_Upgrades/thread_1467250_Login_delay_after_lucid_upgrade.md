---
title: "Login delay after lucid upgrade"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by shadysamir on 2010-04-30
I am having a problem after upgrading from Karmic to Lucid (64bit)

Right after I type in my username and password and hear the usual login sound I have to wait about 15 to 20 seconds to get the X desktop. The system load average monitor is at its max and starts to become lower.

If I log out and in again I dont get that delay. It only happens with logging in after a reboot/power on.

I tried to open a console (Ctrl+Alt+F1) before I log in, move back to X and login then jump to console and use htop to see what's eating up my resources during that time with no luck. Everything seems to be normal.

---

### Post by dino99 on 2010-04-30
try:
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

sudo dpkg --configure -a

---

### Post by shadysamir on 2010-04-30
I tried that, did not change a thing.

I tried one thing, since google-desktop crawler was taking up some CPU in most of my tries I uninstalled it. Now X desktop loads faster compared to before but still not as fast as expected and average load is still high

I am guessing this has something to do with how Lucid loads things on start up

---

### Post by Duckter on 2010-05-18
That made absolutely no difference
...
To fix it try disabling Floppy Disk Drive in BIOS - works for me

[http://ubuntuforums.org/showthread.php?t=1470682](http://ubuntuforums.org/showthread.php?t=1470682)
[http://ubuntuforums.org/showthread.php?p=9205861](http://ubuntuforums.org/showthread.php?p=9205861)

---

