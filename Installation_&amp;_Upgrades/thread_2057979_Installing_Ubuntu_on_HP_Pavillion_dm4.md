---
title: "Installing Ubuntu on HP Pavillion dm4"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by mrgabe55 on 2012-09-14
I want to remove Windows 7 and install Ubuntu 12.04 on my HP Pavilion dm4 Laptop. At the moment it has three partitions; a Recovery D: drive, An HP tools drive and My Local disk C: drive. When I install Ubuntu should I just select the erase all and install Ubuntu or do I have to do something else and also It has ATI Radeon HD 7470M Graphics and USB 3.0. Which Drivers will I need?

---

### Post by lukeiamyourfather on 2012-09-14
The AMD graphics will have official or open source drivers installable from Ubuntu's repositories. Not sure about USB 3.0 but my guess is it would work (never tried USB 3.0 in Linux). If you have enough space to do so I'd leave the original HP partitions and just remove the Windows partition (what was your C: drive in Windows). That way if you want to go back to Windows you still have the installer for Windows and you also have the troubleshooting utilities in case there's ever issues with the laptop.

---

### Post by Mark Phelps on 2012-09-14
BEFORE you do anything else -- wouldn't you at least like to KNOW if your PC will run Ubuntu OK?

Never presume that ANY machine will run an OS OK, without trying it first -- which, fortunately, is an easy thing to do with Ubuntu.

Create a LiveCD or a LiveUSB, boot from that -- and see how well it detects all the hardware and installs all the drivers.

Anything that does NOT work in that mode is going to range from trivial to impossible to fix.

Laptops are especially bad for Linux OSs because laptop vendors use specialized hardware -- for which there is very often, NO Linux drivers.

It's better to find out NOW that something won't work, while you can still browse the forums and possibly, get solutions, than to remove the only working OS on the laptop and then -- end up with an "electric brick"!

---

### Post by verdomde on 2012-10-16
Hmm, dunno if you did anything about this yet, but I have installed 12.10 throught the alpha and now in beta, and it works fine on the machine. There are no drivers for the fingerprint sensor though, and a potential problem with the graphics card, the ATI proprietary drivers dont work with this kernel apparently, and the opensource drivers cause some kind of conflict with the fan I believe, its on all the time, spewing out REALLY hot air. This is rectified with the proprietary drivers from ATI, if you have an older release of ubuntu then it may not be an issue to install them. Because of this I'd recommend doing as lukeiamyourfather says, leave the HP partition alone so you can go back to the original windows if you too have a problem with the fan. Everything else works well though, and the problem im having will be sorted with either an update to amd 12.10 drivers or a fix on the opensource drivers, im about to enquire on here, and maybe submit a bug...

---

