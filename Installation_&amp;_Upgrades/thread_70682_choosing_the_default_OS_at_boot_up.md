---
title: "choosing the default OS at boot up?"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by 68Firebird on 2005-09-30
How do I choose the default os when I start my pc?
I have a dual boot Windows xp/Ubuntu system. Since installing Ubuntu, the default os is Linux and I have to scroll down to the bottom within 10 seconds to boot into Windows xp. I would like the default to be Windows XP. Is there away to change this?

---

### Post by adwait on 2005-09-30
Open up the file /boot/grub/menu.lst using the command
```

sudo gedit /boot/grub/menu.lst

```

There will be one entry for each option shown in the boot up menu, count the serial number of your windows entry (start counting with 0 not 1, ie: 0 1 2 3.....)

Now find the line
```

default 0

```
Change 0 to the serial number of your Windows installation.

---

### Post by 68Firebird on 2005-09-30
Thanks, it worked perfectly.;)

---

