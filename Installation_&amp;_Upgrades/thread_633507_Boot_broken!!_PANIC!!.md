---
title: "Boot broken!! PANIC!!"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by shakaran on 2007-12-06
I have upgrades today in gutsy and when i restart my computer the boot is broken!!

Messages on screen:

```
Begin: Running /scripts/inti-bottom ...
Done.
Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(inittramfs)
```

I need my computer for work tomorrow early.

Please i need help.

Thanks you.

---

### Post by jdt141 on 2007-12-06
You can get dropped into BusyBox for a lot of reasons (usually very bad). You'll need to post some information for folks to help you. What was your setup before (Fiesty? Edgy?) , what was it that you tried to do (upgrade how) and any other information you might find useful. Change your GRUB boot to remove the "quiet" and "nosplash" parameters, and you'll probably find the error message, which will be greatly helpful for a proper diagnosis.

---

### Post by milesinnz on 2007-12-09
The same thing has just happened to me!!!!
Booting from another disk, sbin/init is indeed no longer showing on the corrupted disk.
So the disk must be corrupt - funny thing, system hung during previous shutdown.

---

### Post by milesinnz on 2007-12-09
fsck passed ok; and now that I recall, i had just installed some updates, so i am guessing something has got messed up as a result.
copied another sbin/init, and the boot process goes somewhat further but fails
init - rc-default main process (4523) terminated with status 127????

---

