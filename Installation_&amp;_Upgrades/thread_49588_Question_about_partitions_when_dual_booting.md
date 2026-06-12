---
title: "Question about partitions when dual booting"
date: 2005-07-16
forum: Installation &amp; Upgrades
---

### Post by cajunaggie on 2005-07-16
I'm currently running Ubuntu 5.04. My drive is currently split into three partitions, two 40 GB and one 80 GB. Ubuntu is installed on the first partition. I'm starting to miss my games and I have a copy of Windows I would like to try dual booting. Forgive a n00b his ignorance, but does Windows have to be on the primary partition? I've heard different things from different sources.

---

### Post by not_yet on 2005-07-17
> but does Windows have to be on the primary partition? I've heard different things from different sources.

wondose needs to be in "a" primary partition, as opposed to a logical

from what I've read its always easier to install ubuntu after windows, although it is possible (but no as easy) to do it the other way around.

if you install windows after ubuntu,  grub  can get messed up

heres a link  on how to restore grub [http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

cheers

---

### Post by WildTangent on 2005-07-17
i believe windows need to be on the first partition for its boot loader to work correctly. i may be wrong, ive never tried it myself

-Wild

---

### Post by jerome bettis on 2005-07-17
^ nah it's hda2 on my computer.  install ubuntu, have your windows partition formatted as fat32.  don't use ntfs it's a pain with linux.  windows should install to that partition, when it asks to overwrite the mbr let it.

now you'll be able to boot into windows, but linux will be sitting around doing nothing.  you need to restore grub.  several ways of doing this, that link should help.  if you need help just ask i've done it 1000 times.

after you've restored grub you'll be able to boot linux but windows will be sitting around.  then you just need to add a menu option to grub for windows.  here's mine:

title Windows XP
map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
rootnoverify (hd0,1)
chainloader +1

notice the (hd0,1) . here 1 is your windows partition number minus 1.  hda2 - 1 = 1 .  grub starts at 0, not 1 like linux does.  the two map lines virtually swap your windows partition with the first one, so grub tricks windows into thinking it has the first partition, when it really doesn't.

---

