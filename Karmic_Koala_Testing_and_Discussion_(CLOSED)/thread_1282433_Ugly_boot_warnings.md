---
title: "Ugly boot warnings"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2009-10-04
After the text that says 'GRUB booting' or whatever, I get some warnings:


```
0.1928811 pci 0000:05:00.0: BAR 0: no parent found for of device [0xb020000   ...
17.162907] mmc0: Unknown controller version (16). You may experience problems
```

Eventually, and briefly, I get some the graphical progress indicator before a login screen. It looks pretty bad and I think it might be slowing the boot time down.

If I file a bug under the 'linux' package for ubuntu in launchpad, will I have enough information if I follow up with this in the terminal?

```
$ apport-collect -p linux <bug#>
```

---

### Post by VMC on 2009-10-04
Maybe ```
lspci -v
``` will help to diagnose the problem.

---

### Post by dino99 on 2009-10-04
> **jarlath said:**
> After the text that says 'GRUB booting' or whatever, I get some warnings:


```
0.1928811 pci 0000:05:00.0: BAR 0: no parent found for of device [0xb020000   ...
17.162907] mmc0: Unknown controller version (16). You may experience problems
```

Eventually, and briefly, I get some the graphical progress indicator before a login screen. It looks pretty bad and I think it might be slowing the boot time down.

If I file a bug under the 'linux' package for ubuntu in launchpad, will I have enough information if I follow up with this in the terminal?

```
$ apport-collect -p linux <bug#>
```

restart hal & udev

---

### Post by FuturePilot on 2009-10-04
> **jarlath said:**
> 

If I file a bug under the 'linux' package for ubuntu in launchpad, will I have enough information if I follow up with this in the terminal?

```
$ apport-collect -p linux <bug#>
```

Just use ```
ubuntu-bug <package>
```
No need to manually report it and then follow up.

---

### Post by QwUo173Hy on 2009-10-04
Thanks. I've submitted it using FuturePilots advice.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442346](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442346)

---

### Post by hblaw on 2009-10-04
I think everyone is getting some ugly text between grub and xsplash. Hope the developers can fix this first impression thing.

---

### Post by ranch hand on 2009-10-05
Yup, some text but getting to be less and less.  Last couple of updates cut it by about 2/3 on my box.

I like the title of this thread.  If the bugger wasn't fairly easy to change, I would say that we need an "ugly" warning for xsplash and GDM.

It has encouraged me to learn to fix it.

I am getting pretty excited about this 9.10 bugger.

---

