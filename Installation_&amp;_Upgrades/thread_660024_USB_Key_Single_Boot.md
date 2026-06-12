---
title: "USB Key Single Boot"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by stevenmitnick on 2008-01-06
I was successful in installing Ubuntu 8.04 Alpha 2 into a 4 gig USB key and it boots up using GRUB. I then took the Ubuntu USB key out to restart the computer to boot up Vista but it wanted GRUB to boot. The only way Vista would boot up was by reinserting the USB key. Once Vista was operating I was able to take the key out without problem. Obviously something happened during installation.

My goal is this: 1) for Ubuntu to automatically boot up when I install the USB key into the computer, and 2) for Vista to automatically boot up (as it is supposed to do) when the Ubuntu USB key is not installed. How do I do this, Grub seems to be the problem.

When LiveCD boots up does it use Grub? If not what does it use? If Ubuntu was installed onto a hard drive without any other OS, what does it use to boot up?

This is what I want to do:

* For the USB key containing Ubuntu to automatically boot up the computer without Grub asking which OS to use. Do I need Grub? Can I use Syslinux (or Extlinux) instead, if so how do I install it?

* For Vista to boot up independent of GRUB while the USB containing Ubuntu is not installed. How do I tell GRUB to only boot Ubuntu on the USB and let Vista boot itself when the USB key is not installed.

Thank you.

---

### Post by Pumalite on 2008-01-06
You have to do everything you did, but avoid that half of Grub gets installed to sda and half to your USB. If in a Desktop, I'd disconnect all internal drives during installation.

---

### Post by stevenmitnick on 2008-01-06
Is there something in Grub that I can do to take Vista out of the sequence? My plan is to keep experimenting with the latest Ubuntu's and using the USB key to store it. I would prefer avoiding having to disconnect the hard drive each time. Thanks.

---

### Post by Pumalite on 2008-01-06
You disconnect the hard drives only during installation to avoid the problem you are experimenting. From there on, Grub will be in USB, you'll have no errors, all your drives can be connectec and you'll have no problems booting to Vista.

---

