---
title: "New install - no hard drive found"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by cdelaire on 2008-08-21
Hi,

I am new to Ubuntu and Linux and really want to get rid of Windows...

I have upgraded my pc by buying an ASUS P5Q-pro mobo and a new 80GB SATA hard drive to install the OS.

When i run the install from the Ubuntu 8.04 iso (downloaded from ubuntu.com and burned on a cd), QParted cannot find any devices.

The hard drive is recognized properly in the BIOS.

I have tried to following already, without resolving anything:

1. change SATA Config settings in the BIOS to all different options (Compatible, Enhanced)

2. connected HDD to an external enclosure, connected it to my laptop, formated the HDD

And to complete my bad luck, i also tried to install Win Vista and received an error saying that a file was not accessible on the DVD...

Can somebody please help me, i have searched answer on the net without any luck...

Cheers,
Christophe

---

### Post by redester on 2008-08-21
****

Try running from a Live CD and going into the system /boot/grub and editing MENU.LST using an editor.. NANO *may* be available. Then make sure the drive/partitions are correct.  I had that kind of problem and found the drive referred to hd1.. NOT hd0.

Changing this worked and I'm now a MUCH happier Ubuntu 8.04 user after two weeks of hell!  :-)

Ray

---

### Post by maybeway36 on 2008-08-21
You might need to install to an IDE hard drive if SATA doesn't work.

---

### Post by cdelaire on 2008-08-21
> **maybeway36 said:**
> You might need to install to an IDE hard drive if SATA doesn't work.

Thanks maybeway36,
It might be the easiest way to get around it but i want to fix the problem, surely it can be fixed... And on this new mobo i only have one IDE slot which will be used by 2 optical drives.

---

### Post by cdelaire on 2008-08-21
> **redester said:**
> ****

Try running from a Live CD and going into the system /boot/grub and editing MENU.LST using an editor..

Ray

Thanks Ray,
Running Live Cd (which is the only thing i can do :()I have searched for menu.lst on the system and only found examples of the menu config files...:confused:

---

