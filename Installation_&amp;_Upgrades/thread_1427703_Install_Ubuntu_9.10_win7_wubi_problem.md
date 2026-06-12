---
title: "Install Ubuntu 9.10 win7 wubi problem"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by McSlurry on 2010-03-11
Hey,

i tried to install ubuntu 9.10 on my win7 machine... This is what ive done so far:
- Created 30GB partition on drive
- DOwnloaded and installed ubuntu with wubi (i know its done right)
- rebooted

when i reboot and choose to run ubuntu as the OS i get a message saying something along the lines of: "Could not find the ISO /ubuntu/install/installation.iso

i check my 30GB partition on the ubuntu section of the drive and that exact file is in the right place.... why is this happening? what should i do to run Ubuntu successfully?

thanks in advance

---

### Post by McSlurry on 2010-03-14
ne1?

---

### Post by Mark Phelps on 2010-03-14
About the only two advantages of Wubi are (1) you don't have to create any new partitions, and (2) you don't overwrite the MS Windows entry in the MBR.

Since you've already done (1) and, using the Win7 backup feature, you can easily create and burn a Win7 Repair CD to restore the Win7 MBR that would be overwritten with a traditional dual-boot install, thus addressing (2), I don't see why you want to continue to bother with Wubi.

---

### Post by dataking on 2010-06-04
I'm having this same problem.  I'm trying to use the "Install within Windows" feature of wubi.

This is a work computer, so I don't want to mess with the Win7 image by changing the partition structure or anything.  

I'm able to mount the cdrom from the (initramfs) prompt but it doesn't show up on the root directory.  I can mount it to /cdrom and view the contents from there, but the script for the next step of the install doesn't find it.

Any advice?

---

### Post by dataking on 2010-06-04
I just realized this thread is a few months old.  I'm actually having the same problem with the 10.04 LTS wubi/install disk.

Here's the error in it's entirety:

```

Could not find the ISR /ubuntu/install/installation.iso  This could also happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of a removable device without first unmounting or ejecting it.  To fix this, simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then gracefully shut down and reboot back into Windows.  After this you should be able to reboot again and resume the installation.

```

Naturally, 'chkdsk' was the first thing I tried.

---

### Post by wilee-nilee on 2010-06-05
> **dataking said:**
> I just realized this thread is a few months old.  I'm actually having the same problem with the 10.04 LTS wubi/install disk.

Here's the error in it's entirety:

```

Could not find the ISR /ubuntu/install/installation.iso  This could also happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of a removable device without first unmounting or ejecting it.  To fix this, simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then gracefully shut down and reboot back into Windows.  After this you should be able to reboot again and resume the installation.

```

Naturally, 'chkdsk' was the first thing I tried.

Your going to want to start your own thread to get the quickest help and make it easier to just see whats going on.;)

Also include more information such as what you have done so far in actually installing wubi and post this boot script in code tags to out line the whole setup.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dataking on 2010-06-05
Thanks for the reply.  I will start another thread.

One question:  Is there enough of a "system" in BusyBox/initramfs for the boot script you suggested to gather the information it needs?

---

