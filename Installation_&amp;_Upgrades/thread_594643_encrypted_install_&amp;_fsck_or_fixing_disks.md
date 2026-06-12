---
title: "encrypted install &amp; fsck or fixing disks"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by duister on 2007-10-28
Hi ubuntu users,

I installed xubuntu using the option to use the complete disk and encrypted LVM wizard. This results in 1 small boot, and encrypted LVM.

I searched here, but didn't find my concerns.

What if the computer hangs (ofcourse this will never happend, but still) or i get a powerloss. Something mazy go wrong with my drive then.

i cannot just run fsck on my disks, because i am running from it. So, how to check or fix errors then?

---

### Post by Herman on 2007-10-28
The best way to run a file system check is to use a Live CD. The Ubuntu Gutsy Gibbon Live CD is the best, but any Live CD will do. [GParted -- LiveCD]("http://gparted.sourceforge.net/") is excellent.
If you are using Xubuntu because you have modest hardware then GParted LiveCD will be the best.

You can do this very easily nowadays, just start GParted, (it doesn't matter if it's GParted in Gutsy Gibbon or GParted in the GParted LiveCD.
All you need to do is right-click on the partition containing the file system you want to have checked, and click 'check' on the right-click menu.
If 'check is greyed out you might need to click 'unmount' first and then click 'check' later.
Then you need to click 'Apply', and then confirm 'Apply'
GParted will run a file system check on that partition for you.

When it's finished you should fully expand the 'details' box to read all about what has been done for you.

I am not sure if the fact that it is encrypted will affect anything, I imagine that will be okay, but I'm not sure. 

Regards, Herman :)

---

