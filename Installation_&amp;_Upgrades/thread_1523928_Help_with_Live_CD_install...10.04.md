---
title: "Help with Live CD install...10.04"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by greenpanner on 2010-07-04
hi. i am not sure if there are other posts like this but I searched and couldn't find anything that helped.

I finished  putting my tower together and went to install Lucid Lynx but it failed  to show graphics at first because(as I understand) it is a 2005 Albatron  K8X890 pro II MB with VIA chipset which has known acpi issues when  ubuntu boots up. Basically just an uncommon board??? So, I booted with  "noacpi" and it got me video and to the start installation/pick time  zone and then it wouldn't go any further, it just kept thinking...thats  where I'm at.

My BIOS is not current version I'm pretty sure but I can't update because no floppy drive installed...

Right now every time I let the CD Rom boot up my Live CD it takes  forever and says-

-------------on boot----------
Glib-WARNING **: getpwuid_r():  failed due to unknown get user id (0)

udevd[66}: worker [71] unexpectedly returned with staus 0x0100

udevd[66}: worker [71] failed while handleing  '/devices/pci0000:00/000:00:0f.1/host2/target2:0:0:/2:0:0:0/block/sda/sda1'

stdin: I/O error
stdin: error 0

-------------------------------

It is just really slow...sometimes I can get to LIVE desktop sometimes  it takes  forever...it won't even let me check for disk errors but it did work the first time and it said no errors found but I had a failed installation since then so, not sure.

Any help or suggestions appreciated...thanks in advance.

---

### Post by greenpanner on 2010-07-04
BUMP...I'm getting no views or replies??? Anything helps...

---

### Post by Rubi1200 on 2010-07-04
Hi,

there are a couple of options I can think of that might help.

1) look at the possible solutions mentioned in this post and see if they are applicable:

[http://ubuntuforums.org/showpost.php?p=9543761&postcount=2](http://ubuntuforums.org/showpost.php?p=9543761&postcount=2)

I am referring to the sections towards the bottom of the post.

2) try an older version of Ubuntu; in this case, download and burn to CD the previous version Karmic Koala (9.10)

If that works as a LiveCD then you know that there is an issue with your hardware in terms of the requirements for the current version (10.04)

Hope this helps.

---

