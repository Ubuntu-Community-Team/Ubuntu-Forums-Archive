---
title: "Upgrade to 16 from 14 and now I've lost Launcher"
date: 2017-02-14
forum: Installation &amp; Upgrades
---

### Post by voxpop on 2017-02-14
Hi people, your help would be appreciated.
Recently I upgraded my shop computer from Ubuntu 12 to 14 without any problems. Then today I upgraded to 16.  Now on the shop computer I can not find launcher and when I do manage to get into settings some of the windows have no way to close them. This computer at home is running 16 without any problems.
I may have answered some of the set-up questions incorrectly, but now I can not get on the internet to do a reload.
Regards
voxpop
PS interesting that the spell checker does not like the word internet!

---

### Post by ajgreeny on 2017-02-14
On the computer with the problem can you try running the live 16.04 DVD/USB to see if there is a problem with that.

What hardware do you have?  There have been difficulties with some AMD graphics cards in 16.04 as the drivers are in a start of flux at the moment, so I wonder if you are being bitten by this problem.

The fglrx driver is a non-starter at present in 16.04, so the radeon driver, or if you're lucky the new AMDGPU driver are what you will have to use, and the correct one of those should be installed automatically when you clean install; not sure about upgrades though.

---

### Post by voxpop on 2017-02-15
Hi ajgreeny,
It's strange. I have good graphics. I can change the screen background and the colours are OK, but I can not get Launcher to appear. I have tried moving the cursor to the left of the screen and holding the mouse button down, but no joy. Super keying has not brought any joy either.
Also when I manage to get some windows up, I can not close them, there is no quit box even when right clicking om help; which doesn't seem to - help!
Arrrgggghhh

---

### Post by #&amp;thj^% on 2017-02-15
Lets see if this will help here:
```
sudo apt-get install --reinstall ubuntu-desktop unity
dconf reset -f /org/compiz
dconf reset -f /org/compiz/
```
Post back any errors from the above commands.

---

