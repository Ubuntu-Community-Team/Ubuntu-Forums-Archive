---
title: "Arch no longer listed in GRUB following upgrade"
date: 2012-07-25
forum: Installation &amp; Upgrades
---

### Post by wilberfan on 2012-07-25
I did an upgrade this morning on my 12.04, 64-bit install.  This afternoon when I tried to boot into my Arch install--it was no longer listed. :(

A "sudo update-grub" finds everything BUT the Arch install...:

> $ sudo update-grub
[sudo] password for wilberfan: 
Generating grub.cfg ...
using custom appearance settings
Found background image: /usr/share/images/grub/Plasma-lamp.tga
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Linux Mint Debian Edition (1) on /dev/sdb6
done

(Hmmm.  Time to klean out some kernels!)  ;)

Suggestions?

---

### Post by bohemian9485 on 2012-07-25
Can you see your Arch partition from Disk Manager or GParted?

---

### Post by wilberfan on 2012-07-25
> **bohemian9485 said:**
> Can you see your Arch partition from Disk Manager or GParted?

Yep.  Shows up fine in gparted...  One Archer reported the same problem:  

> I found that when I mount the Arch / partition in Ubuntu, then run update-grub, it finds Arch and puts it on the menu.  (and Arch boots fine).  Then if I unmount Arch / and run update-grub, and it doesn't find it again.

---

### Post by oldfred on 2012-07-26
Some reported the same issue with Fedora. Fedora normally installs to lvm, so in Ubuntu you have to add the lvm2 driver. But you still have to mount the Fedora for grub2's os-prober to see it.

Is the arch in a non-standard formated partition? Grub uses mod files to add code for anything non-standard as grub is more limited in drivers, but I do not then think it can find anything non-standard unless you mount it first.

---

### Post by wilberfan on 2012-07-26
> **oldfred said:**
> Some reported the same issue with Fedora. Fedora normally installs to lvm, so in Ubuntu you have to add the lvm2 driver. But you still have to mount the Fedora for grub2's os-prober to see it.

Is the arch in a non-standard formated partition? Grub uses mod files to add code for anything non-standard as grub is more limited in drivers, but I do not then think it can find anything non-standard unless you mount it first.

My Arch partition is ext4--is that what you meant? :confused:

I would argue that something in todays Ubuntu update (upgrade) changed. Everything was fine yesterday...

---

### Post by oldfred on 2012-07-26
I am current on updates and do not remember anything that should cause that type of issue. Other than the Fedora comment have not seen anyone else with issue, but not many posters have Arch.

I have so many old  installs and only boot a few, so I turn off os-prober and copy in a 40_custom to boot those other systems that I may want.

---

