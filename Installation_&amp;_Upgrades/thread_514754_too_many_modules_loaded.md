---
title: "too many modules loaded"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by cyril.scetbon on 2007-08-01
Hi people,

Is there a way to disable modules that I don't want to be loaded. For example, parport,lp or others. The only way I found is to remove them from /lib/modules, is there a cleaner way ?

thanks.

---

### Post by anubhavrocks on 2007-08-01
check out these file
/etc/modprobe.d/blacklist
/etc/modules

You donot need to remove files from /lib/modules

---

### Post by cyril.scetbon on 2007-08-01
I think they are loaded by udev

---

### Post by anubhavrocks on 2007-08-01
Thats right.
Further you can add modules in the  ```
/etc/modprobe.d/blacklist
``` file to prevent them  from loading .

If you open that file and take a look you can easily understand what it does.

---

