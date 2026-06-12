---
title: "Ubuntu upgrade from 12.04 to 14.04 boots to GRUB menu"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by rudy1094 on 2014-09-21
I finally clicked the Ok button to allow Ubuntu to upgrade from 12.04 to 14.04. When it rebooted, it sent me to a GNU GRUB version 2.02 menu. I'm guessing the upgrade didn't go perfectly and something is amiss. How do I fix it? Thanks.



[ATTACH=CONFIG]256581[/ATTACH]

---

### Post by yancek on 2014-09-21
When you see the menu you posted, what happens when you hit the Enter key or let it timeout?  Does it not boot?

---

### Post by rudy1094 on 2014-09-21
There's no timeout on the menu. If I hit enter the screen goes black with a cursor in the upper right corner blinking for a little bit and then the computer reboots and goes back to the GRUB menu.

---

### Post by Bashing-om on 2014-09-21
rudy1094; Humm;

Grub can not locate it's config files, or they are corrupted ?
Mind you I do not know all there is to know about grub, but, I am willing to work with you to find a resolution.
Will be easier to work from a liveDVD, but we can see what grub knows presently.
Boot to the grub boot menu, with that top entry high-lighted, press the 'c' key for a command line interface.
What returns from:
```

search -f /vmlinuz
search -f /sbin/init
search --set=root --file /boot/grub/grub.cfg

```
Once we know where the 'root' file system is installed to, and where the config files are installed to, we can try and direct grub to boot the system from grub, and once booted try and repair grub to boot automagically.

[INDENT][INDENT]hey, It could happen
[/INDENT][/INDENT]

---

