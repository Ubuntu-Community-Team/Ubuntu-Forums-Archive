---
title: "[SOLVED] 2.6.27-2 won't load - exits to initramfs prompt."
date: 2008-09-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gtdaqua on 2008-09-08
I upgraded from Hardy to Intrepid Alpha 5.

The new kernel wont load - exits to initramfs prompt

The error is like:

```

check root = bootarg cat /proc/cmdline
or missing modules, devices : cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/xxxx-xxx... does not exist.
Dropping in to a shell!

```

The other kernels work. Verified the entries in fstab and menu.lst - the root device is correctly specified. So it cant be problem a with menu.lst or fstab. 

What else could it be?

---

### Post by ronacc on 2008-09-08
the first thing to try is remove quiet and usplash from the bootline and see what happens usplash has had some problems , also check the uuid of / and if you have a seperate /home partition check that one also grub sometimes  writes the wrong uuid even though the device is correct .

---

### Post by gtdaqua on 2008-09-09
I tried doing /dev/sda1 in grub which is root and btw, the UUID is correct.

Should I report this as a possible bug?

---

### Post by gtdaqua on 2008-09-09
I was getting something like this on the console when 2.6.27-2 kernel was loading.

```

ata2.00: status: {DRDY ERR} ata2.00: error: {UNC} ata2.00: exception Emask 0x0 SAct 0x0 SErr 
...
...
...
Waiting for root file system
...


```

The other kernels simply load.

---

### Post by cdtech on 2008-09-09
> Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/827cbda3-51a0-4e5d-a399-a90cef8c5514 does not exist. Dropping to a shell !

Check out this thread about the same issues as you:
[http://ubuntuforums.org/showthread.php?t=649135](http://ubuntuforums.org/showthread.php?t=649135)

---

### Post by gtdaqua on 2008-09-15
Removed and reverted to 8.04. 

Did a fresh upgrade today and the kernel is 2.6.27-3-generic and this error does not appear anymore.

---

