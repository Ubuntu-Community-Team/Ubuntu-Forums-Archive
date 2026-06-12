---
title: "Win Xp beside Ubuntu"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Hogeyfur on 2010-05-25
I need to reinstall Win Xp on my system.
 
I'm sure Win Xp wont "notice" the linux partition on my drive and once installed will boot straight into Win Xp as if its the only OS installed 
 
Can i reinstall GRUB throught Win Xp so i can then boot in to both partitions or will i have to do something else????
 
Any help will be appreciated

---

### Post by darkod on 2010-05-25
No, you can't. You will have to use the ubuntu cd and boot into live mode, and reinstall grub to the MBR from there.

Depending which version of grub you are using, you need to use cd for 9.04 or earlier for grub1, or 9.10 and beyond for grub2.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by lechien73 on 2010-05-25
The best thing to do would be to boot in from a Live CD to restore Grub.

The [instructions here]("http://ubuntuforums.org/showthread.php?t=1014708") might help.

---

### Post by Hogeyfur on 2010-05-25
thanks fo the info guys i'll try it when i get home

---

