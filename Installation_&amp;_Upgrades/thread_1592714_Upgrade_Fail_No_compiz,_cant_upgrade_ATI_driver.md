---
title: "Upgrade Fail: No compiz, cant upgrade ATI driver"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Ant0n on 2010-10-10
Greetings :)

After upgrading, I found that Compiz would not detect my graphics card, and after downloading the latest ATI driver here's what happened:
(Using a Radeon 4770 btw)

> anton@Computo:~$ cd ~/Desktop
anton@Computo:~/Desktop$ sudo bash ./ati-driver-installer-10-9-x86.x86_64.run
[sudo] password for anton: 
Created directory fglrx-install.xr8aPP
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.771.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-22-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.xr8aPP
anton@Computo:~/Desktop$ --iscurrentdistro
--iscurrentdistro: command not found

Is the kernel misnamed or something? Quite bizarre...
I always tell myself to wait two weeks to upgrade to avoid these headaches but I can't resist the new shiny :P

---

### Post by mionescu on 2010-10-10
Did you try to install the drivers using "Hardware drivers" from the system menu? I think this should be your best bet to install correctly the ATI drivers. Ati did not upgrade their drivers on their webpage to support  10.10 yet and that's why you see that error message.

---

### Post by Ant0n on 2010-10-10
Ah, you think so? My understanding was that upgrading drivers via the hardware-drivers tool after doing them manually tends to cause big headaches. I'll give it a go though :)

---

### Post by Ant0n on 2010-10-10
Nope, it didn't find anything... Side note, Hardware Drives has been changed to 'Additional Drivers'. Guess I'll have to wait unto ATI sorts themselves out, oh dear... Thanks for the help bud :)

---

### Post by mionescu on 2010-10-10
Sorry to hear that. You are welcome and good luck.

---

### Post by alphacrucis2 on 2010-10-10
> **Ant0n said:**
> Nope, it didn't find anything... Side note, Hardware Drives has been changed to 'Additional Drivers'. Guess I'll have to wait unto ATI sorts themselves out, oh dear... Thanks for the help bud :)


Ubuntu/ATI already sorted themselves out. The fglrx version in the Maverick repos is a pre release of Catalyst 10.10. You cannot use Catalyst 10.9 as is not compatible with the xorg-server version in Maverick. I went through the upgrade to Maverick and installed the CAT 10.10 fglrx fine via the 'additional drivers' menu. Just to be safe, do the usual sudo aticonfig --initial -f before rebooting.

---

### Post by Ant0n on 2010-10-10
> **alphacrucis2 said:**
> Ubuntu/ATI already sorted themselves out. The fglrx version in the Maverick repos is a pre release of Catalyst 10.10. You cannot use Catalyst 10.9 as is not compatible with the xorg-server version in Maverick. I went through the upgrade to Maverick and installed the CAT 10.10 fglrx fine via the 'additional drivers' menu. Just to be safe, do the usual sudo aticonfig --initial -f before rebooting.

Thanks! Nothing listed in Additional Drivers, but found fglrx in Synaptic - 
it's bizarre that ATI doesn't have 10.10 on their official website yet!

I'll install and let you all know how it went! :)

---

### Post by Ant0n on 2010-10-11
Well that got me the FireGL driver listed in 'Additional Drivers' this would be excellent if I had a FireGL card, but I have a Radeon 4770 so it's not much help! LOL

Compiz had a different complaint about me trying to use the wrong driver...> anton@Computo:~$ compiz --replace &
[1] 2412
anton@Computo:~$ Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
anton@Computo:~$ 


Also, the aticonfig command is now unrecognized! The plot thickens...

---

### Post by castironpants on 2010-10-11
Same problem. I have the "upgraded" driver in Jockey but I still can't enable desktop effects.

---

### Post by castironpants on 2010-10-11
Even after purging everything, installing the 8.73 "TESTING USE ONLY" (from packages) and doing a "sudo aticonfig --initial" and reboot, I STILL can't enable desktop effects! What gives?

---

### Post by alphacrucis2 on 2010-10-11
> **castironpants said:**
> Even after purging everything, installing the 8.73 "TESTING USE ONLY" (from packages) and doing a "sudo aticonfig --initial" and reboot, I STILL can't enable desktop effects! What gives?


What does the following say:


```
fglrxinfo
```

---

### Post by Ant0n on 2010-10-11
Just a heads-up - I tried installing the leaked Catalyst 10.10 driver from Phoronix, and now I'm in lovely low-graphics mode... 

As such, fglrxinfo yields the following:
> anton@Computo:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Error: couldn't find RGB GLX visual!

anton@Computo:~$ 

I'll change back to the FireGL driver and see what it gives me.

---

### Post by castironpants on 2010-10-13
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 5000 Series
OpenGL version string: 4.0.10237 Compatibility Profile Context

---

### Post by JohnH on 2010-10-16
Same problem here!

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3450
OpenGL version string: 3.3.10237 Compatibility Profile Context
```

John

---

### Post by castironpants on 2010-10-16
Mine's fixed. For me, it turns out I kept trying to install compiz from the newest PPA without really thinking about it. Compiz 0.9 doesn't work, but when I did 0.86 it did

---

### Post by phredbull on 2010-10-16
I use the open source drivers w/Radeon 7500M, and Compiz is working pretty nicely...

---

### Post by JohnH on 2010-10-16
SOLVED FOR ME I've got mine back....

I disabled the Compiz PPA, un-installed everything that looked like compiz (including Emerald, and the fusion Icon); I refreshed the repositories (without the Compiz PPA) and reinstalled everything through Synaptic. I then rebooted X and everything seems back to normal.

Regards
John

---

### Post by koblin3426 on 2010-10-21
I have an ATI 4850.

I had the same issue and when I went to activate the drivers it would simply lag and say "searching for drivers" forever.   I couldn't enable desktop effects and thought that was the result of not having a compatible (or...suitable) driver from ATI/Ubuntu.  I was wrong thankfully albeit the additional driver never installed correctly for me without messing with synaptic.

It wasn't just my install fudging up either because the same thing happened when I installed Mint RC 10.  Anyway, to fix the issue I did a very lazy version of what John did.  

How to fix the issue:  

1.  Open synaptic and search for "FG".  Reinstall all of the listed installed packages, and make sure you upgrade all packages that say jockey too which should show an exclamation point next to it (right click ---> upgrade).  Click apply.

2.  Then, search synaptic for "Compiz" and reinstall all packages (and install extra plugins if you want fire!  :P).  

3.  Then reboot and it SHOULD work.  At least, that's how I fixed it.

NOTE: I imagine that you don't actually have to reinstall the packages for fgrlx like I said to in step one.  You most likely only have to "upgrade" those two Jockey packages with the exclamation point.  Not sure though you may have to.  I guess it doesn't really matter either way since it only takes a second.

:popcorn:

---

