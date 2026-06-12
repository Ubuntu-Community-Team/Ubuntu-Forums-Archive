---
title: "USB install hangs on black screen Acer 5338"
date: 2024-08-31
forum: Installation &amp; Upgrades
---

### Post by mistermax on 2024-08-31
Installing on an old Acer 5338 I set the USB to boot first. There is NO secure boot option, so I'm not disabling / enabling anything. The USB gets to the grub/bootloader choice screen, but when I select either install option it drops to a flashing cursor which eventually stops flashing.

This is (currently) from a linuxshop.co.uk bought USB. I've previously tried it from my own written USB.

I've currently got FreeBSD installed on the laptop. (Prior to that, it had Mint).

Bit stuck on what to try next.

---

### Post by Rubi1200 on 2024-08-31
What is the RAM and graphics for the laptop?

Boot with safe graphics mode from the USB also does nothing?

Which version of Ubuntu is on the stick?

---

### Post by mistermax on 2024-08-31
24 LTS. Happens in both modes. I topped the RAM out on that laptop at 4GB, I think. Default graphics which is Intel on the board but Nvidia also.

An Acer 5338 basically

---

### Post by Rubi1200 on 2024-08-31
I don't think 4GB is enough nowadays for recent Ubuntu versions. Try something lighter like Xubuntu or Lubuntu.

However, you can also try this:

When you see the line Try or Install Ubuntu press e to edit.

Find the line with quiet splash and try adding one or all of these parameters: acpi=off nomodeset noapic, Probably best to try each one separately to see if it works.

Then Ctrl+X to boot with the new line.

Probably a longshot but worth trying.

---

