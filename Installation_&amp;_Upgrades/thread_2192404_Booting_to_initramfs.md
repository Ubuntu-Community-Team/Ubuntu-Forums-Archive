---
title: "Booting to initramfs"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by jord1981 on 2013-12-07
I have a hard drive onto which we back up all of our personal pictures and videos.  I want to start making a quarterly back up of this drive.  I disconnected my boot drive and replaced it with this blank drive for the purpose of secondary backup.  I then attempted to boot with live cd to burn from one drive to another.  Lubuntu failed to boot and I ended up at the following command prompt:

> BustBox v1.20.2 (Ubuntu 1:1.20.0-8.lubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I am unable to mount drives and execute the copy I want to do from here.  I researched this and tried burning a second live cd and then booting from a USB key.  In all cases I end up at the same command prompt.

Advice?

Thanks in advance.

---

### Post by ajgreeny on 2013-12-07
Are you sure the live disk or the .iso file you used to burn it is a good one?  Have you booted it before?

When you boot the CD you get a chance to "check install CD" or similarly worded option.  I suggest you do this, and if it shows any errors download the iso and burn again.

---

### Post by jord1981 on 2013-12-07
The live CD has been used to install on 3 systems, but that seems to have been the problem, I downloaded a fresh ISO and put it on the USB key and it works.  I now have another problem, but I'll have to post that in a different thread.  Thanks for your help.

---

### Post by jord1981 on 2013-12-08
I was able to boot once with the USB key.  But I am back to booting to the initramfs prompt.  Machine boots fine to hard disk with Ubuntu on it.  I've tried two different USB keys and with each, created them on different machines from difference ISOs and have used different USB ports on the machine in question to try to boot.  The keys are able to successfully boot other machines.

---

### Post by jord1981 on 2013-12-08
UPDATE: If I disconnect all hard disks, I am able to boot to the Lubuntu GUI from the CD and both USB keys.

---

### Post by jord1981 on 2013-12-08
I was eventually able to boot from USB key with 2 hard disks connected but the DVD drive disconnected.  Apparently 4 disks was too much to handle?

---

