---
title: "Cant start ubuntuLive (with picture documentation)"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by Tag_yer_dead on 2007-02-17
Hi everyone
My specs are 3.88 GHz intel, abit mobo, 250 GB hd, 4 gb ram, dual radien x850xts.....

I have burnt 10+ cds, using differnt drives, differnt downloads, differnt cd types, and a DVD, but i get the same problem each time. (i verified that the disc wasnt corrupt as well)

When I boot from the CD - It begins with the log in screen, all fine an dandy, i get the normal boot screen, and then when it gets to the loading screen, it begins like this
[[IMG]http://img171.imageshack.us/img171/5453/ubuntugoodzz4.th.jpg[/IMG]](http://img171.imageshack.us/my.php?image=ubuntugoodzz4.jpg)

But when it gets about 9/10ths of the way done, everytime the Ubuntu logo goes white and i get weird blue and green lines across my screen.
[[IMG]http://img253.imageshack.us/img253/2744/ubuntubadnl9.th.jpg[/IMG]](http://img253.imageshack.us/my.php?image=ubuntubadnl9.jpg)

After that, it will not load any more, i left it for up to an hour with no results....

Please someone help!!!!!

---

### Post by mikewhatever on 2007-02-17
What is the graphic card?

---

### Post by Tag_yer_dead on 2007-02-17
2 radeon x850xt

---

### Post by DivineOmega on 2007-02-17
Based on experience trying to get Ubuntu installed on a friend's PC, I can quite confidently say this is a graphics driver problem. The ATI graphics driver is not 100% reliable at detecting all ATI cards, therefore it is likely this is the problem in your case.

To get into the live CD successfully you will need to change your driver setting from the predetected 'ati' or 'radeon' driver setting to the generic 'vesa' driver in xorg.conf file. The VESA driver is supported by 99.99% of graphics cards AFAIK, and it has yet to fail me.

The next release of Ubuntu (Feisty Fawn) in April has a permanent solution to this - i.e. the graphics driver goes to vesa automatically if a failure is detected.

Have you tried installing from the Alternate CD as of yet? If not, try that first. Then come back if you are still having the problem and me or another forum member will guide you through changing the driver from 'ati' or 'radeon' to 'vesa' on the live cd session.

---

### Post by Tag_yer_dead on 2007-02-17
thank you for the answer, can ne one go into more depth on how to do that?

---

### Post by towsonu2003 on 2007-02-17
I'll be honest: I'd try other liveCDs at this point. anyway...

this won't be any depth you'd want but... well :)

try to
1. use the alternate installation CD which does not use graphics during installation. So if *it* cannot boot correctly, you'll know the problem is not about your graphics card

2. let it install if you'd like to
2.a. I think the installation doesn't ask you about your graphics card. if it asks, choose "ati" as your driver
2.b. it will reboot. See if it can launch X...
2.c. if it cannot launch X:

2.c.i. login using your username and passwd to the console (white on black ugly screen)
2.c.ii. type: ```
less /var/log/Xorg.0.log
``` and have a look at that file using page-up and page-down. Try to make sense of the errors... Write them down if necessary... type q (or ctrl+c) to leave that file
2.c.iii.  type: ```
sudo dpkg-reconfigure xserver-xorg
```
and when it asks, choose your driver for your card as "vesa". Also, if you can find the horizontal sync and vertical refresh rates of your monitor, they will be very handy (don't put wrong numbers or you'll break the monitor itself). 
2.c.iiii. when you're done and the program exists, try launching X with ```
startx
```

this was the easy part. Now you'll google to find the proper driver for your card. try the proprietary driver (at [http://ati.amd.com](http://ati.amd.com)) but in order to install it, search this forum for a howto...

sorry, wasn't too helpful ... I wish manufacturers cooperated with driver writers so things would go smoothly for all of us...

---

### Post by eapache on 2007-02-17
I had the same problem with a slightly different radeon card, and got the following solution from aberry555:

> This is a big old problem with ATI graphics on the Ubuntu install, though I didn't think it went as far back as that card basically the driver called "ATI" that Ubuntu defaults to doesn't usually work by itself, even though other distros do it out the box. It is, though, fairly easy to get working again.

On the first boot screen (the one giving you boot options) press F6 to edit the boot options line.

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting.

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device".

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better ).

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum!

It's the same bug pointed out by divineomega. I wouldn't suggest installing from alternate cd because you'll just have the same problem booting from your hard-drive once installed. Follow the above steps, and it will work fine.

---

### Post by Tag_yer_dead on 2007-02-17
Well neither of those helped..................
But something is differnt than how he said......

The section said
Section "InputDevice"
Driver "wacom"
Indentifier "stylus"
Option "device"  "/dev/wacom"

I tried 4 things -
1.   changing driver only to radeon
2.   changing driver and device to radeon and /dev/radeon
3.  changing driver to vesa
4.  changing device and driver to vesa

I get this error
[[IMG]http://img178.imageshack.us/img178/4482/1002139tm2.th.jpg[/IMG]](http://img178.imageshack.us/my.php?image=1002139tm2.jpg)

Any help would be much appreciated

---

### Post by DivineOmega on 2007-02-17
> **Tag_yer_dead said:**
> Well neither of those helped..................
But something is differnt than how he said......

The section said
Section "InputDevice"
Driver "wacom"
Indentifier "stylus"
Option "device"  "/dev/wacom"

I tried 4 things -
1.   changing driver only to radeon
2.   changing driver and device to radeon and /dev/radeon
3.  changing driver to vesa
4.  changing device and driver to vesa

I get this error
[[IMG]http://img178.imageshack.us/img178/4482/1002139tm2.th.jpg[/IMG]](http://img178.imageshack.us/my.php?image=1002139tm2.jpg)

Any help would be much appreciated

You've done the right thing but to the wrong section. If you scroll down further when viewing the xorg.conf file you will find a section than already has the driver set to ATI, this is the one you want to change.

1st - Undo the changes to the wacom if you have not already.
2nd - Find the section in xorg.conf where the driver is already set to "ATI", then continue with the previous instructions you were following modifying that section.

---

### Post by towsonu2003 on 2007-02-17
```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
        Driver          "ati"
        Option          "AGPMode"       "8"
        Option          "AGPFastWrite"  "on"
        Option          "EnablePageFlip" "true"
        BusID           "PCI:1:5:0"
EndSection

```

as they said, you did the right thing at the wrong section :) above is how the correct section in my xorg.conf looks like (hopefully, this will make it easier for you to identify the right section)

---

