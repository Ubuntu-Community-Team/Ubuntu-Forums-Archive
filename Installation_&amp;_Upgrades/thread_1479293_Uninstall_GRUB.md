---
title: "Uninstall GRUB"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Nostigex on 2010-05-10
I installed Ubuntu over my windows partition but kept the other NTFS partitions that I use for storage. For some reason GRUB shows up with the option to boot into XP (which isn't there). How do I get rid of the boot menu completely so my computer boots straight into Ubuntu?

---

### Post by darkod on 2010-05-10
If another OS is detected, or more precisely boot files of another OS, the boot menu is created and an entry for that OS created.
Obviously ubuntu can detect XP boot files, or boot files belonging to recovery partition or similar.

For the newer grub2 which 9.10 and 10.04 use, first try running in terminal:

sudo update-grub

If that still reports XP found, it will also say on which partition. As long as it detects something, there will be grub menu and entry for XP.

If nothing else works, you could disable the file searching for other OSs, but have in mind that no new OS can be detected automatically after that. Lets see if that approach is needed.

---

### Post by Nostigex on 2010-05-10
I had already uninstalled GRUB. For some reason, after I installed the packages again, no more XP. Though, it goes through a really strange-looking boot-sequence now... black screen, flicker, black screen, flicker, then brief glimpse of ubuntu startup screen, then desktop. 

Whatever. :???:

---

