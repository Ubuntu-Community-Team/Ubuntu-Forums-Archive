---
title: "I can't boot after upgrade to 15.04"
date: 2015-07-30
forum: Installation &amp; Upgrades
---

### Post by miguel42 on 2015-07-30
I recently upgraded my Ubuntu Gnome 14.04 to Ubuntu Gnome 15.04, and now I cant boot! When I start the computer, the screen has:
```
starting version 219
[   OK    ] Started MySQL Community Server.
```

The text after  [   OK   ] use to change every bn
ooting.
I can enter to bash by pressing Ctrl+Alt+F1
And whenever I press the shutdown button it appears the screen that appears when you shutdown normally in ubuntu gnome.

I tried everything, I reinstalled Gnome-shell, did a lot of operations with apt-get (like dist-upgrade or -f install) but nothing...

Maybe its the drivers of the video? I searched for them on internet but I didn't found... Its an Radeon 7450

I don't know what to do, I dont want to reinstall Ubuntu... Please help me I'm so lost :( Thanks in advance.

---

### Post by orj-gmail on 2015-07-31
same here affter normal update to ubuntu gnome 15.04. leaves me with a blank screen. sent a bug report, it seems to be a problem with the fglrx driver. i hope there will be a fix soon.

---

### Post by bolero11 on 2015-07-31
same here.

I did an upgrade of my system by installing a new Motherboard, Graphics Card, CPU and Memory. My graphics card is MSI GTX-970 , MB is MSI B85-G43, CPU is Intel i5 and 32GB ram. 

 I wasn't able to install 15.04 from the live CD , it would start up and then the monitors just would turn off while I could still hear it running up, so I suspect it had a graphic card incompatibility issue?. Possibly Nivda drivers? 

So then to work around it I first installed 14.04 which worked fine and installed the Nivda utilities and drivers and then did an upgrade to 15.04 from there thinking the drivers will stay there after the upgrade. But no luck and it just goes to a purple blank screen on boot.

I tried booting up in recovery mode and then selected graphics fail safe. but sill no good.

what is the fglrx driver for?   

Look forward to a fix soon.

---

### Post by QIII on 2015-07-31
fglrx is the driver for AMD graphics cards.

Did either of you uninstall the fglrx driver *before* updating to the new release?  If not, that is likely your problem.  Leaving a proprietary driver installed when upgrading is the surest route to problems.

---

### Post by orj-gmail on 2015-08-02
I uninstalle and reinstalled fglrx, but nothing changed. The new (not working fglrx package came with a kernel update too) if I use the older kernel fglrx is working. I'm using ubuntu gnome 15.04. Sent bug report too.

---

### Post by pulpo692 on 2015-08-09
Fglrx seems to be updated an is working now here. Problem solved.

---

### Post by ken78724 on 2015-08-10
Am curious, if either of you had upgrade to 14.10 and then to 15.04 do you believe this might have solved the Fglrx? 

It's been five to six years since I have upgraded, so this is my first time to see an Fglrx create a non-working screen.

Thanks.

---

