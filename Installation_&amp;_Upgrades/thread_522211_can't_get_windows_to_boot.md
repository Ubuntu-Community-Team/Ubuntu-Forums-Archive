---
title: "can't get windows to boot"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by muddymind on 2007-08-10
HI!

I wanted to uninstall ubuntu and then in windows manage the partitions to reinstall it... the problem is when I made fixmbr to install windows mbr with windows CD It gives me an error saying something like "Error loading operative system"... How can I get my windows back?!?!? I don't want to uninstall it...

---

### Post by Mark Phelps on 2007-08-10
When you installed Ubuntu, how did you partition your disk -- did you shrink XP to fit as part of the installation? Or did you use a third-party product to shrink the partition first?  Also, where did you tell it to install GRUB -- mbr of the hard drive, or Linux partition?

---

### Post by muddymind on 2007-08-10
I used acronis to resize the partition... I let the ubuntu installer use automatically the linux partition to put mbr....

now I made fixboot c: and then fixmbr... that should do it... but it didn't :(

help plz....

---

### Post by muddymind on 2007-08-10
I tried windows recovery but it gives me the same error :S I don't know at else to do :(

---

### Post by logos34 on 2007-08-10
try booting back into the recovery console on the XP cd and do


**chkdsk /r**

or

**chkdsk C:/r**

---

### Post by muddymind on 2007-08-10
I had to reinstall ubuntu... What if I wanted to get rid of ubuntu?!?!?

---

### Post by muddymind on 2007-08-10
~~up~~

---

### Post by merlinus on 2007-08-10
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

-merlin

---

### Post by muddymind on 2007-08-10
thank you :) I managed to do a safe windows mbr restore :)

---

