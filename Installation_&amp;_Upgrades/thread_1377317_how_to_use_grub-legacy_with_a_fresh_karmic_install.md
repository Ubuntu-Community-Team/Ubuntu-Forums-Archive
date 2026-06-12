---
title: "how to use grub-legacy with a fresh karmic install ?"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by v41 on 2010-01-10
Does the karmic install CD (or alternate CD) have an option to use grub-legacy with a fresh install, or is it necessary to uninstall grub2 and then reinstall grub-legacy?  Also, does grub2 affect the MBR (master boot record) ?

---

### Post by oldfred on 2010-01-10
I do not think the cd's have the capability to down grade grub. You have to totally uninstall grub2 and reinstall grub legacy. Grub2 is installed in the MBR to boot grub2, so that also has to be changed.
Grub2 works for most people, but is new & different, why do you want to revert?

HowTo: Revert from grub2 to Legacy Grub. 
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by v41 on 2010-01-10
> **oldfred said:**
> I do not think the cd's have the capability to down grade grub. You have to totally uninstall grub2 and reinstall grub legacy. Grub2 is installed in the MBR to boot grub2, so that also has to be changed.
Grub2 works for most people, but is new & different, why do you want to revert?

HowTo: Revert from grub2 to Legacy Grub. 
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Oldfred,  thanks for the confirmation that Grub2 alters the MBR.

My reason for avoiding grub2 is that I'm concerned it might mess up my multi-boot system.
I'm currently using Refit and Grub to triple-boot OSX 10.5, Jaunty and Intrepid.
I'm hoping to replace Intrepid with Karmic, so the upgraded system would use
Refit, Grub for Intrepid and Grub2 for Karmic.  I'm not sure whether the MBR can
simultaneously handle both Grub and Grub2, or whether Refit is compatible with Grub2?

---

### Post by v41 on 2010-01-10
Oldfred,  the link in your post mentions that the Alternate CD has an option to not install a bootloader.  That's what I'm looking for!   I can then install the grub-legacy package.

---

