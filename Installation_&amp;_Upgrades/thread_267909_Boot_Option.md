---
title: "Boot Option"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by chris_trinidad on 2006-09-29
Hello,
Is it possible to install Ubuntu to a 4Gb windows partition [the O/S is WIN XP Pro]on a laptop [P3 Dell Inspiron 8100, 512 RAM, 20G HDD - partitions: 10/5/5] without changing the windows MBR ?
I would like to access the Ubuntu O/S using the "grub" floppy.
Reason: I have had previous bad experiences with the MBR preventing access to the windows partition [for whatever reason] necessitating the re-build of the system.
Thanks for your help !
Chris

---

### Post by Kateikyoushi on 2006-09-29
Installing grub is not a must but it worked out of the box for me and I can dual boot on 2 of my computers.

You have to make 2 partitions one for swap and one for the OS.
A windows NTFS partition won't do.

---

### Post by orb9220 on 2006-09-29
Ubuntu needs to be on a linux partition like ext3 cannot be installed to a fat or ntfs partition.

The alternate install iso will give you control over grub or not to grub.
[http://www.ubuntuforums.org/showthread.php?t=233444](http://www.ubuntuforums.org/showthread.php?t=233444)

---

