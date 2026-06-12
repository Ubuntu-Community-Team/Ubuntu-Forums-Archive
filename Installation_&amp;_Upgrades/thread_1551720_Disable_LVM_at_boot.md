---
title: "Disable LVM at boot"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by merlin371 on 2010-08-12
Is there a way to disable LVM at boot, I'm having problems with the HD at install this on the attachment is what i get.


The only drive showing there is /dev/sdb the other one is not a drive, there should be 2 more 120gb HD and 1 250GB but they don't show, now I've tried installing slackware and it can see all the different drives no problem and i was able to install to /dev/sda with no problem, is there anyway i can just disable LVM or whatever it is that is doing that to my drives? thanks

And btw they are not in a raid at all, they are all sata drives on the onboard controller of the motherboard which is MSI P43 NEO-F

Thanks

---

### Post by merlin371 on 2010-08-12
K so i used nodmraid option on boot and it got rid of the raid but i still cant see my other drives at all, it now only shows the 500gb HD /dev/sdb but none of the other, I can still fully see the HD on GParted but not on the installation, any ideas?

---

### Post by merlin371 on 2010-08-13
Anyone? :(

---

