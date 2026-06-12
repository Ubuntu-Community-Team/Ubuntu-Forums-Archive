---
title: "error updating from 8.04 to 10.04"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by megahost on 2010-04-23
I had originally posted this in installation and upgrade section, but it may be appropriate to move here since it has to do with the Lucid Lynx upgrade attempt. I still have not solved this problem.
Here it is

Alright, I have downloaded the upgrade for 10.04 and installed upgraded from my previous 8.04. Everything was working all fine until I had to reboot my pc. When I did i got some errors

Mount: Mounting none on /dev

It goes on to tell me that my UUID does not exist. Then it says

ALERT! Alert! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xx$ does not exist. Dropping to a shell!

It then drops to a very simple shell which has no flexibility and is very frustrating. Help is VERY appreciated, and I'd hate to to a reformat.

EDIT:

This is the full error message

Mount: Mounting none on /dev
boot args cat /proc/cmdline
check rootdelay =(did the system wait long enough?)
check root =(did the system wait for the right device?)
missing modules ( cat /proc/modules)
ALERT! /dev/mapper/debian-root does not exist
dropping to a shell.

---

### Post by nhasian on 2010-04-23
you could get the UUID for the partition with this terminal command:

```
sudo blkid
```

then:

```
sudo pico /etc/fstab
```

and correct the offending line.  its probably a good idea to backup your original fstab before editing it with this command:

```
sudo cp /etc/fstab /etc/fstab.backup
```

---

### Post by kansasnoob on 2010-04-23
It might be helpful to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

