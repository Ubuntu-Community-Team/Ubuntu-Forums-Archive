---
title: "Grub 2 recognizes partition as LVM"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by michel. on 2010-09-24
Hello,

 Originally I had a system with a Hardy 8.04 installation on a LVM  volume. And Grub legacy.
Later on I decided I did not want to use LVM, so I converted to a regular Linux volume (83) using dd, recreating a new 83 volume and dd'ing the data back into that partition (/dev/sda5).

All was well. The system booted, ran reliably and I thought LVM was completely gone from the system.

But now I installed Lucid alongside the old Hardy install. And much to my surprise, Grub 2 recognizes the old Hardy install as being on a LVM volume....But it's not. Anymore anyway...

It is only a minor problem, but it is irritating to see update-grub persistently detecting the old install as LVM and thus adding root=/dev/mapper/vgh-root to the boot parameter. So on each kernel upgrade I find myself manually editing /boot/grub/grub.cfg changing the root= kernel parameter to the correct value.

I checked if there where still any LVM traces left using lvdisplay,vgdisplay,etc and they all come up empty. I deleted the /etc/lvm directory from the Hardy install. I checked the manuals to see if I can override the update-grub to use LABEL but the there does not seem to be a way to do that. Set GRUB_DISABLE_LINUX_UUID=false  to force the default usage of UUID's but it still uses root=/dev/mapper/vgh-root

Anyone who can tell me how I can remove any old LVM leftovers, configuration or otherwise, from the old Hardy installation?
Or force GRUB2 to ignore it?

---

