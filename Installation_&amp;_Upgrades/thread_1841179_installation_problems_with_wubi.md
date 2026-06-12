---
title: "installation problems with wubi"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by ryanpl77 on 2011-09-08
i have asus p6t motherboard with intel i7. i downloaded wubi under windows7. when i restart the screen remains black and goes directly into windows with no option of choosing os. I need help figuring out what i need to do to get this to work.

---

### Post by Bucky Ball on 2011-09-08
You don't get to choose OS. You need a full dual-boot, hard drive install for that. Ubuntu wubi install should be with your other programs on your Win system. It is just like installing another Win application, not a full-blown install of Ubuntu, and intended to try out Ubuntu to see if you like (not a permanent install). ;)

I would advise booting from the install CD, 'Try Ubuntu', see how it goes and if you like, then clear some space and install to the hard drive. You will have better Ubuntu experience that way than Wubi or running from the CD.

---

### Post by bcbc on 2011-09-08
Right click Computer, Properties, Advanced system settings, Startup & recovery settings. Check the "time to display operating systems" is not zero. Make it 10 if it is.

---

### Post by fdrake on 2011-09-08
when booting keep pressed the "SHIFT" key untill you see the grub menu.

---

### Post by Mark Phelps on 2011-09-09
> **ryanpl77 said:**
> i have asus p6t motherboard with intel i7. i downloaded wubi under windows7. 

Did you actually install it? Or did you only download it?

Disagree with the claim that a wubi-install is not a full version of Ubuntu -- it IS.  It only uses Windows to install.  When you launch it, it's running the same Ubuntu version as if you installed to a separate partition.

ALSO, if you did NOT install it, and are considering the regular dual-boot install (i.e., separate Linux filesystem partition), then BEFORE you do that, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will come in handy later, should you need to repair the Win7 boot.

Should you decide to do the dual boot, do NOT use the Ubuntu installer to shrink the Win7 OS in a side-by-side setup.  That runs the risk of corrupting the Win7 OS partition.  Instead, use the Win7 Disk Management utility to shrink the Win7 OS partition, and then use Manual partitioning to install Ubuntu.

---

### Post by Bucky Ball on 2011-09-09
> **Mark Phelps said:**
> 
Should you decide to do the dual boot, do NOT use the Ubuntu installer to shrink the Win7 OS in a side-by-side setup.  That runs the risk of corrupting the Win7 OS partition.  Instead, use the Win7 Disk Management utility to shrink the Win7 OS partition, and then use Manual partitioning to install Ubuntu.

+1. Defrag two or three times (at least once) is good idea, too. I generally use something a little gutsier than the Win defragger (Power Defragger I think it is called and open source from memory, been awhile).

---

### Post by Frogs Hair on 2011-09-09
> You don't get to choose OS. You need a full dual-boot, hard drive install for that. Ubuntu wubi install should be with your other programs on your Win system. It is just like installing another Win application, not a full-blown install of Ubuntu, and intended to try out Ubuntu to see if you like (not a permanent install).A Wubi installation when installed  offers the Ubuntu and Windows option from the windows boot loader . After Ubuntu is selected , Grub opens and the kernel options are displayed .   It is not a case of booting into Windows  and starting Ubuntu like a windows program .

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by ryanpl77 on 2011-09-09
is it possible to have ubuntu and windows on the same hard drive? there are programs i use that are not offered for linux.

---

### Post by fdrake on 2011-09-09
> **ryanpl77 said:**
> is it possible to have ubuntu and windows on the same hard drive? there are programs i use that are not offered for linux.

dual booting with ubuntu in 2 different partitions. but a wubi install should be good enough and easier to manage in my opinion. I think something went wrong with your install. did you try to do what I said in my previous post. if that does not work, boot in windows , un-install wubi, and reinstall it again. during installation if you see any errors please post them here.

---

