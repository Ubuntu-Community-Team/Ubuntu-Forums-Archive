---
title: "Blank Screen after install - Maverick Meerkat"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by tigerplug on 2010-11-15
Hi everyone, 

I'm experiencing an unusual issue while trying to install on my Dell Inspiron 1520.

I can test the distro using the LIVE CD just fine but after installation I just get a light colored screen - usually a blank gray screen.

I have tried burning multiple copies of the installation disk, different media and different downloads (torrent, ftp, http etc.) but still no luck.

My graphics card is an Nvidia Geforce 8400M GS.
I've also tried the "alternate" install disk from a previous release - unsuccessful.


Suggestions appreciated!



Thanks,

---

### Post by Rubi1200 on 2010-11-15
Have you tried the nomodeset parameter when booting?
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
(it says 10.04, but should also be relevant for 10.10)

Also try this:
> On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
(courtesy of forum member oldfred)

---

### Post by tigerplug on 2010-11-15
Rubi1200, 

Thanks for the quick reply!
I'm going to attempt a dual boot config now and I'll report back shortly.

---

### Post by tigerplug on 2010-11-15
Worked a charm.
Thanks for your help!

---

### Post by Rubi1200 on 2010-11-16
You are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy!

---

