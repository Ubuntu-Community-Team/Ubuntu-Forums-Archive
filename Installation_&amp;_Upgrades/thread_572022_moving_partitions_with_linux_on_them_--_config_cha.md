---
title: "moving partitions with linux on them -- config changes check"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by gregconquest on 2007-10-10
I have read here what I can on moving partitions, but I still have a few questions:

1) If I insert a new partition on a drive above a linux install, not using Linux to do
this, how do I reconfigure the installed Linux to continue booting? The sdc2 linux will
have become sdc3 as a result on the new partition. My fstab is mostly configured already
to not use paths to mount volumes, I use uuid and label, but there is still something
else to be done. What is this? Edit the grub configuration?

Supposed answer:
edit the following -- updating paths/id's:
grub.conf
/boot/grub/menu.lst
   for gnome (ubuntu)
      sudo gedit /mnt/boot/grub/menu.lst
   or for kde (kubuntu)
      gksu kwrite /mnt/boot/grub/menu.lst
/etc/fstab
   for gnome (ubuntu)
      sudo gedit /etc/fstab
   or for kde (kubuntu)
      gksu kwrite /etc/fstab

Is this right? grub.conf is important also? Can I use uuid or labels in grub, or must I use the paths? These change when I alter partitions or even when I plug in a USB drive before booting into openSUSE.

2) If I take an image (bit copy) of a linux install, using BootIt NG in my case, and then
I paste that image to an entirely different partition, what do I need to do? Same as above?

3) uuid: this is supposed to be a unique identifier, but if I make an image of a partition, and then paste it elsewhere, I do end up with two partitions with the same uuid. Is there anyway to reassign uuid's?

I can do the above from three times/locations:
- edit config files before the shutdown prior to the move
- edit config files from the command prompt -- if i can get one.
- edit config files using another installation of linux on a different partition before
or after the move.

Which of these are preferable in these cases?

Thanks for any help.
Greg Conquest

keyphrases: moving partition, copying partition, moving partitions, copying partitions,
cloning partition, cloning partitions, not bootable, format

---

