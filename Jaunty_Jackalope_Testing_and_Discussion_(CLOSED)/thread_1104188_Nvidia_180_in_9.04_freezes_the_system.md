---
title: "Nvidia 180 in 9.04 freezes the system"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by briancb on 2009-03-23
Nvidia 180 in 9.04 freezes the system
I can load and start playing Civ 4 Beyond the Sword but after 2-3 turns the screen freezes and so does the computer. I have to restart the computer. If I change the driver to 173 the game runs but at snails pace. I had no problems in 8.10.

---

### Post by Flarkis on 2009-03-23
Go yell at nvidia, literally. My asumption here is that you suffer the corruption bug in the nvidia driver that alot of us have. Basiclly the driver just doesn't work for some things and (like you said) the old drivers are snail slow.

Odd that they worked in 8.10. Normally kernel/xorg versions dont mater but sometimes they do.

---

### Post by dBuster on 2009-03-23
Strange how I have no issues with my nvidia drivers and I am running the 180.37 release.  I am running this on a 64bit install of Ubuntu and contrary to others, have no issues with my video what so ever.  

I would if I were you still report it to nvidia.

---

### Post by captive on 2009-03-23
I think it's very card-related. A lot of users found 180.xx and 185.xx beta drivers (which you can find packaged in a ppa) to be stable and fast. This is not what I experienced on an integrated 8200 card, which is not so fast and IS terribly unstable, with compiz causing graphic glitches and tearing, hard locks and random xorg reboots.
I'm on jaunty 64bit.

---

### Post by jfernyhough on 2009-03-23
No problems for me with 185.13. :)

Even though it's a beta it fixed problems with full-screen apps not returning control after exiting (which was a little annoying tbh).

---

### Post by Chemical Imbalance on 2009-03-23
> **captive said:**
> I think it's very card-related. A lot of users found 180.xx and 185.xx beta drivers (which you can find packaged in a ppa) to be stable and fast. This is not what I experienced on an integrated 8200 card, which is not so fast and IS terribly unstable, with compiz causing graphic glitches and tearing, hard locks and random xorg reboots.
I'm on jaunty 64bit.

Same with my 8300--xorg restarts randomly, etc..

---

### Post by briancb on 2009-03-23
I am also on 64bit. Everthing else works perfectly e.g. videos, flash in firefox but as soon as you start civ4 in wine you get the problem. I.ll go to Nvidia site and complain there

---

### Post by getaceres on 2009-03-29
I have a Geforce 7600 and I was using the 180 drivers in Intrepid and they were completely stable but now in Jaunty I'm getting hard freezes and X crashes with 180.37. I think it has to do with NVidia drivers + xorg version.

---

### Post by linuxisevolution on 2009-03-29
It's time for Xorg to die...

I am having problems with these drivers in hardy. Sometimes I can still see text when I backspace, and if I move my mouse to fast over menus then they all get selected and I can't click :(

See attached screenshot.

---

### Post by drmattoclarkson on 2009-03-31
I'm experiencing the same issue in Jaunty - I had no problems on Intrepid with the 180 drivers.

I managed to get my system to run without crashing by adding maxcpus=1 to the end of my boot parameters in grub.

---

### Post by chenhaw on 2009-04-02
So far what is the solution for this?  I tried not to use Nvidia driver but my resolution is limited to 800x600 only.

---

### Post by kodiakmax on 2009-04-02
Nvidia 180.x series are Notoriously buggy in linux.

Either downgrade to 177.x

or 

Upgrade to 185.13

---

### Post by larrinh on 2009-04-13
I have the same problem with the 180.xx drivers on my AMD64 platform. In both 8.10 and 9.04 if I would resize a window by dragging it the system would lock up and I was forced to hit the power button to restart (not as good thing to do). In 8.10 I was able to install the 177 drivers and they worked great, 173 drivers in both 8.10 and 9.04 have verious problems with updating the screen when you scroll in a window. However, I am forced to use the 173 drivers in 9.04 because for some reason the 177 drivers are not supported by the AMD64 architecture??? odd that it was supported in 8.10 but not in 9.04. Any one know where I can get the latest 177 drivers compiled for install on an Ubuntu AMD64 platform?.

Larrin

---

