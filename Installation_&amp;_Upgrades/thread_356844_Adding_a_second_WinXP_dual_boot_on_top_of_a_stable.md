---
title: "Adding a second WinXP dual boot on top of a stable installation"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by CELI-Nux on 2007-02-08
Hello everyone,

I'm currently faced with an architectural dilemma.  My portable system is currently stable with the following configuration (an 80 Gb HD with 5 partitions):

- Partition 1 (Drive C: ) - hda1 - (for WinXP - NTFS - 18 Gb)
- Partition 2 (unrecognized) - hda2 - (for Ubuntu - ext3 18 Gb - not recognized by WinXp)
- Partition 3 (healthy) - hda? - (for Ubuntu Swap space 1.5 Gb - not recognized by WinXp)
- Partition 4 (Drive D: ) - hda5 - (FAT32 18.5 Gb - for Data & pictures)
- Partition 5 (Drive E: ) - hda6 - (FAT32 18.5 Gb - for Backups & MP3s)

Everything is working perfectly in this configuration with Grub as the main loader since WinXP was installed first (Ubuntu second).

I now have to add a second WinXP to my original C: drive partition for professional reasons (hda1).

Hence, hda1 (Drive C: ) will inherit two boot partitions after a stable install.  

Has anyone done this before?  What are the issues and my avenues?  Any problems encountered?  What are the issues here?

Any feedback would be appreciated.

Regards
Domenico

---

### Post by confused57 on 2007-02-08
I haven't actually done this myself, but there's information in this link for grub entries with 2 different Windows OS installed on the same hd(see the hide & unhide options):

[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

The above will work only if you retain Linux & boot from grub...if you're installing the 2nd Windows over Ubuntu, I don't really know how Windows bootloader handles it.

---

