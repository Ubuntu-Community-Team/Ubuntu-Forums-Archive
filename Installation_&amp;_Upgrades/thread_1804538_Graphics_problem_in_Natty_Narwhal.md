---
title: "Graphics problem in Natty Narwhal"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by quantumcop on 2011-07-14
Hello everyone,

I've been using Maverick for a little while now and have had almost no problems with it. I decided that I would try Natty from a Live CD, but when I booted it up, all of the colors were completely screwed up. The system is completely functional and everything works correctly, but I can't actually see much of anything because all of the colors are so distorted.

I tried messing around with the monitor and graphics settings, but nothing seems to work, and it doesn't look like anyone else is having this problem, as far as I can tell. I attached a picture of the screen to this thread, which I had to take with a camera; a screenshot taken from within Ubuntu displays normally on other machines.

I have no idea what's going on. Any help would be greatly appreciated.

---

### Post by mikewhatever on 2011-07-14
What happens if you logout, select the option with no effects under Session, and log back in? The output of lspci would also be nice, it will provide valuable info about the graphics hardware you have.

---

### Post by quantumcop on 2011-07-14
> What happens if you logout, select the option with no effects under Session, and log back in?

I tried to log out and log back in in order to switch users, but I don't think I can log out from a live session without shutting down completely. The "power button" menu at the top right doesn't list anything like "Log Out" or "Switch user".

> The output of lspci would also be nice, it will provide valuable info about the graphics hardware you have.

I'm not sure what that is. Is that a terminal command?

---

### Post by quantumcop on 2011-07-14
> The output of lspci would also be nice, it will provide valuable info about the graphics hardware you have. 			 		

Nevermind, I figured it out. The output of lspci run from my working 10.10 install (I assume this doesn't matter if it's giving info about my hardware) is as follows:

jeff@jeff-FX400:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV45 [GeForce 6800 GTO] (rev a2)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 01)
07:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
07:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
07:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
07:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
jeff@jeff-FX400:~$

---

### Post by mikewhatever on 2011-07-14
To logout, hit ctrl+alt+t to pull up a terminal window, then type the following and hit enter:
```
sudo service gdm restart
```

If everything goes according to plan, you should find yourself at the login screen in a few seconds.

Edit: Thanks for the output. You have an Nvidia GeForce 6800 GTO card. Don't think that's going to work with the new Unity interface. As I've mentioned earlier, try the Classic option with no effects.

---

### Post by quantumcop on 2011-07-15
Using the command

```
sudo service gdm restart
```

did successfully log me out, but as I said, I'm running a live session here, so all that did was to bring me back to the "Try Ubuntu/Install Ubuntu" screen.

I'd like to avoid actually installing 11.04 on my machine, as it doesn't seem to work, and I'm afraid I'll not be able to get back to a clean 10.10 install. If I can get 11.04 to work properly under a live session, then I'll consider actually installing.

---

### Post by mikewhatever on 2011-07-15
Hm..., do you have something like 'End Session' in the Power button drip down menu? If so, then that's the equivalent of logout.

---

### Post by quantumcop on 2011-07-15
> Hm..., do you have something like 'End Session' in the Power button drip down menu?

No, it doesn't appear so. The only options in that menu are Suspend, Hibernate, Restart, Shut Down, and System Settings, as far as I can tell. It's a little hard to read.

---

### Post by Blasphemist on 2011-07-15
The live cd thinks you can run unity since it displayed it. Even if it did it with the cool psychedelic affect. It runs a test to see if unity should work. [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

The live cd is likely using the nouveau driver and you'll see from the link it recommends the proprietary driver or the experimental open source driver. I recommend you search for your gpu in these forums in particular in this thread. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I got 11 hits in that sticky thread on your card. The OP that runs that thread is real good with video and he has likely already worked through issues that would help you. The first few posts are his updated troubleshooting posts.

---

