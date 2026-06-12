---
title: "Major video problem with 16.04, Gigabyte mobo w/integraed Nvidia 6100"
date: 2016-06-14
forum: Installation &amp; Upgrades
---

### Post by brucew on 2016-06-14
I&#8217;m installing 16.04 on a friend&#8217;s PC and having terrible video problems.

It&#8217;s an ancient (2007 or 2008?) Gigabyte M61PME-S2P (rev. 1.0) with integrated Nvidia GeForce 6100 GPU. [Specs here]("http://www.gigabyte.de/products/product-page.aspx?pid=3009#sp").  BIOS flashed to the most current rev.  This is a fresh install on a new out-of-the-box hard disk.

The installer ran just fine, as do the splash screen and the login screen.  

Problems begin very quickly at the Unity desktop.  It takes less than 10 seconds before the screen freezes in a stairstep pattern.  It locks the computer so completely, even the front panel off button and reboot buttons don&#8217;t work.  Only a full disconnection from the mains works.  (Always works!)

I just checked, and running Ubuntu from the DVD also fails in the same manner at the desktop. Yes, I should have done this first.  (Live and learn, but ever since Breezy, I&#8217;ve never had a problem.  It Just Plain Works.)

Near as I can tell from looking around here, I need to install the nvidia-304 driver from the graphics-drivers ppa.

First, does this seem like the correct step?

Second, if so, how do I do this without going to the Unity desktop?  

Again, since it usually Just Plain Works, I've never had to mess around with things like this.  So while I've been a happy user since Breezy, I know little beyond the desktop.

---

### Post by kansasnoob on 2016-06-14
Were you able to open the Additional Drivers UI and check for proprietary drivers?

The Unity DE is quite resource hungry so you may not be able to, in which case you could see what happens from terminal:

```
sudo apt-get install nvidia-current -s
```

The -s at the end means "simulate" so nothing will actually change but just give you a chance to see what will happen. If it looks like it won't blow anything up you could run the same command sans the -s and then reboot.

You may need to access terminal using F-1 from the login screen or from Recovery mode.

---

### Post by brucew on 2016-06-15
> **kansasnoob said:**
> Were you able to open the Additional Drivers UI and check for proprietary drivers?

Nope.  Won't stay running long enough to get the mouse to the System Settings dialog.

> **kansasnoob said:**
> < snip >  You may need to access terminal using F-1 from the login screen or from Recovery mode.

Thanks.  This is the sort of stuff I need.  I'll give it whirl when I get home from work this afternoon--about 12 hours from now--then report back.

---

### Post by X-RED_Tech on 2016-06-15
If you're able to, you should try the recommended nvidia drivers for that chip, the "LTS" legacy 304 (304.131).

```
sudo apt update
sudo apt install nvidia-304
```

If not you must edit Grub, add nomodeset and then you should be able to do it graphically, in VESA mode (low graphics): Settings -> Software Porperties -> Additional drivers tab.

---

### Post by brucew on 2016-06-15
Getting the nvidia-304 driver installed did the trick.

Thanks to you both for setting me down the right path.  I figured that would do it, but didn't know how to do it before the GUI loads.

---

