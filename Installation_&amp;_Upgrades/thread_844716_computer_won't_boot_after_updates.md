---
title: "computer won't boot after updates"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by raceman62race on 2008-06-29
Insstalled updates and then it said I needed to reboot. Now I get an error
MP-BIOS bug: 8254 timer not connected to IO-APIC
Kernel panic not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the noapic option.

What do I need to do?????

---

### Post by iaculallad on 2008-06-29
Edit your /boot/grub/menu.lst file:

```
gksu /boot/grub/menu.lst
```


and append 'noapic' to the line the says "#defoptions=", then

Update grub:

```
sudo update grub
```

EDIT: Be sure to uncomment "#defoptions=" by removing the # sign afterwards.

---

### Post by raceman62race on 2008-06-29
How do I do that? computer locks up during boot up after it gives me the error?

---

### Post by iaculallad on 2008-06-29
> **raceman62race said:**
> How do I do that? computer locks up during boot up after it gives me the error?

Press F6 key when you see GRUB loading at boot time. A window will popup with a bunch of junk in it. Add 'noapic' (w/o single quote) after that and press Enter key. The system should boot and redo the process above when you are on GUI to fix it permanently.

---

