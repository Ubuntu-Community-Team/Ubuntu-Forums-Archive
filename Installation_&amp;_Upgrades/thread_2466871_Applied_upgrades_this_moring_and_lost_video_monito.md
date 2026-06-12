---
title: "Applied upgrades this moring and lost video monitors and high resolutions"
date: 2021-09-08
forum: Installation &amp; Upgrades
---

### Post by packer_fan on 2021-09-08
I have been running a clean install of Ubuntu 20.04 for the last 2 months with 3 video screens with higher resolutions.

This morning I was prompted to install/upgrade some packages.  I accepted and went on my merry way.  

I was then prompted to reboot, which I did.

I now have only 1 video screen and the max resolution in 640x480.
I launch settings and all I see is a single display and only one resolution available 640x480.

I tried to reinstall the ubuntu-desktop but  that did not help.

I was not using any of the proprietary video drivers.  I did an install a proprietary video driver 20 minutes ago to see if that would resolve  my issue.  It did not.
How do I revert back?  I need my multiple screens and higher resolutions.
Not really sure how attack this problem. 

lsb_release -d
Description:    Ubuntu 20.04.3 LTS

Thank you
Peter

---

### Post by packer_fan on 2021-09-08
Additional details

I interrupted the GRUB boot loader and decided to try booting the previous version of the kernel (5.11.0-34-generic) was installed this morning.

So I picked 5.11.0.27-generic and I now have all 3 of my displays back with proper resolutions.

So what is up with the 5.11.0.34-generic?  When booting 5-11.0.34-generic how do I get the 3 displays working with proper resolutions?

I can keep running 5.11.0.27-generic for now.

Thank you

---

### Post by janeku2 on 2021-09-08
Looks like the same problem like upgrading from 5.8 to 5.11 kernel. Something not linked with graphc card drivers.
I had similar problem with my HP8440p where I lost my Nvidia drivers when updated from 5.8 to 5.11 beacuse somebody or something did not  managed to extend support to this new version of kernel so I got stuck with nouveau driers instead of Nvidia ones.

---

### Post by packer_fan on 2021-09-09
So were you able to fix this?

---

### Post by packer_fan on 2021-09-09
So were you able to fix this?

---

### Post by mikewhatever on 2021-09-09
What is the graphics card, and have you install a driver manually?
As is, this help request lacks any useful info to work with.

---

### Post by ActionParsnip on 2021-09-09
Does the system have a make and model?

---

