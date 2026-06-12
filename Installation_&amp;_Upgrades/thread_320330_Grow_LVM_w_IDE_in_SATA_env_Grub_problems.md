---
title: "Grow LVM w IDE in SATA env: Grub problems?"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by jboehm on 2006-12-17
Hi

I'm running Edgy Server, if that matters.

I have 4 drives, 3 SATA and one IDE in slave to and DVD.  I am running the OS on the much faster SATA drives.  During the install I learned the HARD WAY that I must install the boot partition onthe first drive in the list. Since hd comes before sd (as in /dev/hdb and /dev/sda) I learned that I needed to unplug the IDE drive or GRUB would be in the weeds when I booted my new system.

So, now I'm pretty happy with my OS and I'm ready to plug the IDE drive back in and grow my LVM partition.

Do I need to worry about upsetting Grub?

Can you point me in the direction of a good how to for formatting a drive XFS then adding it to and existing LVM partition?

Any good GUI tools out their for doing this?

Thanks,
Jon

---

