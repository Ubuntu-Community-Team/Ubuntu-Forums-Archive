---
title: "Unkown Filesytem rescue grub"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by Lynrax on 2011-03-08
I installed Ubuntu on a partition fron my external HD.

Works great and without problems wehn i boot it from my PC,

but when i try to boot it from my Laptop or an other Computer i get this error message

```
error: unknown filesystem
rescue grub: 
```

how caan i fix this?

---

### Post by Dutch70 on 2011-03-08
> **Lynrax said:**
> I installed Ubuntu on a partition fron my external HD.

Works great and without problems wehn i boot it from my PC,

but when i try to boot it from my Laptop or an other Computer i get this error message

```
error: unknown filesystem
rescue grub: 
```

how caan i fix this?

Welcome to UF Lynrax

 I'm no expert, but it appears that grub is installed to the MBR on your computer, but not your laptop or the other pc's your trying to boot from. You can try to install grub to your external HD with a live cd/usb. I would unplug my internal hdd before I attempted it, just to be on the safe side. 

This may help...
[[COLOR="Blue"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

