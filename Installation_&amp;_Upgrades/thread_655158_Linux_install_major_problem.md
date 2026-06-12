---
title: "Linux install major problem"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by waahoo on 2008-01-01
Ok folks, here we go with a little history (sorry, but this will be long);

I am having a problem getting any, and I mean any, disto of linux to install on a new build.  No, I'm not a noob, but it has been a few years since I have played with Debian.

Six months ago I decided to give Microsoft the farewell with a gradual migration to linux.  Ubuntu seemed to be the best option, so I commited to this distro for the conversion.  All had gone well until I built myself a new box for Christmas :redface: and I tried to install Ubuntu over XP Pro.  It was a major pain to even get to the Live CD desktop.  After using  F6  and editing for pci=nomsi --irqpoll it would boot but was unstable and would not reach logon.

Many attempts later I  tried Hardy 8.04 and got it to load ( once again using F6 edit - pci=nomsi -- irqpoll) with much force but it was very unstable and crashed programs with abandon.  Being frustrated at that point, I tried PCLinuxOS with results much like Ubuntu Gutsy and openSUSE 10.3 the same.

The only thing my pea brain can come up with for a problem is the cutting edge components which are as follows:

MoBo -          Abit IP35 pro
CPU    -         Intel Quad
RAM   -          Mushkin 4gb (2x2gb) DDR2
HDD    -         WD Raptor (2) 150gb Sata
DVDRW-       ASUS Sata
GCD -           XFX GeForce 8800GT

So I am asking for any help from you die hards and big brains that will help me go forward and not revert to Microsoft.

By the way, XP Pro and Vista Ultimate work great as much as it hurts me to say.

Hopefully I am just missing something.  I am not a complete NOOB and I cut my teeth on Basic, Cobol abd Fortran.  Any help would be appreciated as I would like to test and give feedback for Hardy 8.04

Bob

---

### Post by PmDematagoda on 2008-01-01
Did you try installing Ubuntu using the Alternate CD? The issue could be because your VGA card may be too advanced to be handled by the built-in driver.

---

### Post by waahoo on 2008-01-01
Haaa... No, that would be to simple... I'll download and give it a try.

Thanks for removing the brain fart, I'll give a report when completed.

Thank you,
Bob

---

### Post by waahoo on 2008-01-01
anyone else while I'm waiting?

---

### Post by waahoo on 2008-01-01
The install completed using alternate cd.  The system appears to be stable, but will not provide adjustment other than 800x600 for my monitor and will only use vesa driver.  The Nvidia driver appeared to install fine but will now not register.

Any suggestions would be helpful.

By the way... the monitor I'm using is a Samsung 740n lcd and it does not show up in 'screens and graphics', nor does the 8800gt.

Thank you, 
Bob

---

### Post by PmDematagoda on 2008-01-01
How did you install the Nvidia driver? What version was it?

---

### Post by Pumalite on 2008-01-01
Check Nvidia site for appropriate driver for your card. Download it. Edit menu.lst and replace 'splash' for 'nosplash'. Reboot. Now install your new driver.

---

### Post by oldsoundguy on 2008-01-01
try installing your nVidia  drivers using Envy.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
worked for me BEAUTIFULLY!
(but, even tho it says it will install ATI .. it has to have something to install and therein lies the problems with that card.  Did NOT work on an ATI equipped machine, but works flawlessly on an nVidia machine!)

---

### Post by waahoo on 2008-01-01
> **PmDematagoda said:**
> How did you install the Nvidia driver? What version was it?

I installed V. 169.07 through GRUB recovery.  I tried to install by "Ctrl + Alt + F2 = INIT 3" but It would not let me log in as 'root'.

---

### Post by waahoo on 2008-01-01
> **oldsoundguy said:**
> try installing your nVidia  drivers using Envy.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
worked for me BEAUTIFULLY!
(but, even tho it says it will install ATI .. it has to have something to install and therein lies the problems with that card.  Did NOT work on an ATI equipped machine, but works flawlessly on an nVidia machine!)

I tried ENVY with the following result::

ENVY ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed.  You can try the manual installation at your risk.

I used ENVY - Version 0.9.9

---

### Post by oldsoundguy on 2008-01-01
sorry, It worked great on a couple of 6200 cards .. might have something to do with PCI-e?

Most likely you will have to do a manual install.  NVidia has some really good support (especially as opposed to ATI!).  And a couple of very good forums.  You might try that route.

---

### Post by waahoo on 2008-01-01
> **oldsoundguy said:**
> sorry, It worked great on a couple of 6200 cards .. might have something to do with PCI-e?

Most likely you will have to do a manual install.  NVidia has some really good support (especially as opposed to ATI!).  And a couple of very good forums.  You might try that route.

Thank you for the help.

I cleaned up and did another manual install with the same results.  Nvidia X Server Settings shows up in Applications/System Tools, but when I select it the error message ' You do not appear to be using the Nvidia X driver' shows up.

---

### Post by waahoo on 2008-01-01
Well I don't know where to go from here.  Once again, after a clean install of the 169.07 driver, the install from root went flawlessly and I even had it reconfigure the xorg.conf file.  It is still not working.  The xorg.conf file is continually backed up and moved out for another with generic monitor and vesa drivers.  This is very disappointing considering I have already changed two home and two business boxes over to linux.  I've got a lot of time invested at this point and would hate having to consider Micro$oft again.

If anyone has any further ideas, please let me know.

---

