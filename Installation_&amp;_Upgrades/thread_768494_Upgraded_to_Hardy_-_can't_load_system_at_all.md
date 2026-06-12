---
title: "Upgraded to Hardy - can't load system at all"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by waldron on 2008-04-26
Did an upgrade to hardy yesterday. Partway through the installation stalled, and there was an icon at the top of the screen which said "unable to get data". 

Switched off the pc and tried to reboot, but the system won't come up. Went back to a previous checkpoint, which says that it can't detect my graphics card and is running in low resolution. I can enter my username and password, but then just get a blank screen.

Thank goodness I still have Windows XP. I was happy with converting to Ubuntu until this happened.

---

### Post by NilsE on 2008-04-26
Sounds like you may have had a read error on the cd when you installed.  Try to re-burn the cd at a slow speed like 4x and re-install

---

### Post by waldron on 2008-04-26
I didn't install from a CD. I did an upgrade from Gutsy 7.10.

---

### Post by chek2fire on 2008-04-26
Try recovery mode from grub and from there try to fix xserver.

---

### Post by waldron on 2008-04-26
@chek2fire.
I've tried recovery mode from grub. It shows a few items as [Fail], then "Kernel.maps_protect" and "vm.mmap_min_addr" as 'unknown keys'.
I then get a prompt
   root@xxxxxxxx:~#

That's where I am stuck, as I have no idea what to do next.

---

