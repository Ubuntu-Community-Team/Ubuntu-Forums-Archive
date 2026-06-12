---
title: "The alternate cd really needs a little update"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by CHUCKYCHUCK on 2008-05-12
Hi !

I've just installed Hardy Heron using the alternate cd ( because i don't want to install Grub on the master boot record but on another partition )

When i got to the Grub setup step, the help text tells me :

example :
(hd0,1) or /dev/hda2 for the 2nd partition ofthe 1st hard disk

Cool ! That's exactly where i want to install my grub, so i type in /dev/hda2, well impossible to install grub, i had a nice error message ..

Tried several more times, but it just cannot install on the /dev/hda2 ..
So i gave up and i installed it on the master boot record .. and it worked !!

Just after the 1st reboot, i really wanted to understand what happened, so i ask fdisk ( fdisk -l ), and then i realized that partitions were renamed !!!
now /dev/hda2 is /dev/sda2 ...

Could developers update those help messages ??
It may seem not very important , but i think it would save some people to screw up their ubuntu installation ... ( some people might have cancelled their installation instead of installing on the mbr as i did ... )

thanks

---

### Post by bapoumba on 2008-05-12
Salut !
May be look at the bugs on launchpad regarding grub. I found a few, but not sure which one is related to yours. What was the exact error you got, if any?

---

### Post by CHUCKYCHUCK on 2008-05-12
there isn't any bugs, it's just that the help text needs to be updated ( the partitions are now named /dev/sda and not /dev/hda so this can lead to mistakes ... )

---

### Post by bapoumba on 2008-05-12
Well, in this case you should report a bug against the alternate cd or the debian installer :)

---

