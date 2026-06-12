---
title: "software update problem"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by moejoe125 on 2010-02-21
Hi Guys, Im a total newbie to Linux. Would appreciate it if someone could help.

I installed Karmic 9.10 on my machine yesterday, it was working fine then.
Powered up this morning, and straight after the GUI loaded, it prompted me for some software updates, it looked it there were hundreds of them...

So it went through the motions, updating various things...then at about 60% of the way through, it asked me to restart so that installation can continue...

when it rebooted, it displayed the following:

udevadm trigger is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
svgalib: Cannot open /dev/mem.
Gave up waiting for root device. Common Problem:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/9e0ce62f-accf-4a81-9c72-3801bdf5ad2c does not exist. Dropping to shell!


it then goes to the BusyBox v1.13.3 built-in shell
(initramfs)_


My guess it that maybe its something to do with not having the right drivers or something for the graphics card...i duno...


Any help or tips would be much appreciated!

---

### Post by northrup on 2010-02-21
That's weird that it would ask for a restart in the middle of an update.  Normally, it'll wait until the end, at least in my experience.  That might be a problem in itself...

---

### Post by moejoe125 on 2010-02-21
Does anyone have any ideas how I might be able to fix this?

Ideally, I'd much rather to fix the problem rather than just re-installing as I want to learn how to solve/fix these kind of issues...

---

### Post by northrup on 2010-02-21
Hmm... After taking a bit of a deeper look at the error message, it looks like it's having difficulty recognising which hard drive to read the operating system from.  The kernel is obviously loading fine, but something's wrong with it, or it's initial memory image (initramfs).  Are there any other kernel versions you can try that are installed?

Otherwise, reinstalling would probably be your only option.

---

### Post by moejoe125 on 2010-02-22
OK, done some reading, I have managed to find out that this is problem due to the kernel not being able to load because it cant find the root where it expects the kernel to be in...

This is because the initramfs that contains the file initrd.img (which should contain the hd drivers, amonst others) has been corrupted/changed. Therefore it cannot find the harddrive so to speak because it cant find its driver (known as a module in initramfs)


The only problem now is how can I edit the initrd.img file to include the correct modules so that the kernel can boot???

Apparently, this is not something thats easy to do!!!

But anything thats easy usually isnt fun! :P


any ideas guys?

---

### Post by mUsLi on 2010-02-23
I had the same problem. Reinstalled and then chose "restart later" when asked. After the rest of the update I restarted and had no problem.

I don't know how to fix it directly, sorry.

---

