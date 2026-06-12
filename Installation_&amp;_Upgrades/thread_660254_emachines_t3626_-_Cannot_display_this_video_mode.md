---
title: "emachines t3626 - Cannot display this video mode"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by msrk on 2008-01-06
Hi,

I searched the forum for the last two hours and have not found a solution to my problem.

I have successfully, seamlessly, installed ubuntu on a couple of desktop machines already.  Today I bought a new EMachines T3626 with a NVIDIA GeForce 6100 chip and have a Dell E151FPb 17in monitor.  I put my ubuntu 7.10 cd in and boot.  I get the first menu and select the default to install.  Everything looks great until I get the message "Cannot Display This Video Mode".

The computer seems to be hung.  I cannot get a text prompt with Alt-F keys.  I have tried rebooting in graphics safe mode, I've tried noapic options, I've tried lots of suggestions that I find in the forums but I get no further than the "Cannot Display This Video Mode" message.

I have tested the memory and the install cd.  Both are OK.

I took out the "quiet" boot option and all systems are OK while booting but then at the end of the boot process it hang.

Any help would be greatly appreciated.

Thank you,
Marc

---

### Post by taurus on 2008-01-06
Perhaps you should consider using the alternate CD to install it on your new Emachine.  It's a text based installer but should be real easy to follow.

---

### Post by msrk on 2008-01-06
Yes, thank you.  I was just reading about the text based installer.  Do you know if I do that will I have a chance to install the proper video drivers and change the x config before starting x?

I'm still hoping someone will advise on how to do it with the regular install disk.

I suppose the Ubuntu maintainers would want this to work because I expect this low end emachines to be popular hardware since it sold at Best Buy.

Thank you again, I'll try the text based installer.

---

### Post by taurus on 2008-01-06
It will probably configure the X server for your harddrive.  And if you are running into a problem with it, you can always reconfigure with

```
sudo dpkg-reconfigure xserver-xorg
```
Once you have Gutsy installed, you can go into System -> Administration -> Restricted Drivers Manager and install nvidia driver for your graphic card so you can run some 3D like compiz-fusion stuff.

p.s.  I have XFX GeForce 6800XT and the alternate CD didn't have any problem configure X at all.

---

### Post by msrk on 2008-01-06
I will try.  But I'm not sure how I will get a chance to reconfigure x if don't have any video.  If I understand this correctly then I'll manually start x from the text based install and if it is not configured properly I'll be able kill x, reconfigure, and try again, right?

Thank you for being so responsive.

---

### Post by taurus on 2008-01-06
The alternate CD will install the same stuff as the desktop CD/LiveCD, including X and Gnome.  A lot of people thought that alternate CD won't give you X when you finish installing it.  That's not true.  You don't have to install anything extra to get Gnome running.  When you are finished installing, it will ask you to remove the CD and reboot.  It will reboot into GUI login screen just like the desktop CD would.  

If you want command line only, then you would install the server version.  Then, you need to install X and Gnome separately if you want a nice window manager.

---

### Post by msrk on 2008-01-06
OK, I think I understand.   I'm sorry to be so tedius but if I do the text based install then won't I end up with the same "Cannot Display This Video Mode" message?

Do you know if this is a video card problem or a monitor problem?

Thank you,
Marc

---

### Post by msrk on 2008-01-06
I finally got it to work with the regular 7.10 install disk.  Before it locked up I managed to grab a virtual terminal with Ctl-Alt-F1.  When I got a prompt I ran:

$ sudo dpkg-reconfigure xserver-xorg

All is well.

---

