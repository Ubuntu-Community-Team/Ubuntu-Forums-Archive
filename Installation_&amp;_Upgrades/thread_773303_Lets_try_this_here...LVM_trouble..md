---
title: "Lets try this here...LVM trouble."
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by stuman on 2008-04-28
I installed ubuntu 7.10 with encrypted file system.  I swapped out the hard drive for a larger one, and now I want to add the extra space to the LVM.

dd copied whole system...no problem.

boot live cd.  gparted increase sda2.  no problem.

reboot live cd.  fdisk redefine sda5 to fill sda2.  no problem.

pvresize physical partition.  no problem.

lvresize...says no extents are available.  pvdisplay shows 48844 free.  what did I miss?

---

### Post by K.Mandla on 2008-04-28
I shifted this to Installation and Upgrades for you. I have a feeling more people with LVM experience will see it here.

Cheers!

---

### Post by stuman on 2008-04-28
I actually figured it out.

I was forgetting to pvchange -x y and to delete the swap partition, which was in the way, first.

I may post a list of what I did just because...while it is all still fresh in my mind.

I'm all good to go now with almost 300g encrypted working space on my notebook.  WIFI works great.  Sound even works (bit of a pain on Toshiba).

It only took me two years of linux in a vm under windows to get to the point of inverting the setup.  Now I have several client related windows vm's running under ubuntu 7.10.  Thanks.

---

