---
title: "install Ubuntu DHCP"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by arsidh on 2011-09-24
Guys, 
                 How to install Ubuntu over the network using network boot.

Regards,
arsidh

---

### Post by sanderd17 on 2011-09-24
Some more details please: what do you have as installation medium? What connection do you want to use (wireless or wired)?

---

### Post by arsidh on 2011-09-24
Hi sanderd17,
                        I have like 10 machine, where in i want to install ubuntu from a center server(which have the ubuntu installation image ) over a wired network (or say netboot). How can we do that. 

cheers

---

### Post by sanderd17 on 2011-09-24
A netboot will be no good option. It means that you have to download all files again for each machine. You'll better be off with a regular installation CD.

But if you want something easier, you can install it on one hard disk (with any method you want), configure it as you like. And afterwards, you can clone the hard disk on every machine you like. The setup will be the same.

The first harddisk can be an external one, or one of your machines. 

Note that you can only clone from and to hard disks that are not used for anything else at that time. So the OS you're using to clone can't be on those hard disks.

---

### Post by arsidh on 2011-09-24
Thanks for help, How can i clone , any tool i can use, please suggest

---

### Post by sanderd17 on 2011-09-24
If you work on a unix-like server and just connect two harddisks, you can clone with the dd command.

```

dd if=/dev/sdb of=/dev/sdc

```

The above will clone the complete contents of sdb to sdc. Watch out for typos.

You can also use the more graphical clonezilla.

---

### Post by arsidh on 2011-09-24
cool
Thanks for the help Sir :) appreciated

-Hanmant

---

