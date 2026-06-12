---
title: "&quot;Failed to allocate video memory&quot; = Low graphics mode"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by blakamin on 2010-03-11
Anyboy else have this problem? 
Only since yesterdays update.
Running nvidia 7000m in acer laptop.
nvidia-current

---

### Post by blakamin on 2010-03-12
Added "nopat" to the grub.cfg and all my problems went away.  :D



[SIZE="1"]well, not all of them... I *still* have to go to work and I'm *still* not a millionaire.[/SIZE]

---

### Post by dino99 on 2010-03-12
> **blakamin said:**
> Added "nopat" to the grub.cfg and all my problems went away.  :D



[SIZE="1"]well, not all of them... I *still* have to go to work and I'm *still* not a millionaire.[/SIZE]

it's nice you have found the solution, but where have you added "nopat" into grub.cfg ?

---

### Post by psyke83 on 2010-03-12
> **dino99 said:**
> it's nice you have found the solution, but where have you added "nopat" into grub.cfg ?

Don't edit grub.cfg directly! Any modifications you make will not survive through GRUB or kernel updates!!!


Edit "/etc/default/grub":
```
$ sudo nano /etc/default/grub
```

Change this line:
```
GRUB_CMDLINE_LINUX=""
```

To this:
```
GRUB_CMDLINE_LINUX="nopat"
```

After saving changes to the file, update your GRUB configuration by typing the following into the command line:
```
$ sudo update-grub
```

This method will ensure that customizations will always survive GRUB/kernel upgrades.

Important: anything you add to the "GRUB_CMDLINE_LINUX_DEFAULT" line will take effect for a normal boot, but not for recovery mode. Anything added to the "GRUB_CMDLINE_LINUX" line will be added to **all** boot options (recovery **and** regular boot).

Therefore, it's always best to add system/quirk-specific boot options (such as nopat, noacpi, nomodeset, etc.) to the "GRUB_CMDLINE_LINUX" line, to ensure that the recovery mode is also usable.

---

### Post by blakamin on 2010-03-13
^^^ exactly what I did.


Unfortunately, this is an old kernel problem that goes back a couple of years and not a very nice way of fixing issues. I'm really hoping for a kernel update to solve it properly.

---

