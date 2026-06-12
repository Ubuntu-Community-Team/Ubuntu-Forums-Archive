---
title: "[SOLUTION]Graphical Desktop for Ubuntu 8.10 with NEW ThinkPads (T400/T500/W500)"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by inf32n0 on 2008-11-03
For those who don't have a graphical desktop with Ubuntu 8.10 that have the new Lenovo thinkpads (T400/T500/W500/...) with switchable graphics

The problem is, since the new thinkpads have switchable graphics, ubuntu is confused with which graphics card to use and appearently can't locate the appropriate one.

after reading the message carefully it says that no PCI Express display found or something like that, don't remember the message exactly

to solve this problem:

SOLUTION: Go into BIOS and change your display settings to:

Default Primary Video Device = PCI Express
Boot Display Device = ThinPad LCD
Graphics Device = Discrete Graphics
OS Detection for Switchable Graphics = Disabled

This worked for me

The main thing that you need to do is change the 
Graphics Device = Discrete Graphics

You don't necessarily have to change the other things, It worked for me after just changing the Graphics Device and keeping the others the same.

Hope this works for the rest of you with the same problems
enjoy

---

### Post by kevinality on 2008-11-05
You can also choose to graphics mode=integrated to use intel's chipset. This will give you much weaker but still acceptable performance. If you don't need the extra performance this will give you exceptional battery life. With this setup, I've gone over 5hrs with a 9cell battery.

---

### Post by festerwim on 2008-11-13
Thank you for posting this!

---

### Post by bebox on 2008-11-16
Thank you very much!

---

### Post by rcmn on 2008-12-04
Hello. I was playing with the switchable options .I was trying to see how it was acting .I tryied to find a pattern , so maybe I could take advantage of the 2 video cards with a minimal impact in my user experience.
I noticed i was able to load the ATI driver if i set the BIOS like this:

Default Primary Video Device = PCI Express
Boot Display Device = ThinPad LCD
Graphics Device = Discrete Graphics
OS Detection for Switchable Graphics = **enable**

then I would change my xorg.conf to INTEL then reboot or restart X. And surprisingly it would work .Looking at the Bios after i would find :

Default Primary Video Device = PCI Express
Boot Display Device = ThinPad LCD
Graphics Device = internal or switchable
OS Detection for Switchable Graphics = **enable**

So upon that observation I was wondering if we could get something out of it with a reasonable amount of effort for an experienced develloper? 

I Google it but couldn't find much. 

I read somewhere in the forum that using INTEL card let u use more than 5 hours with a 6 Li battery. I know i have only 3 and less with the ATI.

So Looking at that aspect and the point of having a laptop. A tool that would give the user a way to easily switch video card could be a pretty nice feature. 

Did anyone try ? Have u seen anybody posting/writing anything about it ? Is it even doable ?

---

### Post by gatman3 on 2008-12-06
Interesting.  That makes one think that enabling "OS detection for switchable graphics" actually means that both graphics controllers are enabled.  That would explain why you could select one or the other by just changing the driver setting in xorg.conf.  So, if the switchable graphics is enabled in the BIOS, and the "intel" driver is used, does it burn just a little power as if only the intel controller is enabled, or does it burn lots of power as if both graphics controllers are enabled?

---

### Post by antmo on 2008-12-08
i don't have ubuntu installed at the moment, but maybe you could use intel's power utility software to monitor and test power usage with and without both enabled...  i'd be very interested to know, since it would be monumental if it would be possible to switch graphics controllers by simply restarting x, without them both eating power at once...

mjb

---

### Post by gatman3 on 2008-12-09
I attempted to reproduce the switchable graphics behavior that rcmn reported but had no success.

I did observe the phenomena rcmn reported where the BIOS setting for "Discrete" would get changed to "Switchable" after booting up with "OS detection" = enabled and then restarting X with the intel driver.  But that's as far as it goes - only the setting gets changed, but I still have no success dynamically loading either video driver.  For me, whenever I have the graphics device set to "switchable" I can load neither driver, and all I get is just a text login prompt.  The OS detection doesn't seem to matter; with the graphics device set to "discrete" I can load the fglrx driver, and with the graphics device set to "integrated" I can load the intel driver.  But I haven't found any BIOS settings where I can load either driver by restarting X.  Bummer.

By the way, I believe the power consumption is reported by ACPI somewhere in /proc/acpi/battery/BAT0/state (unplug the power cord and cat this file a few times and you can watch it update the power consumption calculation).  It's also reported by the "guidance power manager" which, at least for KDE, is the battery icon in the task bar (it probably uses the same ACPI data, just a hunch...)  You need to let it sit for a few minutes at a steady state, though, because it seems to average over at least a minute or two.  With just the intel graphics running, I average around 15 to 19 watts on battery, depending on CPU load and screen brightness setting.  That makes sense, because the battery is listed as 84 Wh, so 84/16 or 84/17 is around 5 hours of battery life.  With the fglrx driver running it reports around 22 to 27 watts on battery, so around 3 1/2 hours of battery life.  The radeon driver is horrible, though, and runs around 35 watts.  The proprietary fglrx driver obviously does a better job of power management.

---

### Post by rcmn on 2008-12-10
Ok Mea Culpa. I did miss a step in the confusion of trying different things .
But it does work for me the way I wrote it.Actually I'm writing this after trying it for the 2nd time.
Here how it happen.

So let say I was working on the INTEL driver.

-Before rebooting change the xorg to ATI.
-Set the Bios like this:
Default Primary Video Device = PCI Express
Boot Display Device = ThinPad LCD
Graphics Device = Discrete Graphics
OS Detection for Switchable Graphics = enable

-let X load the ATI driver.
-change xorg to intel driver
-restart X ,X will failed to load the INTEL driver.(Guessing it change to switchable at that point)
-reboot
-X will load the INTEL driver.

I tryied to restart X 2 or 3 time without rebooting but INTEL failed.A reboot is needed. Since X set the Bios to switchable then at the reboot the intel card become available.

---

### Post by gatman3 on 2008-12-12
rcmn - Does it work the other way (changing the driver in xorg.conf from intel to ATI and rebooting) ?  Or does it only work going from ATI to intel?

---

### Post by rcmn on 2008-12-13
it work only from ATI to INTEL. unfortunatly.

---

### Post by gatman3 on 2008-12-13
Oh well, thanks for sharing your experimentation anyway.  The reality is that the chipset supports OS switchable graphics, but we just don't know how to do it.  Intel is pretty linux-friendly, so my guess is that someone with the appropriate credentials and motivation could probably get the necessary spec and implement it.

---

### Post by markdude on 2009-05-09
My lenovo t500 has only this two items under config->graphics on bios 
 Default Primary Video Device => PCI Express
Boot Display Device => ThinkPad LCD
 and missing this two
Graphics Device => (change it) Discrete Graphics
OS Detection for Switchable Graphics => Disabled
 I updated bios to latest version and searched again all over bios but did not found “Graphics device”. any idea?

---

### Post by gatman3 on 2009-05-10
Are you sure your machine has switchable graphics?  I think that switchable graphics in the T500 is an option and is not found in all versions.

If you don't know your model number, try:

```
> dmesg | grep Lenovo
[    9.919593] thinkpad_acpi: Lenovo ThinkPad W500, model 406226U

```

Note that it reports my model as 406226U (I have a W500), but it is typically listed in the literature as model 4062.  In any case, you can Google on it either way and get some info on which graphics it includes.

---

### Post by markdude on 2009-05-11
gatman, your'e right. I spoked with Lenovo support today and not all T500 has this option on bios.
However, I solved the problem by pressing F4 on installtion menu on ubuntu, and selected "safe graphics mode".
This solved the installtion problem, now I need to get the internet working, but that's another story. :)

---

