---
title: "Installation of Ubuntu 8.04 killed grub of 9.10"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by fitzefitzefatze on 2010-04-16
Hi,

I installed Windowz XP at first and then Ubuntu 9.10. Grub offered to choose between these two. Now I intalled Ubuntu 8.04 over Windowz but now I am not able to choose between these two systems. 
Ubuntu boot-Partition also uses ext4 which I can't mount under 8.04 so I don't know what to insert into the menu.lst of 8.04. Besides I would prefer to use Grub (2?) of 9.10
8.04 is not important for me, but 9.10 is. The partition table looks like this:

|hda0|hda1|hda2|
|8.04|Swap|9.10|

How can I boot 9.10 again?

Cheers!

---

### Post by zvacet on 2010-04-16
[Reinstall grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD") with Karmic live CD.

---

