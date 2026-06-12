---
title: "view directory in recovery mode"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by the_french_canadian on 2006-10-29
Hello All

I want to view the /etc/X11 directory in Recovery Mode

I also want to rename a file in Recovery Mode, how would i do this?

It's just that i reconfigured my /etc/X11/xorg.conf file, but before overwriting, it created a backup saved in the same directory. I want to replace the reconfigured file with the backup!

Can anyone help!!!!

---

### Post by _lynX on 2006-10-29
To view the directory, you can simply use *dir /etc/X11*.

To rename a file, use *cp oldfile newfile*, or in your case, something like *cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf*.

---

