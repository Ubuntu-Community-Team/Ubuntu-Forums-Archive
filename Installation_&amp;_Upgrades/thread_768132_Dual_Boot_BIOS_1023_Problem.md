---
title: "Dual Boot: BIOS 1023 Problem???"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by karthikb23 on 2008-04-26
Hi,
I have installed Ubuntu 5.04 on my second Hard Drive. My first HD contains windows.

When i make my 2nd HD as boot device, i see GRUB Menu (i.e. stage 2).
On trying to boot Ubuntu, I get an Error 15: File missing problem. The FS shown was FAT.

On trying to boot Windows, I am presented with the GRUB Menu again.
After some help on this Forum, figured out that mapping HD0<->HD1was t solution.

But now, on dual booting from GRUB, GRUB Stage 2 still gives t File Missing error.
On dual booting from Windows, GRUB Stage 2 hangs.

Now i certainly feel, i am stuck with the BIOS 1023 Cylinder problem.

Any solution please?
Or if i re-install Ubuntu, what should i do to ensure boot is within this limit?
Is it a good idea, to create a seperate 1GB Partition for /boot as first partition on HD2, and install root on the other partition?
(Remember i am installing Ubuntu 5.04, and dont have a sophisticated installation menu :( )

Any help is highly appreciated.

---

