---
title: "Samsung 9 series fresh install"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by LordVeovis on 2011-04-26
I have a Samsung NP900X3A.  Fresh install running into some issues.  First wireless was not working and the Broadcom driver I needed was labeled as blacklisted.  Since then it has been successfully installed, just took a few restarts while  trying to get other hardware to function properly.

Currently I need help with the Intel drivers.  They are not enabled by default it seems, and I am not finding a way to enable it.  Secondly the touch-pad is multi-touch capable, I need to find out what I need to do to get drivers for it as I have never worked with a multi-touch pad before.  The Samsung also has a webcam, I may be able to get this working on my own, but as I normally don't use a webcam, in the past I have skipped even trying.  Any tips that may make that setup painless too appreciated.

~Thanks

New stuff:

Upgraded the kernel to 2.6.35.25  which enabled me to have a better resolution but still did not enable the Intel drivers.  Also broke the Broadcom driver and I am now without wireless.

---

### Post by Lateralis on 2011-04-26
Intel drivers are built directly into the Linux kernel as kernel modules.  They shouldn't need "enabling".  What piece of hardware are you having trouble with?  Is it sound?  

System -> Preferences -> Mouse Preferences.  In this GUI window you should see a tab called "Touchpad."  In there you can enable and disable various things, including edge scrolling (which hilariously my Windows doesn't allow being enabled) and two finger scrolling.  There may be other options for you (I'm in Lucid, not Maverick).  

Webcam.  Make sure you turn your webcam on.  On my laptop there is a Function button for doing just that.  When I first got the laptop I was trying to use it and was failing, until I discovered a little movie camera like object on one of the 'F' keys.  Hitting that with the function key turned on the webcam (a small, blue LED light turned on next to the camera) and then the webcam was detected.  To see if it works you could use something like 'Cheese'

```

sudo aptitude install cheese

``` 

If you don't see anything with that, or no webcam is detected, then let us know and we can try and help (although you'll be better off making a specific thread to deal with that specific issue).

---

### Post by LordVeovis on 2011-04-26
Sound works great!  The biggest issue is with the video drivers.  It is setting them as VESA.  I wanted the Intel ones for 3D support.  Currently I cant enable Compiz because of it.  Broadcom wireless now non-functional since the kernel upgrade I did.

Main question with the touchpad is about settings.  Is the mouse settings the only control I have over the touchpad?  For example, in Windows there are many more options to set such as if i want right click to be a 2 finger press or if I want to enable some kinds of mouse gestures among other things.

---

### Post by Lateralis on 2011-04-26
Hmmmm... never known any issues with Intel graphics!  What specifically is the hardware?  

```

sudo lshw -C display

```

The output will tell us the product and the driver which is currently being used. 

As for broadcom, there are probably hundreds of threads on these boards dedicated solely to broadcom wireless cards.  I personally can't help you with that specific issue as I steer well clear of these particular cards.  But a good search of the forum might lead you somewhere.  There may even be a sticky dedicated to wireless cards somewhere... 

As for your mouse, I fear I'm going to be pretty useless here too!  Have a look around in your mouse preferences.  I have few options in mine as I'm in 10.04.  I believe 10.10 and Natty have more options due to recent updates.

Additional: On the mouse, I've just done some googling and found this: [http://ihaveapc.com/2011/01/how-to-configure-mousetracksticktouchpad-in-linux-mint-ubuntu/]("http://ihaveapc.com/2011/01/how-to-configure-mousetracksticktouchpad-in-linux-mint-ubuntu/").  I don't know how useful it will prove, but the package is in the main repos.  Try installing that - you might have some more options not found in the default settings menu.

---

### Post by LordVeovis on 2011-04-26
Sorry for the long delay.

```

*-display UNCLAIMED     
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-c03fffff memory:b0000000-bfffffff(prefetchable) ioport:3000(size=64)

```

Was unfamiliar with that command, thanks.  This is what i get before i did the kernel update.  I have fresh installed again since i had tried a whole bunch of stuff and didnt want it to effect the system.

According to the spec sheet it has: Intel HD Graphics 3000

---

### Post by b16a2smith on 2011-04-26
I dont see the grub menu after install. any luck helping me out? I just used the alternative daily because the current doesnt work.

---

### Post by LordVeovis on 2011-04-27
Was able to get everything working with fresh install of 11.04 (still beta) so this means it is possible...  Was hoping to get this with an LTS release.  I think most of the issue is in the Sandy Bridge chip in there, alot of stuff is integrated and doesn't have the support on Lucid it seems.  Any suggestions?

---

### Post by Lateralis on 2011-04-27
@b16a2smith

If you only have Ubuntu installed, then by default Grub 2 does not display a menu and boots directly to the first listed kernel.  To have the menu displayed, hold down the shift key.  


@LordVeovis

If everything works fine in the Natty beta, then I'd suggest staying with that to be honest.  In fact, Natty will be released proper tomorrow and is supported right up until October 2012.  If everything works as you expect it to, and you can see no obvious errors or problems, then I see no reason to switch to Lucid.  You can also continue to upgrade your distro as new ones come out and unless you have lots of customisations the upgrade should be fine.  (I have upgraded from Inteprid all the way to Maverick on my home desktop computer without any problems or issues at all.)  If you do want to bomb proof your computer from upgrade issues then there are ways you can do that, but that is a totally separate discussion!

---

### Post by b16a2smith on 2011-04-28
> **Lateralis said:**
> @b16a2smith

If you only have Ubuntu installed, then by default Grub 2 does not display a menu and boots directly to the first listed kernel.  To have the menu displayed, hold down the shift key.  


@LordVeovis

If everything works fine in the Natty beta, then I'd suggest staying with that to be honest.  In fact, Natty will be released proper tomorrow and is supported right up until October 2012.  If everything works as you expect it to, and you can see no obvious errors or problems, then I see no reason to switch to Lucid.  You can also continue to upgrade your distro as new ones come out and unless you have lots of customisations the upgrade should be fine.  (I have upgraded from Inteprid all the way to Maverick on my home desktop computer without any problems or issues at all.)  If you do want to bomb proof your computer from upgrade issues then there are ways you can do that, but that is a totally separate discussion!

I was/am Dual Booting, it would not stick, but that was fixed by using Maverick to install then distro upgrade.

Cheers!

---

