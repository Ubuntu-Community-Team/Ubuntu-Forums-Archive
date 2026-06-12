---
title: "USB HDD Install With Encrypted Win Internal HDD (no bootloader)"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by dstickst on 2010-03-23
Hi all!

I have a laptop with one internal HDD encrypted using Safeboot and running Vista. What I'd like to do is install and run Ubuntu exclusively to/on an external USB HDD. My caveat is that I do not want to mess around with the bootloader. 

To be clear; when I power on my PC as usual, I'd like it to boot directly into Vista (no bootloader). The only time it will boot to Ubuntu (again, no bootloader) is when I first change the boot order to set USB first.

Is this possible?

---

### Post by partloer on 2010-03-23
Hi dstickst,

One way to install Ubuntu without messing around with the bootloader on the Vista HDD is to unplug the HDD with Vista.  That way when you install Ubuntu there is no chance of messing with the bootloader.  

However I don't know how this will boot when you choose the boot order.  What you plan to do sounds like it can work by changing the boot order I just have not tried this method before.

Good luck let me know how this goes.

---

### Post by dstickst on 2010-03-23
> **partloer said:**
> Hi dstickst,

One way to install Ubuntu without messing around with the bootloader on the Vista HDD is to unplug the HDD with Vista.  That way when you install Ubuntu there is no chance of messing with the bootloader.  

However I don't know how this will boot when you choose the boot order.  What you plan to do sounds like it can work by changing the boot order I just have not tried this method before.

Good luck let me know how this goes.

Thanks, but I'd like to avoid having to open up my laptop and physically remove the internal HDD. Any other way I can set this up?

---

### Post by Mark Phelps on 2010-03-23
Sorry if this is going to sound negative ... but ... you are going to have to decide which is more trouble for you: (1) opening up your laptop and disconnecting the hard drive, or (2) repairing any MBR or bootloader damage you accidentally did during Ubuntu installation.

Don't know about YOUR laptop, but I've installed a score of different laptops, and in all of my cases, removing the hard drive took only a couple of minutes.

Just trying to tell you that there is no way to GUARANTEE that an Ubuntu installation will leave your current install untouched -- without actually disconnecting the drive.

---

### Post by dstickst on 2010-03-23
Thanks - I suppose I knew that was probably the only sure-fire way to go about it.

---

