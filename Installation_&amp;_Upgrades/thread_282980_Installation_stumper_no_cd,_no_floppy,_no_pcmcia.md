---
title: "Installation stumper: no cd, no floppy, no pcmcia"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by Bastanteroma on 2006-10-23
I'm stumped.

I've got a sony vaio PCG-Z505LSK laptop missing the pcmcia card reader, which is the only way to attach a bootable external cd or floppy drive (can't boot from a usb drive).  Installed on the hard drive is a copy of Win2000 with an unknown password.

I am capable of putting the hard drive in another computer and either wiping it or installing something on it.  Could I, for example, install Ubuntu on another laptop, swap the drive into this one, and then somehow modify the hardware configuration accordingly?  Or are there any other ideas?

---

### Post by hellblade on 2006-10-23
It is possible I guess. But don't forget to install the right kernel for your laptops processor. Also you will need network access later to install more packages and updates.

Try it and tell us what you got:)

---

### Post by Jussi Kukkonen on 2006-10-23
You can try the drive swap, it could work. At least well enough to get you to a console... 

Alternatively you might get a working copy of Windows from the BIOS -- many laptops have a hidden partition that has the windows install media on it. Check the BIOS choices. Then you could try [http://instlux.sourceforge.net/](http://instlux.sourceforge.net/) or  [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html).

---

### Post by gn2 on 2006-10-23
I am told what you propose can be done, but I haven't tried yet.

When you put the drive back in the Vaio, you should get to a terminal prompt.
Type "sudo dpkg-reconfigure -phigh xserver-xorg" (without the quotes" and you will be able to reconfigure the hardware set-up.

---

### Post by Bastanteroma on 2006-10-23
I may try soon, and I'll post an update.

---

### Post by Bastanteroma on 2006-10-23
Another idea!  Someone told me a while back that most external usb hard drives use the same 2.5 in drives as laptops.  Assuming I can get my laptop drive to work in an external enclosure, which I should be able to scrounge up, does anyone have any suggestions for installing to a usb drive in such a way that it will then be able to boot as an interal ide?  Would the change in bus create problems?

---

### Post by Bastanteroma on 2006-10-23
I found an enclosure, which I hope to put the laptop drive into.  It seems that if I install Ubuntu onto a usb drive from my desktop the fstab, and probably other things, will be all wrong when I put it into the laptop.  Is there a way to setup the drive, maybe putting the installation cd onto a partition flagged as bootable?

I don't think I know enough to make this work without help, and I don't have a laptop available to try the other technique.

---

### Post by Craigus on 2006-10-24
You should be able to do a network install - does this machine pxe boot?

[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

I did this with no problems on my similar machine - a Toshiba 3490CT.

---

### Post by Bastanteroma on 2006-10-24
Netboot is out because I can't get into Windows because I don't know the password.  But I fixed the pcmcia slot, so I should be able to attach a cd drive now.  So the experiment may be off.

---

### Post by Craigus on 2006-10-25
Wouldn't net booting be simply a matter of changing the boot device in the BIOS? Or is it the BIOS password that you don't know?

---

### Post by Bastanteroma on 2006-10-27
The boot sequence provides only the floppy, cd, or hard drive as options.  So I ordered a cd drive after realizing that the pcmcia slot wasn't broken, as I'd thought.

---

