---
title: "Installing from USB gives an  apt error"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-03-14
After using the Startup Disk Creator and installing to USB flash drive. When using that flash drive I get an error(see attachment).

I think it has something to do with it not being a CDROM, and its looking for /cdrom device.

This is probably where i should file a bug report, but wanted to pass it by here and see if anyone else using SDC to install to a hard drive noticed the same apt error. A simple click and it continues, but Its still a bug.

---

### Post by Ibidem on 2010-03-15
The surprise would be if it *worked*--how on earth would Ubuntu figure out to point to a flash drive it booted from?
Look at your sources...
The only ways I can see are 1. if the boot scripts resolve the root= option and inserts the right "deb file:///bla/bla/bla" string (*very *complex)  or 2. if the installer binds the boot device to /cdrom (dirty hack; mount --bind /media/something /cdrom)
It may be annoying, but it will be work or a dirty hack.
Ibidem

---

### Post by cariboo on 2010-03-15
As far as I know the USB disk creator app was not meant to create installable media, it's been like that since it's inception.

---

### Post by psyke83 on 2010-03-15
> **cariboo907 said:**
> As far as I know the USB disk creator app was not meant to create installable media, it's been like that since it's inception.

Surely that can't be true. If the USB Startup Disk Creator can't allow regular installs, it's not very useful, is it?

I regularly install from a USB disk to hard disk, though I use unetbootin from Windows to create the installable media (as I install primarily on machines intended for dual-boot configuration).

---

### Post by nubalci on 2010-03-15
I installed kubuntu lucid daily (then removed since I didn't like KDE very much) and got the same error. I did install from CD, so it's gotta be something else.

---

### Post by mc4man on 2010-03-15
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Would seem to be a use (installing

---

### Post by VMC on 2010-03-17
Here's the [**_bug report_**]("https://bugs.launchpad.net/ubuntu/+source/apt-setup/+bug/534473"). Its slated to be fixed by beta2.

---

### Post by VMC on 2010-03-18
Using todays live-daily, MAR18th,  I no longer have the apt error.
It appears to be fixed.

---

### Post by PenguinInside on 2010-03-18
> **VMC said:**
> After using the Startup Disk Creator and installing to USB flash drive. When using that flash drive I get an error(see attachment).


Yes, I had that problem, too. And at exactly 79%.

Unfortunately, I wasn't able click to move forward.

I had to burn a DVD-RW in order to install.

I'll check out the beta to see if it's fixed.

---

### Post by jppr on 2010-03-18
> **vmc said:**
> using todays live-daily, mar18th,  i no longer have the apt error.
It appears to be fixed.

+ 1

---

