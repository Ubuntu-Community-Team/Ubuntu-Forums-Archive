---
title: "New Windows partition"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by HarveyBirdman on 2011-06-29
Hi everybody

I've been using Ubuntu for a while and its nice but I need to run some windows only applications now. I want to add a partition now and install XP on it. What is the easiest way to shrink my current partition and make a new one?

---

### Post by Quackers on 2011-06-29
Welcome to UF.
Will the installation be made from an installation disc or a recovery disc?
How many partitions do you have already?
Are they primary or logical partitions?
Give us a clue :-)

---

### Post by pjd99 on 2011-06-29
A few questions:

What are the applications in question?

Are there viable alternatives in the repositories/greater world?

Do you require the extra native installation? Can you use a virtual machine?

Can wine be used to run the windows programs in Ubuntu?

Can the programs be recompiled with winelib?

If you need to shrink your partition, backup all important data first. There is a gparted-live distribution available (bout 120MiB), burn it to a cd, boot from it then resize your linux partition and create the NTFS one. gparted is fairly intuitive.
Then install windows. MBR will be wiped, so dual boot will be lost. You'll need to reinstall grub. This can be done from the Ubuntu install cd.

---

