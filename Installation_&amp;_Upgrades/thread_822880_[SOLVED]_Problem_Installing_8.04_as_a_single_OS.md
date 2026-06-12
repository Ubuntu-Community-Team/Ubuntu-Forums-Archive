---
title: "[SOLVED] Problem Installing 8.04 as a single OS"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by Cha0tik on 2008-06-08
Currently, I have Win Vista and I have been running Ubuntu 8.04 for a few months now using Wubi.

I am not ready to kiss goodbye Windows all together so I downloaded the ISO image, burned it and now I am booting on the CD just fine.

When booting, I select English as my language, than I select Install Ubuntu.

Right after I select Install, there's a quick popup window showing "Loading Linux Kernel". The progess indicator goes up to 100% and then all I see is a black screen with a blinking cursor at the very top.

It doesn't seem to matter how long I leave that screen there, nothing happens.

Any idea what could be wrong ?

Thanks

Cha0tik

---

### Post by Cha0tik on 2008-06-08
Actually, here is more info on the problem.
I removed the --quiet in the install parameters so I now know why it's stalling.

The last line before stopping any work says:

"..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1"

does this mean anything to anybody ?

Thanks again

Cha0tik

---

### Post by Pumalite on 2008-06-08
You could try these:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=791 vga=788
Alone or in different combinations until you hit the right one.

---

### Post by Cha0tik on 2008-06-08
acpi=off took me further...
I am now navigating through the installation screens.

Thanks !

---

### Post by Pumalite on 2008-06-08
You are welcome. Good luck.

---

