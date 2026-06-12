---
title: "Use USB key install disk as repo source?"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by nexus_2006 on 2010-04-08
I wanted to try a newer version (9.10), so I DL'd the iso and put it to a USB key.  Boot and install to new partition just fine.  When running from the live session, I can use the "restricted drivers" utility to enable the WiFi (4-year old broadcom chip).  After the install, enabling the Wifi chip fails because it can't connect to the repos to get the package.  I'm assuming this is on the USB key, but when I go to synaptic to try and point it at the install disk as a source, it tells me to insert the CD I wish to use.  Short of burning a disk with the iso, what possible work-arounds are there?

---

### Post by solar george on 2010-04-08
Do you know which packages were installed to enable your wireless (or what the name of the driver it installed was)?

---

### Post by nexus_2006 on 2010-04-08
My WiFi chip is the Broadcom BCM4312 802.11 a/b/g

I figured out that the live boot from the USB key installs these packages, in this order, when using the restricted drivers:

```
http://archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.5.9-5_i386.deb

http://archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.12.4ubuntu1_i386.deb

http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.0.1-0ubuntu1_all.deb

http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb

```

I tried d/l-ing them manually, saving the packages, and then installing from the hard drive-based version.  When I do that, the "restricted software" dialog says the hardware drivers are installed but not yet active.  The Wifi light won't come on, and no network device is present.  These are the same things that happen over the live disk.

---

### Post by solar george on 2010-04-08
this may be a sill question but have you rebooted?

---

### Post by nexus_2006 on 2010-04-08
Well indeed, that is a silly question.  However, it was the correct one, as the system now works. :redface:

Anyone know how I might have done this differently, say, if I didn't have multiple OSes installed?  What if I had been stuck out somewhere and needed to use only the USB key install disk?  This software has to be on there, but I couldn't figure out where all the actual packages and data are stored on there...

---

### Post by solar george on 2010-04-08
Look in the pool/ directory on you USB disk.
e.g. bcmwl-kernel-source is in
pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb

---

### Post by nexus_2006 on 2010-04-08
Ah, excellent.  Thats exactly what I was looking for.  

[SOLVED]

---

