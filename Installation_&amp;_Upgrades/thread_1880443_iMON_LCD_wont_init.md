---
title: "iMON LCD wont init"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by Sunborn on 2011-11-13
Fresh install of the LTS Ubuntu. I have an iMON LCD but can't get the LCDd to work. 

I have been trying to follow the online guides but they are mostly outdated with improvements to the software.

The output of my LCDd -f -r 5 -s 0 is:

```
Listening for queries on 127.0.0.1:13666
screenlist_init()
driver_load(name="imonlcd", filename="/usr/lib/lcdproc/imonlcd.so")
imonlcd: using Device /dev/lcd0
imonlcd: ERROR opening /dev/lcd0 (Permission denied).
imonlcd: Did you load the iMON kernel module?
Driver [imonlcd] init failed, return code -1
Module /usr/lib/lcdproc/imonlcd.so could not be loaded
Could not load driver imonlcd
There is no output driver
Critical error while initializing, abort.

```

I am too much of a newb to know what to do now.

This is a make or break issue, if I can't resolve this I will have to pay the M$ tax.

Thanks for any help.](*,)

---

### Post by Sunborn on 2011-11-13
turns out that all I needed to do was reboot

---

