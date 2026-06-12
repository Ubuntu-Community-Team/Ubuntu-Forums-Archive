---
title: "deleting a second Ubuntu install"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by chrisetlo on 2011-07-29
Hi,

I'm running 11.4 in a dual boot with windows vista.  

I accidentally filled up my ubuntu partition while doing some data recovery.  The associated errors left me unable to load ubuntu.  I was also unable to delete the excess data using terminal, so I installed a second copy of ubuntu, and freed up enough space to get running again.

I then used gparted to delete the redundant ubuntu partition.

That didn't work.  Grub was unable to boot into anything.  So, I reinstalled the second copy of ubuntu.  

How do I get rid of the redundant copy of ubuntu, without screwing up grub?

Thanks!

---

### Post by Quackers on 2011-07-29
Install gparted (if you haven't already) via synaptic package manager then open it and post a screenshot of what it shows please.

---

### Post by oldfred on 2011-07-29
Can you boot into the install you want to keep? If not sudo update-grub to find old install.

If so you will need to install grub2's boot loader from the install you want to keep into the MBR so you boot it, not the install you want to delete. When you delete the second install the grub2 boot loader in the MBR is looking for the rest of the boot files in the now missing install. You just need the grub bootloader to be looking for the files in the version you want to keep.

Boot into your permanent install:
#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

Then using the screenshot Quackers suggested we can recommend how to houseclean the extra partitions.

---

