---
title: "No Grub Post Install"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by jadacyrus on 2006-09-17
Okay, twice i've tried to clean install ubuntu (Xubuntu & Knot 3), each time GRUB never installed. There are no isntances of 'grub' in /boot. I've installed other Linux distros like opensuse and archlinux and the bootloader installs correctly, however using the LiveCD install method with Ubuntu does not correctly install grub. What could be the problem here?

It doesn't seem to be a problem with the specific version of Ubuntu. All Ubuntu LiveCD's i've tried before this have failed in the same way. However I had dapper isntalled on this machine previously, and I wanted to clean install over it, and this is when the problems arose.

And yes, i've checked the CD for defects.

---

### Post by ciscosurfer on 2006-09-17
If for some reason GRUB never got installed and wrote to your /boot partition or MBR, then you can always install it yourself through the repositories by issuing```
sudo aptitude update && sudo aptitude install grub
```

---

### Post by semakwetu on 2006-09-17
I recently bought a new 160Gb HD and had problems with GRUB not installing (even from the repositories) I figured that it was related to my partions and second drive.  If I stopped trying to put /home on my 2nd drive and let Ubuntu install using defaults to the new HD only then GRUB installed fine.

---

### Post by jadacyrus on 2006-09-17
Okay, i've got grub installed and setup, however when It goes to boot I get this:

 Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1). Please append a correct "root=" boot option. 

But in my grub menu.lst file I do have root=/dev/hda1 ro quiet splash... and I know for a fact the device is /dev/hda1

---

