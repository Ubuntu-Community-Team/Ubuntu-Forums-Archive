---
title: "Installing Kubuntu onto VMWare 4.0.5.6030?"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by foober on 2005-04-11
Anyone know how to install on VMWare 4.0.5.6030?

I get a screen with a window entitled "Preparing for live session".  Inside the box are the words "Loading modules...", and the bar always stops at 5%.

If I Alt-F3, I see the last module loaded is isofs.  If I Alt-F4, I see the text of the log scroll by.  The last entry talks about redrawing the screen, at which point the screen clears, and the progress bar returns.

If I Alt-F1 at this point, the screen with the progress bar says 'Segmentation fault' at the bottom of the screen.

I've tried starting the kernel with various things as listed in the startup screens of the live CD, but no joy.

So, anyone got any advice?

-Ken

---

### Post by lao_V on 2005-04-11
Ken,

What is the host operating system you're using? How have you created the Virtual Machine?

---

### Post by foober on 2005-04-11
Whoops!

The host is Windows XP SP2 (Athlon 2000 xp, 1GB ram, 750GB disk, ATI 9800 video), and I created the virtual machine as a 512MB machine using bridged networking.


I think that's all the relevant stuff.

-Ken

---

### Post by lao_V on 2005-04-11
What type of HD did you create? Bear in mind that kubuntu will only work with IDE disks.

---

### Post by foober on 2005-04-11
I do have an IDE drive configured.

Just 5% into the "Loading Modules...", and it always hangs.  This is on both the install CD and the live CD too.  This is despite me trying quite a few of the loading params described in the boot of the CDs.

It's a bit sad, really, as I've heard such good things about ubuntu.

-Ken

---

### Post by lao_V on 2005-04-12
You have a number of options still:

[list=1]
[*]If you are able to then try upgrading your VMWare to 4.5   
[*]Try using other VM software, eg, Virtual PC 2004   
[*]If all fails, you can always try installing directly on your hard drive! 
[/list]

---

