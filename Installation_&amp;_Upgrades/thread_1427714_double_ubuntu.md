---
title: "double ubuntu"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by jojom271 on 2010-03-11
i have a problem i have two ubuntu programs on my hard drive. i have old 9.4 and i installed new 9.10 in a partition. i was unable to get old 9.4 to work correctly and i installed new in fear of looseing pics and files. what do i do.

---

### Post by 2hot6ft2 on 2010-03-11
> **jojom271 said:**
> i have a problem i have two ubuntu programs on my hard drive. i have old 9.4 and i installed new 9.10 in a partition. i was unable to get old 9.4 to work correctly and i installed new in fear of looseing pics and files. what do i do.
Since you're calling it a program instead of an operating system. How did you install ubuntu?
WUBI, installed like a program in windows?
Real hard drive install to it's own partition?
Virtual Machine?

Is one a WUBI? The other you said to it's own partition.

---

### Post by Contra75 on 2010-03-11
I have somwhat similar problem - I think I installed Ubuntu 9.10 twice  - as a partition and in wubi. Why I think so? 1) on start-up I shall choose between ubuntu and windows and 2) after I choose windows, I again have to pick between Windows and Ubuntu. :confused:
What shall I do - I want only one ubuntu - actually only one thru Wubi, as I am still learning this new animal. How do I uninstall ubuntu I got into partition?

---

### Post by jojom271 on 2010-03-11
sorry operating system. is there a way to remove old with out hurting files and pictures

---

### Post by 2hot6ft2 on 2010-03-11
I have never used wubi so I'll let those that are familiar with that type of install help. Since I don't even know if a wubi install would show up in windows add remove programs and I don't want to give any advise that may mess you up. And it looks to me like the OP jojom271 and Contra75 may be doing the exact opposite of each other.

---

### Post by 2hot6ft2 on 2010-03-11
> **jojom271 said:**
> sorry operating system. is there a way to remove old with out hurting files and pictures
So they are BOTH hard drive installs?
Can you attach a screenshot of System > Administration > GParted so we can see if there are actually 2 installs and how they are partitioned.

Or are you going by there being more than 1 entry in grub when you boot up?

---

### Post by 2hot6ft2 on 2010-03-11
If you have 2 hard drive installs you can just browse to the other installs folders and copy what you want to save.

Places > (the other installs drive/partition) > home > yourusername
then you can go in all the folders in your home folder on the other install (like Documents, Pictures etc...) and copy what you want to the install you want to keep.

Once you have everything you want to keep off the install to be removed it can be removed and everything will be safe on the new install.

---

### Post by Contra75 on 2010-03-11
I had an option of uniinstalling ubuntu thru control panel->remove prog
Tried that, it said that ubuntu was uninstalled, but in fact nothing changed. It is still the way I descrribed above ....

---

