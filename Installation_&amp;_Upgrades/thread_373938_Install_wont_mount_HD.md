---
title: "Install wont mount HD"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by HeftyOrb on 2007-03-01
OK. I was able to install Ubuntu on a computer with XP using a dual boot. My girlfriend wasn't keen on this so I went and bought a new laptop. And since the release of Vista. I now have it, and hate it. So I'm trying to get rid of it, and only run Ubuntu, but the install wont mount or find my hard drive. The live CD runs and boots fine. But nothing is able to find my hard drive.

I noticed during the boot that the mount process reads something about an invalid feature.

Any Ideas?!?

Thanks
:smoking:

---

### Post by x64Jimbo on 2007-03-01
It's possible that your new computer uses a SATA hard disk whose controller is not supported in the latest stable version of Ubuntu. You could try Feisty Herd 4 (a development version) and see if that works. Unfortunately, the latest and greatest hardware is often not very well supported in Linux because open source devs don't get the chance to test the hardware before it's released, and many hardware manufacturers only write Windows drivers.

---

### Post by AAM on 2007-03-02
x64Jimbo is correct, look at the disk option in the administration/control centre menu. If you can't see the sda drive there, your chipset is not recognised. If not then try MEPIS or some other distro.

---

### Post by warjowuch on 2007-03-02
Let us know the results! Curious...

---

### Post by HeftyOrb on 2007-03-02
Thanks. I'm off to try to see what happens.
:smoking:

---

