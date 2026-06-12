---
title: "Failed to Upgrade"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by ryy705 on 2009-12-09
Hello, 
I tried to upgrade to 9.10. It downloaded all the packages, installed them, then it said that the upgrade failed and and it will now execute the recovery process.

I rebooted the computer and this is the message I get:
```

init: ureadahead main process (2689) terminated with status 5
mountall:/proc: unable to mont: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2690) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
Control-D will terminate this shell and re-try.

```

Hitting Ctrl-D generates the same message.
This is a Dell Inspiron 1501 laptop.  I have Vista and Kubuntu installed on it.

Would anyone know what I have to do next?  I am Stumped.  Googling the error was not fruitful. 
Please help.

---

### Post by ryy705 on 2009-12-10
Hello, 
I am trying to run the upgrade from the command prompt.
But it seems that I can't access the internet from the command prompt.  Is there a way to do so?
The following is the result of fdisk -l.  Shouldn't there be an * next to sda2 as well?

```

Device               Boot    Start          End            Blocks                ID           System
/dev/sda1                      1                6                48163+            DE          Dell Utility
/dev/sda2           *         7                8586          68915039+      7            HPFS/NTFS
/dev/sda3                   8587          14341        46227037+      83          Linux
/dev/sda4                     14342         14595        2024190          5            Extended
/dev/sda5                      14342        14593        2024158          82          Linux Swap/Solaris

```

---

