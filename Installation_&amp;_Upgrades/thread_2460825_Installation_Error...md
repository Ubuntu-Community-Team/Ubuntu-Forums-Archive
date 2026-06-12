---
title: "Installation Error.."
date: 2021-04-19
forum: Installation &amp; Upgrades
---

### Post by ananthan-y on 2021-04-19
I try to install Ubuntu in my desktop. Earlier I installed Ubuntu  in dual boot (windows and Ubuntu) no problem at all. 
Later I try to install Ubuntu as single OS, so during the installation I erase the window and try to install Ubuntu, then I am getting the following error message.
[COLOR=#000000][FONT=Helvetica]pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]pcieport 0000:00:1c.6:    [ 0] Receiver Error

Any idea how to resolve this ?[/FONT][/COLOR]

---

### Post by CelticWarrior on 2021-04-19
Welcome.

Does it prevent booting? If not you can ignore it.

---

### Post by ananthan-y on 2021-04-20
Yes its prevent from booting. After sometime stuck un sane place.

---

### Post by ActionParsnip on 2021-04-21
If you run:
```

dmesg -T > /tmp/boot.txt; gedit /tmp/boot.txt

```
You can look for large gaps in time on the right hand side (These are the kernel messages as the system boots) which will help diagnose the issue

---

### Post by ananthan-y on 2021-04-22
But my case is different . Even system is not boot . stuck in mid of installation.

---

