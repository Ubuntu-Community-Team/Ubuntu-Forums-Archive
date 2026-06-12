---
title: "Advice on 12.04.4 LTS HWE EOL Upgrade / Update - nVIDIA"
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2014-07-06
Hello,

   I am using 12.04.4 LTS (AMD64).  I recently got a message from Update Mangaler about HWE EOL and the recommendation that I upgrade to the Trusty Kernel.  Upon upgrading, the nVIDIA DKMS did not build - and gave an error.  I then removed the Trusty Kernels.

  Was this because upon HWE EOL upgrade, the kernel source was not downloaded, therefore the DKMS failed to rebuild the module on the new 3.13.x (Trusty Kernel)?  Or is there an issue with the nVIDIA drivers?  I'm using the XORG EDGERS PPA.

Regards,
CH

---

### Post by Frogs Hair on 2014-07-06
Mis-understood post

---

### Post by frogotronic on 2014-07-07
Here's the message that comes up with the Update Manager:[ATTACH=CONFIG]254528[/ATTACH]

And here's the link: [ATTACH=CONFIG]254529[/ATTACH]

But the nVIDIA driver fails to build for the Trusty Kernel...

---

### Post by frogotronic on 2014-07-07
Ok, kernel build (DKMS) spits an error, everything else builds okay.  Reboot & all running fine.

Here's the command I used:

```
$ sudo apt-get install linux-generic-lts-trusty linux-image-generic-lts-trusty
```
 

- CH

---

