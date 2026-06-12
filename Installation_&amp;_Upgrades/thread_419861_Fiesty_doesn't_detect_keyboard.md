---
title: "Fiesty doesn't detect keyboard"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by GeoPirate on 2007-04-23
OK I've been using edgy the last several months.  I downloaded and installed fiesty, neither the live CD or the installed version detects my keyboard.  I have a gateway MX6448 Laptop.  Any suggestions?

---

### Post by Big Ed on 2007-04-23
This may be a really stupid suggestion, but here it is anyway:

There have been a number of people reporting problems with keyboards and mice after upgrading to Feisty.  Mostly, usb ones work and ps/2 ones don't.  So reboot and go into the bios screen, disable usb (temporarily) and see if that fixes it.

I donb't know if it will help you, but it worked for me.  Mind you, I'm using a desktop rather than a laptop.  Once I found that to work, I went back into the bios and turned usb back on and disabled only the line for usb keyboard support.  Now my ps/2 keyboard and usb mouse work fine.  However, ymmv.

HTH,
Ed

---

### Post by werewolf on 2007-04-25
Actually, it's not Feisty that's not detecting your keyboard, it's the kernal supplied with Feisty.  Both Ubuntu and Kubuntu are using 2.6.20-15.  When I boot in to Ubuntu Feisty using 2.6.17-10 my keyboard works fine.

Otherwise, I get to the login screen and I'm dead in the water.  Can't login.

The LIve CD's of both Ubunt and Xubuntu do not detect my keyboard.

Has there been a fix yet?  How would I find out?

Thanks

---

### Post by Big Ed on 2007-04-25
> **werewolf said:**
> Actually, it's not Feisty that's not detecting your keyboard, it's the kernal supplied with Feisty.  Both Ubuntu and Kubuntu are using 2.6.20-15.  When I boot in to Ubuntu Feisty using 2.6.17-10 my keyboard works fine.

Otherwise, I get to the login screen and I'm dead in the water.  Can't login.

The LIve CD's of both Ubunt and Kubuntu do not detect my keyboard.

Has there been a fix yet?  How would I find out?

Thanks

Do you have a usb keyboard?  Did you try disabling usb in the bios?  Is your mouse usb or ps2?  Does it work?

Ed

---

### Post by werewolf on 2007-04-26
Thank you *so* much for replying!!!

I have a PS2 keyboard and a USB mouse.  The mouse works fine.

I have enabled and disabled the USB keyboard in the BIOS with no effect.

I tried booting into the recovery mode of kernel (generic) 2.6.20-15, but the keyboard still does not work.

It is definitely something in the new kernel.  I am typing this in Feisty using kernel 2.6.17-10.

Even the LiveCD for XUbuntu exhibits this problem.  I've been trying to get the live CD for KUbuntu, but the servers are down.

---

### Post by Big Ed on 2007-04-26
> **werewolf said:**
> Thank you *so* much for replying!!!

I have a PS2 keyboard and a USB mouse.  The mouse works fine.

I have enabled and disabled the USB keyboard in the BIOS with no effect.


Hmm, try turning off usb altogether and see what that does for your keyboard.  It'll kill the mouse temporarily, but it will give an indication of where the trouble is.

This site will help you get around the Gnome gui without a mouse so you can reboot gracefully:

[http://www.gnome.org/learn/users-guide/latest/keyboard-skills.html](http://www.gnome.org/learn/users-guide/latest/keyboard-skills.html)

Ed

---

### Post by werewolf on 2007-04-26
:) actually tried that already.  Keyboard still didn't work and the mouse, of course, didn't either, so there wasn't anyway at all to navigate the OS.  That was amusing.

I noticed that the latest stable kernel for Linux is now 2.6.21.

Is it possible to upgrade just the linux kernel, or must it be compiled into the Ubuntu release?

---

### Post by Big Ed on 2007-04-26
> **werewolf said:**
> :) actually tried that already.  Keyboard still didn't work and the mouse, of course, didn't either, so there wasn't anyway at all to navigate the OS.  That was amusing.

I noticed that the latest stable kernel for Linux is now 2.6.21.

Is it possible to upgrade just the linux kernel, or must it be compiled into the Ubuntu release?

You could download and compile a v2.6.21 kernel from source.  Not sure if it will help or not.

Did a quick google of the linux kernel mailing list and found this:

>>>>>>>>
Date	Sat, 3 Mar 2007 15:14:24 +0000
From	Ash Milsted <>
Subject	2.6.21-rc2 regression vs. 2.6.20: AT keyboard only works with pci=noacpi

With 2.6.21-rc2-git1 I have a problem with my ps/2 port keyboard - it only works
with one of the following on the command-line:
 - nolapic
 - irqfixup
 - pci=noacpi
Otherwise it gets stuck with the numlock on.

Just checked 2.6.21-rc2-mm1, still has the problem.
Also, acpi=noirq fixes it too.
To clarify, the problem is that my ps/2 port keyboard is completely frozen
on boot - usually it gets activated when udev probes for hardware (my kernel
config is highly modular). It worked fine with 2.6.20 and earlier with acpi 
taking care of interrupt routing.
>>>>>>>>>>

This is from more than one page but all the same thread.  You can read the whole thing here:

[http://lkml.org/lkml/2007/3/3/68](http://lkml.org/lkml/2007/3/3/68)

Before recompiling the kernel, try adding (one at a time) the above lines to your grub bootloader.

Ed

---

### Post by werewolf on 2007-04-26
Thanks so much, will give it a try....


.... and hello from 2.6.20-15 :)

I added pci=noacpi and everything seems to be working correctly.

Thank you very much for your help.  It was really appreciated.

---

### Post by werewolf on 2007-04-27
so, I am curious...

How can I install from a live CD if my keyboard isn't going to work?  Would like to try installing Kubuntu Feisty

---

### Post by Big Ed on 2007-04-27
That's a good question.  Can you break into the boot cycle on a Live Cd the same way you do it when booting from the hard drive?  I haven't tried that myself.

Ed

---

### Post by werewolf on 2007-04-28
well, turns out I'm not as ignorant as I supposed.  Was able to get the Live CD to work and then, after installing Kubuntu, fix my Grub command.  So...well...

Hmm, this is nice :)

Sorry, didn't see your post.  You can modify the boot command on the Live CD menu.  I just added in the magic words pci=noacpi and it booted with keyboard support.  I then installed Kubuntu and changed to boot commands in the grub loader.

---

