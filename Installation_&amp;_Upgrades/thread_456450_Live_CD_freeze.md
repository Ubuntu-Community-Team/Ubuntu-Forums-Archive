---
title: "Live CD freeze"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by fatnic388 on 2007-05-27
Hi. Appologies if this has been covered before, but my searching hasn't turned up anything that works so far.

I'm pretty new to Linux and have just downloaded 7.04 and burnt the image to a disc. All seems fine when booting from the CD (apart form a message saying 'Unknown keyword in config file')

However, I get the following displayed (which I assume are normal)

```
loading /casper/vmlinuz....
loading /casper/initrd.gz.....
```

Then the GUI disapears and then the display freezes on a white cursor. Thats it. I have tried adding 'noapic' and 'nolapic' and also the safe graphics mode. not sure what else to try!!!

I'm running it on a P4 2.8. 1GB RAM. NVIDIA GeFroce 6200 LE graphics card. 

Help please!!!!

---

### Post by fatnic388 on 2007-05-27
OK. Got a bit more info now. Removed 'quiet' from the command line and now the last line to be dislpayed is...
```
Using HPET for base-timer
```
Hope this helps!

---

### Post by fatnic388 on 2007-05-27
Sorted now. Needed to add 'acpi=off'.

---

