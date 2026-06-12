---
title: "Cannot allocate resource region.."
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by djeikyb on 2007-12-20
I'm trying to install Ubuntu 7.10 desktop on an HP ML350. I get the following errors before I get a chance to install:

```
[150.100623] PCI: Cannot allocate resource region 4 of device 0000:00:1d.0
[150.100679] PCI: Cannot allocate resource region 4 of device 0000:00:1d.1
[150.100730] PCI: Cannot allocate resource region 0 of device 0000:00:1f.2
[150.100776] PCI: Cannot allocate resource region 1 of device 0000:00:1f.2
[150.100822] PCI: Cannot allocate resource region 2 of device 0000:00:1f.2
[150.100867] PCI: Cannot allocate resource region 3 of device 0000:00:1f.2
[150.100913] PCI: Cannot allocate resource region 4 of device 0000:00:1f.2
```

And then it dumps me into a busybox shell (initramfs).

Anyone know what's wrong?

---

### Post by Partyboi2 on 2007-12-20
You could try this,
Boot the live cd. When you get to the main menu screen (Where the cd options are)
Hit F6 to edit boot options and at the end of the line add "pci=routeirq" (Without quotes) then press enter.

---

### Post by abupapu on 2007-12-25
Did the 'pci=routeirq' command help?

---

### Post by djeikyb on 2007-12-26
Nope.

---

### Post by Partyboi2 on 2007-12-26
since pci=routeirq did not work try these two
```
noapic nolapic
```
If that doesn't work you could try the alternate cd 
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

