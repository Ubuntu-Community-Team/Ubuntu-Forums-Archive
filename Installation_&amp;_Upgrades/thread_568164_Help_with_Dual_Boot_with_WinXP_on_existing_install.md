---
title: "Help with Dual Boot with WinXP on existing installation of ubuntu and fedora"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by eva on 2007-10-05
Hi,

Am a newbie and I need some serious help. A little background first. I have a single hard disk with a dual boot of ubuntu feisty fawn and fedora. I am pasting below my partition table.

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          64      514048+  83  Linux
/dev/sda2              65        2614    20482875   83  Linux
/dev/sda3            2615        2933     2562367+  82  Linux swap / Solaris
/dev/sda4            2934        6120    25599577+   5  Extended
/dev/sda5            2934        4845    15358108+  83  Linux
/dev/sda6            4846        6120    10241406   83  Linux

Now, I want to remove fedora mounted on sda6 and in its place I want to install winXP (don't ask y).
I don't understand much about partioning. Would appreciate any help. 

Thanks in advance,
Best
eva

---

### Post by wolfen69 on 2007-10-05
you could reinstall xp on sda6, then you will have to reinstall grub. [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by lex1 on 2007-10-05
May not help but vmware player or workstation 6 is great for running xp or fedora

lex1

---

### Post by maybeway36 on 2007-10-05
VirtualBox can run Windows or Linux as a guest OS very well. (Just don't try BSD :P)

Anyway, if you need to add Windows on sda6 to the menu.lst, just add this stanza:
```
title Windows XP
chainloader (hd0,5)+1
savedefault
boot
```

---

### Post by eva on 2007-10-07
Thank you all. i already have virtual box with windows but doesnt solve my purpose completely. thanx lex1 i had tried vmware but found it little difficult to configure so gave up and got vitual box. But what I want to know is -

1. How do I remove fedora from sda6
2. Install WinXp on sda 6.as in how and where to say that winxp needs to be mounted on sda6.
3. I read here about NTFs and FAT 3. is that required? (i can do without sharing files between XP and Ubuntu.
4. Can someone please help with a detailed step by step procedure.

Ubuntu is my primary and production system, so i can't afford to make mistakes.

Please help me!

Thanks again

---

