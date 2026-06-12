---
title: "Virtual Windows XP inside Ubuntu, help!"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by samuraitor on 2010-01-27
hey,

what is the best way to install a virtual copy of Windows XP inside ubuntu 9.10?

How can I install office 2007 in the virtual XP inside ubuntu?[CENTER][/CENTER]

---

### Post by howefield on 2010-01-27
Have a look at Virtualbox.

You can install from Synaptic Package Manager, or download the .deb package from Virtualbox.org (the download from the website is a different version which allows amongst other things, you to use USB devices, so if this is important, get it from the website)

Also on that site, you will find short video tutorials that are worth watching.

Once you have virtualbox running and windows installed, you will install any program just as if it were on a "real" windows installation.

---

### Post by bullgr on 2010-01-27
you can use virtualbox... follow these instructions to install it: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

note that this is the closed version... virtualbox OSE (open source edition) has some limitation (not supporting usb).

with virtualbox you can run windows xp inside ubuntu, with all the programs you want and with usb support and native (brigded) network.

note that you need a dual core mashine to have functionality in the virtual environment... or else youl get nerve damage!!!

another note: in the disk creation, use the option "fixed hard disk" insteed "dynamical hard disk" to avoid disk fragmentation (virtual or not, some s**ty winblows stuff are still remain!!!)

---

### Post by samuraitor on 2010-01-27
> **bullgr said:**
> you can use virtualbox... follow these instructions to install it: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

note that this is the closed version... virtualbox OSE (open source edition) has some limitation (not supporting usb).

with virtualbox you can run windows xp inside ubuntu, with all the programs you want and with usb support and native (brigded) network.

note that you need a dual core mashine to have functionality in the virtual environment... or else youl get nerve damage!!!

another note: in the disk creation, use the option "fixed hard disk" insteed "dynamical hard disk" to avoid disk fragmentation (virtual or not, some s**ty winblows stuff are still remain!!!)

guys,

I have installed Virtual Xp inside Ubuntu. Now the only problems remains the USB which is not found in virtual XP. Under device manager it says that everything is correct but fails to load the inserted USB. Anyway around this?

---

### Post by howefield on 2010-01-27
> **samuraitor said:**
> guys,

I have installed Virtual Xp inside Ubuntu. Now the only problems remains the USB which is not found in virtual XP. Under device manager it says that everything is correct but fails to load the inserted USB. Anyway around this?

Have you created a filter for it ?

---

### Post by samuraitor on 2010-01-27
> **howefield said:**
> Have you created a filter for it ?

what values do I enter for the creation of USB filter?

---

### Post by howefield on 2010-01-27
All you should need to do is go to the settings screens, as per my screenshot and click on the USB icon (with the plus sign) on the right hand side of the window, then select your device.

It'll then appear inside the main window.

---

### Post by samuraitor on 2010-01-27
> **howefield said:**
> All you should need to do is go to the settings screens, as per my screenshot and click on the USB icon (with the plus sign) on the right hand side of the window, then select your device.

It'll then appear inside the main window.

I have followed your steps, and even filled info where required.

Device manager says that it is already installed. When I check under "Devices " Virtual box window, I spot my USB but it is greyed out.Funny thing is that my biometric finger reader is detected and ready for isntallation.

---

### Post by howefield on 2010-01-27
You may need a reboot after installing virtualbox and adding yourself to the vboxusers group for everything to take effect.

---

### Post by samuraitor on 2010-01-27
> **howefield said:**
> You may need a reboot after installing virtualbox and adding yourself to the vboxusers group for everything to take effect.

bravisimo! mission accomplished!

---

### Post by howefield on 2010-01-27
> **samuraitor said:**
> bravisimo! mission accomplished!

I thought it was "bravissimo" !!

Anyway, well done and have fun virtualising :)

---

### Post by bullgr on 2010-01-27
don't forget to install in virtual xp the virtualbox guest additions: [http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/](http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/)

---

