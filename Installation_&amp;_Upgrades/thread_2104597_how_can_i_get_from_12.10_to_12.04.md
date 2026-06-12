---
title: "how can i get from 12.10 to 12.04"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by gamezoid123 on 2013-01-13
okay i'm kinda new to Ubuntu and i installed 12.10. it's been pretty buggy and i would like to install 12.04. now i know there are 2 ways of doing this. i could take Ubuntu off. but I've heard that would also remove grub so i would have to reinstall windows as well (i'm using a dual boot. and i don't know if it would stop me from running windows because windows is on a totally different drive from Linux)or i've heard there is a another option, downgrading. my dad says i could find a way to downgrade from 12.10 to 12.04. the only problem is i don't know how, so which of the 2 options is the better one. reinstallation or downgrading. ]

i know i probably made this more confusing then i needed to but any answers would be wonderful. thanks in advanced.

---

### Post by howefield on 2013-01-13
There is only one realistic way and that is a clean install. You can install over the partitions/disks that 12.10 currently resides on.

---

### Post by Elfy on 2013-01-13
You need to reinstall with 12.04.

Once you've started you can use the 'Something Else' option at the partition stage to install over the top of the existing install. 

Alternatively try a thread or two about things you have issues with :)

---

### Post by darkod on 2013-01-13
First of all, if you delete the ubuntu root partition that will delete the grub config files, so the grub bootloader will be broken. You will need only to restore the windows bootloader to the MBR of the disk, NOT reinstall windows again. In this case it's better to restore the bootloader first, and only after you are sure windows is booting, delete the ubuntu partition.
If you have two disks, you might actually have windows bootloader on the other disk in which case it doesn't matter what you do with the ubuntu disk. Simply set your bios to boot from the windows disk and it should work.

But, for the purpose of your question, getting to 12.04, there is no way to downgrade. You will have to make a clean installation of 12.04. You can do that even without deleting the ubuntu partitions, simply use the manual partitioning method (Something Else), and reuse the same partitions. You will need to select each individual partition you want to use, click the Change button below, and set what to use it as, filesystem and mount point. The install will write new grub connected to the new install, so you will not get into a situation of having grub on the MBR but no ubuntu partition (broken grub).

---

### Post by gamezoid123 on 2013-01-13
thanks  guys this helped alot.:D

---

### Post by stber321 on 2013-01-13
there was a time when i tried to downgrade, i wrote a weird script that changed the repos then tried reinstalling everything, than going into an archive of the older version and started to replace all my config files and change the name everywhere. it created an mess and does not work. do not try it. it is a very BAD idea to try to downgrade without just doing a fresh install. it may be possible now, i have not looked into it as i am primarily using arch now. but it is still going to be a headache. it is best just to do a fresh install. before you wipe your system i just want to remind you about ```
dpkg --get-selections
```. often people forget they can do that

---

