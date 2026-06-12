---
title: "fglrx driver issue with 10.10"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Gualdim on 2010-10-10
Hello,

I am able to get fglrx driver to work with 10.10, but as soon as I change my displays settings to have my good old dual screen setup, I get a blank screen when I reboot the system.

Any thoughts?

Thank you!

---

### Post by skutter2k on 2010-10-10
I think I have a similar problem. I upgraded and had an error about not being able to install fglrx. Now when I boot up I have a text based logo then a purple screen. You can hear it log in but see nothing but the pruple background :-(

It's a Dell Studio with ATI 4570 graphics.

Help!

---

### Post by Xarver on 2010-10-10
You have to put in the dual monitor when ubuntu is started.
This is because when you boot your computer your BIOS doesn't know which monitor to use is the simple explanation.
A simple fix is to again just plug in the monitor when Ubuntu is started.

---

### Post by cdr. on 2010-10-10
This is a longstanding problem that people have been having throughout the 10.10 beta. The problem is likely some sort of incompatibility with xserver 1.9.

I saw someone filed a bug [here]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/657588"), but you would think there'd have been a bug filed already.

> **skutter2k said:**
> I think I have a similar problem. I upgraded  and had an error about not being able to install fglrx. Now when I boot  up I have a text based logo then a purple screen. You can hear it log in  but see nothing but the pruple background :sad:

It's a Dell Studio with nVidia graphics.

Help!

fglrx is for ATI... fglrx shouldn't even let you enable it at all if your card is nVidia.

> **Xarver said:**
> You have to put in the dual monitor when ubuntu is started.
This is because when you boot your computer your BIOS doesn't know which monitor to use is the simple explanation.
A simple fix is to again just plug in the monitor when Ubuntu is started.

BIOS? I think you're in the wrong thread...

---

### Post by Xarver on 2010-10-10
> **cdr. said:**
> This is a longstanding problem that people have been having throughout the 10.10 beta. The problem is likely some sort of incompatibility with xserver 1.9.

I saw someone filed a bug [here]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/657588"), but you would think there'd have been a bug filed already.

Strange. I thought this was a computer thing because the same thing happened with windows.

---

### Post by ronparent on 2010-10-10
It's all a blur now. But when fglrx was first released for Maverick,I had a fit trying to keep my screen settings. In prior distro's when fglrx was installed the ATI Catalyst Control Center was where I set my display settings and the Preference>Monitors setting were out of play. Now I found that I had to use the Monitors control to set and retain my monitor resolutions. Now everything is fine? (I think)

---

### Post by skutter2k on 2010-10-10
> **cdr. said:**
> 

fglrx is for ATI... fglrx shouldn't even let you enable it at all if your card is nVidia.
.

My mistake, that was my old laptop. It's an ATI 4570.

---

### Post by Gualdim on 2010-10-10
Well,

I tried the "pull the plug" work around, and even if the system boot normally, multi-display is out of reach... The monitors control does not work either: I tried to set multidisplay in it, with no success. (the log-off then loggon trick: no effect)

What's going on???

This is a thing where Windows 7 is faaaaaaar better than Ubuntu... with 7, it is just a matter of plug and play...

---

### Post by jetpeach on 2010-10-13
I didn't see this thread and posted my own, but it is probably the exact same problem.

[http://ubuntuforums.org/showthread.php?t=1596039&highlight=fglrx](http://ubuntuforums.org/showthread.php?t=1596039&highlight=fglrx)

First, I'd like to eliminate the possibility that it is related to KDE and that the bug occurs on Gnome as well - Gualdim, are you running Ubuntu or Kubuntu? If Ubuntu, then I know it's not a KDE issue... (although I should say, KDE developers are upset right now with the fglrx driver and saying the bugs are with the driver, so what I mean is to find whether it's specific to KDE and fglrx interactions...)

My guess is, since the fglrx driver used in Meerkat is an early release, made especially to work with XServer 1.9, which Meerkat is using, that ATI/AMD has just not done a could job of fixing bugs yet.

It's unfortunate, that Linux/Ubuntu get blamed for this type of thing- it's not as if it's because the product itself isn't superior, but that when vendors such as AMD deliver poor or inadequate drivers....

---

### Post by mixmastamyk on 2010-11-23
Same here, having these two problems:
[LIST=1]
[*] dual monitor setup not saved across restarts (of X)
[*] if second monitor is plugged in at boot, crash with power cycle needed. :(
[/LIST]
The second has already corrupted my fat drive once.  :mad:

To get around the issues, I unplug the second monitor when booting then plug it in when the login screen shows.  When I log in I have a script added to the "Startup Applications" control panel that runs this command so I don't have to configure the damn settings every boot:

```
xrandr --output LVDS --primary --auto \
    --output DFP1 --mode 1600x1200 --rotate left --right-of LVDS

```
Hope this helps someone.  Wish I knew a way of fixing it for good.

Luckily sleep works on this laptop so I don't boot often anymore.

BTW, what kind of clowns at ati/amd write drivers and don't test them with dual monitors in 2010?

---

