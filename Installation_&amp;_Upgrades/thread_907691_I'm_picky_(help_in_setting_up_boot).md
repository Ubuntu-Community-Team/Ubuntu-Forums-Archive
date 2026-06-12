---
title: "I'm picky (help in setting up boot)"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by MillerD on 2008-09-01
Well I have already determined how my partitions will be set up.

Computer:

|| Vista (along with vista programs) | Recovery Partition ||

HDD1:

|| All other files of mine/not parents ||

HDD2:

|| Ubuntu split into many partitions ||

<h />

So what I'm asking about is how would I set it up so,
A. Vista is the default boot (as in waiting those 5 sec of doing nothing in the boot program brings up vista)
B. Have it so the boot doesn't even come up if the HDD with Ubuntu isn't hooked in.

Any help for how I could do this?

---

### Post by Partyboi2 on 2008-09-01
> A. Vista is the default boot (as in waiting those 5 sec of doing nothing in the boot program brings up vista)
You can make these changes in your /boot/grub/menu.lst after you have installed your sytstem.
[[COLOR=Blue]Here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc") is a link that explains how to change the default boot option
and [[COLOR=Blue]here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#timer") is one that explains how to change the timer if you are wanting to.

If you still not sure you can post your grub menu.lst and someone should be able to help.
```
cat /boot/grub/menu.lst
```

---

### Post by pofigster on 2008-09-01
Do you already have this all set up?
Installing Windows and Ubuntu to different hard drives makes for a difficult time.
If I remember correctly (and there's a how-to somewhere) what you need to do is remove every hard drive but the drive to have Vista and install Vista.  Then, make Vista the slave drive and plug in the Ubuntu drive and install Ubuntu.  This way Grub will correctly detect Vista and get grub set up.
Now, if you remove the Ubuntu drive, make Vista the master drive and it should boot into Vista no problem.
Then, do everything the post above suggested.

---

### Post by MillerD on 2008-09-01
Ok I should have been more descriptive. HDD 2 and 3 are external USB drives. 2 is lowspeed high capacity, with HDD 3 being fast read but somewhat low capacity. Currently I am already set up with Vista and programs on HDD 1, and files and some programs on HDD 2. Anything you can tell me now?

---

