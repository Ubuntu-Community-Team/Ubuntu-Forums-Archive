---
title: "Keyboard doesnt respond"
date: 2004-10-14
forum: Installation &amp; Upgrades
---

### Post by -baHam- on 2004-10-14
after booting the cd, the keyboard doesnt work,, Does not respond to any command.. it is like it doesnt work, but it works.. what to do ?

---

### Post by -baHam- on 2004-10-15
Got it, got it :)

---

### Post by bdoetsch on 2004-10-15
what did ya do to fix it? got the same problem...

---

### Post by -baHam- on 2004-10-15
just boot like that:

linux pci=noacpi acpi=off nopic nolapic


 8)

---

### Post by bdoetsch on 2004-10-15
Got it fixed myself. 
added the bootparam "noapic" and deactivated legacy usb in my bios. but maybe it was just the amd64 iso (now I'm using i386).

Thx alot for your effort,
Bastian

---

### Post by aod on 2005-08-31
I had the same problem using 5.04 on my amd64 / nf4 system. Tried disabling acpi in bios and on kernel, but no go. I use ps2 keyboard and mouse, so I tried disabling usb keyboard and usb mouse suport on bios and it worked!

---

