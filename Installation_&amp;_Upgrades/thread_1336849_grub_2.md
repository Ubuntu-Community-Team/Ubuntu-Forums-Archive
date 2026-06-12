---
title: "grub 2"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by wilburg on 2009-11-24
I have two identical hard disks with XP and 9.04 on one (hd0), /dev/sda and a new installation of 9.10 on (hd1), /dev/sdb.

I have reinstalled grub several times including from chroot. It installs without errors but on boot gives a 'grub rescue>' prompt. lt shows (hdo) and 'Cannot get C/H/S values'. Set shows the correct UUID and root=(hd1,1). All files are visible and accessible on sdb. I have checked grub-update and it is working correctly. The devices file also looks correct.

Where do I put the C/H/S information and why would the second disk need *it while the first does not?*

---

### Post by oldfred on 2009-11-25
Is your system old or is the BIOS setting wrong? I just happened to be reviewing my motherboard manual and one of the IDE settings was auto, none, manual where under manual you set the CHS cylinder, head, & sector settings. 

At least on my motherboard it looks like a system setting not an individual setting but mine is in auto so I am not sure. I do have two channels and they seem to be different, so if the drives are on different channels they may have different settings.

Some very old drives have to have the boot at the beginning of the drive.
 list of BIOS hard disk limits:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

---

### Post by wilburg on 2009-11-25
Thank you. Changing the hard disk to auto fixed the grub2 boot problem.

Many thanks.

---

### Post by 73ckn797 on 2009-11-25
Ignore[COLOR=Navy][COLOR=Red]
[/COLOR][/COLOR]

---

