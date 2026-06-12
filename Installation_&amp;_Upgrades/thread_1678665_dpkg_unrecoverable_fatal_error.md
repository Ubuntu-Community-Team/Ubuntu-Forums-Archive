---
title: "dpkg: unrecoverable fatal error"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by gadikas on 2011-01-30
```
sudo apt-get upgrade
..
...
.... Lots of text ...
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `grub-common': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
```Anyone have an idea of what is wrong?

---

### Post by nerdy_kid on 2011-01-30
um that looks bad, really bad.  Someone correct me if I'm wrong, but I think your disk might be failing/failed.

what i would do is

```

sudo touch /forcefsck

```

and reboot to check your filesystem for errors.

---

### Post by gadikas on 2011-01-30
Ok i  will do it
The machine  has no screen, it will  save a log somewhere?
I  reinstalled ubuntu from  a USB to CF  card because of problems with  the file system :lolflag:

---

### Post by nerdy_kid on 2011-01-31
> **gadikas said:**
> Ok i  will do it
The machine  has no screen, it will  save a log somewhere?
I  reinstalled ubuntu from  a USB to CF  card because of problems with  the file system :lolflag:


lol, yeah it will leave a log in /var/log/fsck/

---

### Post by gadikas on 2011-01-31
grrr new problems :/
```
magnus@MediaHubb:/var/log/fsck$ sudo cat checkfs
[sudo] password for magnus:
magnus is not in the sudoers file.  This incident will be reported.
magnus@MediaHubb:/var/log/fsck$

```

---

### Post by nerdy_kid on 2011-01-31
yeah I would start backing any files up that you need...

you should be able to get in by booting in recovery mode (you need a screen though...) and doing

```

sudo adduser USERNAME admin

```

but if your whole system is crashing, which is what it sounds like, then it wont do you too much good for very long.

---

### Post by gadikas on 2011-01-31
Yes. Is there a way to find out what part of a new computer that is failing. 
First i had grub2 problems whit my USB disk so i replaced it whit a sata to CF card adapter and a Adata 8gb CF card. 
And now i get more problems of failing grub2......
Ether i am extremely unlucky or it was never the fault of the USB disk from the beginning. 
Going to work now and do not have time to do any "hacking" on my router. I come  back tomorrow. 
I just  want to say I really appreciate the  help I get here.

---

