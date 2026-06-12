---
title: "Ubuntu upgrade to 16.04 from 14.04"
date: 2016-11-02
forum: Installation &amp; Upgrades
---

### Post by evilvargon on 2016-11-02
I would like to preface this by saying I am a beginner at using Linux. I have only had it the past year and haven't played around with it as much as I should have. 

That aside, I tried to upgrade from 14.04 to (I believe) 16.04. The installation went okay, and it unpacked a number of libraries. But when it tried to unpack fonts, the entire computer crashed. I could move my cursor, but no luck pressing anything. No keyboard or mouse actions did anything. Now when I try to load in with Ubuntu I get the following screen: [https://drive.google.com/file/d/0B_fz6gi4tNpcMVhrMkFvSTlqVk0/view?usp=drivesdk](https://drive.google.com/file/d/0B_fz6gi4tNpcMVhrMkFvSTlqVk0/view?usp=drivesdk)

I have a msi gp60 2qe Leopard. I am using GNU GRUB version 2.02~beta2-9ubuntu1.12  to dual boot Ubuntu and windows 10

---

### Post by ian-weisser on 2016-11-02
Boot from a LiveUSB.
Use the LiveUSB environment to back up your data to an external device (not to the LiveUSB, which is read-only).
Install 16.04 fresh from the LiveUSB.

A crash in the middle of an upgrade from one release to another is super difficult to recover from, and requires lots of skill and time.
It's generally not worthwhile to fix that kind of (very rare) failure, but to simply wipe and start over.

---

### Post by kevdog on 2016-11-03
I'm sorry I can't be of more help but I can only point you in the right direction.  I've only done something similar on an Arch Linux System where by you would boot from a USB or install disk, and then mount the partitions of your original drive and chroot into the mounted directory whereby you could then try to upgrade various items within the installation.  I think there is a tool called debchroot or maybe you could just straight chroot into the directory tree.  Come to think about it, I'm pretty sure you could use the arch boot method to chroot because once your in the chroot environment, you essentially would be back into the Ubuntu way of doing things.  

Again, sorry I'm not too much help about specifics.

---

### Post by i2000s2 on 2016-11-03
> **kevdog said:**
> I'm sorry I can't be of more help but I can only point you in the right direction. I've only done something similar on an Arch Linux System where by you would boot from a USB or install disk, and then mount the partitions of your original drive and chroot into the mounted directory whereby you could then try to upgrade various items within the installation. I think there is a tool called debchroot or maybe you could just straight chroot into the directory tree. Come to think about it, I'm pretty sure you could use the arch boot method to chroot because once your in the chroot environment, you essentially would be back into the Ubuntu way of doing things. 

Again, sorry I'm not too much help about specifics.

The apt-get will be available in the chroot mode even the original system had the apt-get package broken? I got a similar error with apt-get broken.

---

### Post by kevdog on 2016-11-03
Hmm, the debootstrap method is to install a base system.  Perhaps you could just install apt from source with dpkg?

---

### Post by i2000s2 on 2016-11-05
I think I have screwed up. I followed the steps in[ this post]("http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html") and used chroot to fix the broken packages. I thought I have fixed the apt-get problem, but when I reboot into the normal mode, the system cannot boot into the Ubuntu systems. I also tried to boot with my live CD on my usb stick again, but the usb stick could neither boot up. Both with black screens. Alt+Ctrl+F2 and found the system was waiting for the boot to be finished without mentioning what module was left to run. Wait for a day and nothing happened. The TTY mode doesn't have an internet connection. The USB stick booting basically said release-upgrade-notifier does not work because of lack of space. Now what can I do?

> **i2000s2 said:**
> I think I have screwed up. I followed the steps in[ this post]("http://www.webupd8.org/2014/01/how-to-fix-non-bootable-ubuntu-system.html") and used chroot to fix the broken packages. I thought I have fixed the apt-get problem, but when I reboot into the normal mode, the system cannot boot into the Ubuntu systems. I also tried to boot with my live CD on my usb stick again, but the usb stick could neither boot up. Both with black screens. Alt+Ctrl+F2 and found the system was waiting for the boot to be finished without mentioning what module was left to run. Wait for a day and nothing happened. The TTY mode doesn't have an internet connection. The USB stick booting basically said release-upgrade-notifier does not work because of lack of space. Now what can I do?

I think I didn't mount the /boot directory while updating in liveCD. The /boot directory was on a separated partition on my HDD. Redo everything and to see if it works. Following instruction at [http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation](http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation)

Ok, now I can login and update packages using the liveCD, but this fix doesn't make me boot into the Ubuntu 16.04 system in a normal mode afterward. It went into emergence mode in a new boot, and from the journal it failed to connect to the system bus (systemd-udev) and cannot mount ntfs partitions on my disk. Not sure what to fix now.

There maybe something to do with the switch between upstart and systemd by updating from 14.04 to 16.04. So, I am in booting with Upstart and now can use 

```
sudo startx 
```
 
to boot into a desktop environment. The booting screen was black still, alt+ctrl+F2 showed:

```
A start job is running for Hold until boot process finishes up (xxmin xxs / no limit)
```

So, on TTY1, I tried ```
sudo service lightdm start
```, and it returns ```
job failed to start
```. Not sure what else I can diagnose.

Update: I think there is a problem with lightdm setting, which gives errors:
```
think-keycodes is broken, missing valid name for "Provides"; cannot find Upstart. 
```
I have installed systemd, of course.
But for some reason it's working now. Thanks for the helps earlier!

---

