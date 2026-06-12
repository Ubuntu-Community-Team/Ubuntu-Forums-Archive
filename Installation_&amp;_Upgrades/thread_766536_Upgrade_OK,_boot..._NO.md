---
title: "Upgrade OK, boot... NO"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Blastomorpha on 2008-04-25
It took about 4 hours to fetch packages and install (via upgrade manager... yes that thing), but installation ended succesfully... I thought, because now the poor old T40 hangs loading Hardware Abstraction Layer modules, taking 2 minutes to get there!
And now what I'm supposed to do :confused:

---

### Post by Blastomorpha on 2008-04-25
Trying to shoot down manually boot process ended and took me to the login command line.
So I logged and tried startx command... no sound, no wifi, user switcher failed... nothing!

---

### Post by Blastomorpha on 2008-04-25
I think it's a kernel problem, because this time I didn't select the upper one in the grub (the one the upgrade installed), and I'm sure that I'm using 8.04 by ```
cat /etc/lsb-release
```

---

### Post by Puru on 2008-05-03
Got the same HAL issue here.

Well, if unplugging any not necessary device doesn't help, it's probably an acpi problem.

Here what I did:

boot without acpi support, by adding

```
acpi=off
```

at the end of the kernel line in grub's menu. You don't need to manually edit menu.lst file, as you can select the kernel and press "e" to edit a line, than "b" to boot.

Without acpi hardy started fine (but without removable disk support and auto-off). Then I used apt-get to fix dependencies (the hal hang prevented some installations). Everything fine at next boot.

Hope this helps!

---

