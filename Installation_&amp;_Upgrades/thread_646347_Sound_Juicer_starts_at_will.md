---
title: "Sound Juicer starts at will"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by Bukran on 2007-12-21
Hi everyone!

I'd like to mention something curious (so to say) that happens after upgrading to Ubuntu 7.10 (Gutsy Gibbon). At any time, Sound Juicer thinks that I've inserted a music CD (when the unit is empty) and the following message pops up:

[INDENT]"Sound Juicer could not read this CD tracklist. Reason: can't read CD: track numbers must be within range 1..99" (sorry, error message translated from spanish).[/INDENT]

It would be nothing but annoying if it was just that, but the problem is: after closing that window, I can't work with the cdrom drive. "Disk mounter" on top bar shows the CD icon and there's no way of unmounting. I've tried removing Sound Juicer from Synaptic but then the program executing is the standard CD player.

In case it helps, this is an output of /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=2e29a79a-7b3e-4952-92de-ebf28185eed9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=e0a4d1d3-86a7-4009-a8dd-e71b7cb8755e none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
# /dev/hda1
UUID=98B0A384B0A36788   /media/windows  ntfs-3g user,auto       0       0
# /dev/hda2
UUID=42AA-FD19  /media/backup   vfat    user,auto,fmask=0111,dmask=0000 0      0
```

I often miss Feisty...

---

### Post by kyrox on 2007-12-28
I get the same problem.

I used envy to install the latest nvidia drivers. Everything was working great, but I wanted to play the game Frets On Fire and I read somewhere it might work if you install the latest drivers. However, the drivers didn't work very well. I got weird bugs so I decided to uninstall them (using envy). Now I use the generic drivers without the restricted drivers enabled and now suddenly sound juicer pops up every once in a while like you describe. Help... ? :)

I'm on a HP tx1020ea.

---

### Post by Guenter on 2007-12-30
same here with hardy (alpha2)

not doing anything unusual (suring, etc.)

---

### Post by balaji.ramasubramanian on 2008-01-13
Is there a solution to this? Any bugs on Launchpad for this? I'm facing this issue and it is annoying to find Sound Juicer trouble me like this. I have changed the auto-start program in the removable media (multimedia section) to gnome-cd instead. However I just don't know if it will be ok.

---

