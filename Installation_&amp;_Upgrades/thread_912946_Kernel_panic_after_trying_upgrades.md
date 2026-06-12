---
title: "Kernel panic after trying upgrades"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by Edzio on 2008-09-07
I tried to do some upgrades to my 7.10 install and upon rebooting I got:

14.0273531 ..MP-BIOS bug: 8254 timer not connected to IO-APIC
14.2060251 Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option.

I can't type anything at the prompt, so I'm not sure what to do here.
Can anyone help me?

---

### Post by Edzio on 2008-09-07
I was able to reboot the machine by hard restarting and holding the Escape key and choosing a previous kernel.

---

### Post by Shazaam on 2008-09-07
Try this when you boot....
When your pc boots hit your 'ESC" key. Highlight the first one and hit "e"(without the quotes). This will bring up a list that will look similar to this...
root (hdx,x)
kernel /boot/vmlinuz---------ro quiet splash
intrid
Highlight the kernel line and hit e again. Add this to the end (after splash)...
```
noapic
```
hit enter, then hit "b" (without the quotes). See if it will boot. If it does boot, you can add "noapic" to the same spot on the kernel line in /boot/grub/menu.lst

---

