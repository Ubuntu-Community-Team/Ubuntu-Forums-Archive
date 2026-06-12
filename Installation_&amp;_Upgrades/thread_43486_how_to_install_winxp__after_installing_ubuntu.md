---
title: "how to install winxp  after installing ubuntu?"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by icecube76 on 2005-06-22
i have a HP ze4900 laptop running ubuntu .i thought that i dont need widows any more . so i removed it compleatly.
few days ago i bough streets & trip 2005 and i need to install it on my pda .
ican do that with windows only .
andy idea how to install windows on a system ruuning linux 

regards

---

### Post by Dragonfly_X on 2005-06-22
Did u partition u'r HD before installing linux?

---

### Post by icecube76 on 2005-06-22
no i did not

---

### Post by GeneralCody on 2005-06-22
Consider using Vmware.
U can download a trial at [www.vmware.com](www.vmware.com),
and we all know about serials...

 :)

---

### Post by XDevHald on 2005-06-22
[off topic] 

This is way off topic, but if you could please make the subject titles not starting with "**how to**" but with a "**how do I**". Reason for this is so that the users do not get confused with the Tips & Tricks Forum(s) for Warty and Hoary.

Thanks :)
[/off topic]

---

### Post by mingus on 2005-06-22
[QUOTE=icecube76]i have a HP ze4900 laptop running ubuntu .i thought that i dont need widows any more . so i removed it compleatly.
few days ago i bough streets & trip 2005 and i need to install it on my pda .
ican do that with windows only .
andy idea how to install windows on a system ruuning linux 

regards[/QUOTE]

Two options . . .

The usual would be to make a backup of Ubuntu, repartition the drive, reinstall Windows on the first partition, restore to the new Ubuntu partitions from the backup.

A second approach is to shrink an Ubuntu partition enough to make room for Windows, install W$ on that partition, mark the Ubuntu /boot partition as "bootable" in the partition table, and in the grub /boot/grub/menu.lst file use a chain-loader stanza to boot Windows from its partition.  You would want to verify this elsewhere (I'm a tad rusty on this one), almost positive this works with XP, less so earlier vsns of W$.

If you had another HDD, you could install XP there and use the second method, too.

---

### Post by icecube76 on 2005-06-22
thanks for your reply
i think i'll backup ubuntu and restor it after installing windows
what backup method can i use?
w'll norton gost work,

regards

---

### Post by mingus on 2005-06-22
[QUOTE=icecube76]
what backup method can i use?
w'll norton gost work,[/QUOTE]

Ghost *should* - but if your current Ubuntu is important, I would use a second method, too.

Ghost is going to create a bit image.  When you restore from an image, you are just laying bits down on a specified location on the disk, not restoring the files and rebuilding the tree as you go.  So it must work *just so* or you are hosed.  I've heard of problems, although usually everything is fine.

So, if important, I would tar Ubuntu.  You can find a howto, I think in the forums, about using tar for a backup and how to restore from it.

---

### Post by icecube76 on 2005-06-23
i'll try the tar method ,,,,,,,, :???:

---

### Post by afonic on 2005-06-23
[QUOTE=icecube76]i'll try the tar method ,,,,,,,, :???:[/QUOTE]
 As the previous user suggested I'd try VMware. If you just need to run a program here and there it's the best choice.

---

### Post by mingus on 2005-06-23
[QUOTE=icecube76]i'll try the tar method ,,,,,,,, :???:[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+howto](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+howto)

Note the author's remarks re Ghost . . . I cannot comment, no exp w/Ghost on Linux.  Surprising, should not do that.  In any event, it's a caution worth considering.

---

