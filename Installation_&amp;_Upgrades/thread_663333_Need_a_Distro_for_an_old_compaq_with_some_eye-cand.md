---
title: "Need a Distro for an old compaq with some eye-candy"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by Tekno_Cowboy on 2008-01-10
I've got an old Compaq with an AMD K6-2 533/97 MHz CPU and 192MB ram. I got puppy linux installed, but it lacks even an xfce level of eye-candy. Since this is going to be used to try and sway someone from Windows, I need a little nicer looking system. I'd like to install something with xfce or a similar lightweight window manager, but I'm not sure what would be best. If I could get 
Xubuntu working, even if it's a little slow, it would be perfect, but I cant seem to get past the Kernel loading popup and then my computer reboots. I think it may have something to do with the way the isolinux loader handles things, but I'm not sure. I would appreciate any help or suggestions I can get.
Thank You.

---

### Post by tylerspaska on 2008-01-10
i have recently installed geubuntu and love it. check it out:

[http://geubuntu.intilinux.com/](http://geubuntu.intilinux.com/)

tons of eye candy and very, very light. i have it running on 450 Mhz with 256MB ram

edit: i would also check out dream linux

---

### Post by ugm6hr on 2008-01-10
> **Tekno_Cowboy said:**
> I've got an old Compaq with an AMD K6-2 533/97 MHz CPU and 192MB ram. I got puppy linux installed, but it lacks even an xfce level of eye-candy. Since this is going to be used to try and sway someone from Windows, I need a little nicer looking system. I'd like to install something with xfce or a similar lightweight window manager, but I'm not sure what would be best. If I could get 
Xubuntu working, even if it's a little slow, it would be perfect, but I cant seem to get past the Kernel loading popup and then my computer reboots. I think it may have something to do with the way the isolinux loader handles things, but I'm not sure. I would appreciate any help or suggestions I can get.
Thank You.

You are going to struggle with eye-candy on that.  Perhaps if that is what you are after - Enlightenment might be the best option (rather than XFCE).

Maybe this?
[http://www.thinkgos.com/](http://www.thinkgos.com/)

Unfortunately, I have no idea why your computer won't boot.  Are you using a LiveCD or Alternate?

EDIT: I see tylerspaska has also suggested an Elightenment Ubuntu derivative..... great minds, eh?

---

### Post by zvacet on 2008-01-10
Try with [Xubuntu](http://www.xubuntu.org/get) alternate CD.

---

### Post by angelsguitar on 2008-01-10
> **Tekno_Cowboy said:**
> I've got an old Compaq with an AMD K6-2 533/97 MHz CPU and 192MB ram. I got puppy linux installed, but it lacks even an xfce level of eye-candy. Since this is going to be used to try and sway someone from Windows, I need a little nicer looking system. I'd like to install something with xfce or a similar lightweight window manager, but I'm not sure what would be best. If I could get 
Xubuntu working, even if it's a little slow, it would be perfect, but I cant seem to get past the Kernel loading popup and then my computer reboots. I think it may have something to do with the way the isolinux loader handles things, but I'm not sure. I would appreciate any help or suggestions I can get.
Thank You.

I have an old Compaq laptop with a 266Mhz processor an 192 RAM.  I tested Xubuntu but found it slow on it (I had problems with the desktop install cd too; had to use the Alternate install CD to be able to install it).  I'm using Puppy on it right now and am happy with it, considering the capabilities of the laptop.
You can install XFCE on Puppy. It's available as a .pet package.  XFCE is a little heavier than the default Puppy window manager (JWM), though.

---

### Post by raymac46 on 2008-01-10
> **Tekno_Cowboy said:**
> I've got an old Compaq with an AMD K6-2 533/97 MHz CPU and 192MB ram. I got puppy linux installed, but it lacks even an xfce level of eye-candy. Since this is going to be used to try and sway someone from Windows, I need a little nicer looking system. I'd like to install something with xfce or a similar lightweight window manager, but I'm not sure what would be best. If I could get 
Xubuntu working, even if it's a little slow, it would be perfect, but I cant seem to get past the Kernel loading popup and then my computer reboots. I think it may have something to do with the way the isolinux loader handles things, but I'm not sure. I would appreciate any help or suggestions I can get.
Thank You.

Stepping away from the Ubuntu family a bit. I have a Compaq Presario 5360 - K6-2 450 320 MB RAM.
The two best distros I've found are Vector Linux 5.9 and Antix Spartacus. VL for sure is the nicer desktop. If you decide on Antix use the older version (Spartacus) based on Mepis 6.5. The newer Antix based on Mepis 7.0 is 686 based and the K6 doesn't like it.
I had to add the following boot options to VL to avoid rrreepppeeaaattttiiinnggg letters in X, and also to get the Compaq to power off properly.
acpi=force pci-=noacpi
192 MB of RAM is a little on the light side for decent performance. If you can add another 128 you'll be in business.

---

### Post by K.Mandla on 2008-01-10
Take a look at this thread too, if you need more ideas.

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by Tekno_Cowboy on 2008-01-10
I seem to be having troubles with anything that uses isolinux to boot a cd.(this includes every ubuntu-based cd I've come across) I would use some kind of grub to boot, but I only have 1 drive to work with. looking at vector linux in virtualbox it looks like it should boot. If I can get that running, maybe I can get geubuntu going too, since it looks like it has nicer eye-candy. Thanks to everyone who gave me suggestions:)

---

### Post by Tekno_Cowboy on 2008-01-10
well, I accidentally dropped that computer and wrecked it. I'm working with a Pentium III - 450 MHz with 128 MB ram now. I'm having troubles with booting though. I can get Vector Linux to boot to command line, but I can't start x. It gives me an error about no displays(or was it screens) being found, and goes back to the command line. I ran into this same problem while trying to load gentoo/sabayon onto my desktop, but was never able to find a way around it. If anyone knows what might help, I'd be grateful for your advice.

---

### Post by oldos2er on 2008-01-10
I'd be asking about that in the Vector forums: [http://www.vectorlinux.com/forum2/](http://www.vectorlinux.com/forum2/)

---

### Post by Tekno_Cowboy on 2008-01-11
That's a very good point. Thank You.

---

