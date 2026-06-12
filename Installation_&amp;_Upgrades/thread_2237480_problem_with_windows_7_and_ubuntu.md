---
title: "problem with windows 7 and ubuntu"
date: 2014-08-02
forum: Installation &amp; Upgrades
---

### Post by mahshid2 on 2014-08-02
hi
i want install ubunto when i have window 7
after installing ubunto windows can't load and come blue screen page
how i can fix theme??
 :(
i need windows :(

---

### Post by hdi on 2014-08-02
Hi,
you can use Virtual Software to run one of them inside another.

---

### Post by mahshid2 on 2014-08-02
but it's late for this action
my windows don't load
my ubuntu  don't delete completely
i need computer for next classs in tomorow :(

---

### Post by ajgreeny on 2014-08-02
You could try **Boot-repair** from my signature below.

---

### Post by yancek on 2014-08-02
You haven't actually posted enough information to get any help.  If you are getting the Ubuntu bootloader menu and select windows and then get a blue screen and it doesn't boot, you have messed up your windows boot files somehow.

When you installed Ubuntu, you had several options as to the type of install.  Do you remember which you selected?  How are you trying to delete Ubuntu?  You can delete the partition it is on but Ubuntu is an operating system, not an application so it is not something you can delete as you do an application.  Does this mean you can no longer boot Ubuntu either?  If you still have the Ubuntu installation DVD/flash drive, boot it and run this command:  sudo fdisk -l(Lower Case Letter L in the command) which will output some information you can post here.  Someone may be able to help then.n

---

### Post by Mark Phelps on 2014-08-02
If boot-repair works, you will be OK; but if it does not, you need to consider doing a boot loader repair from a Win7 Repair CD -- which you could have probably made on your PC, had you not rushed into installing Ubuntu without asking here first.  Now, you can download an ISO image of that and burn a CD from it, but you need a working machine and you will need to purchase the ISO image online.

---

