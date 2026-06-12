---
title: "Ubuntu freezes/errors during install reboot computer now trashed"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by Colquetzlquatl on 2010-08-13
I installed Ubuntu formatting it to my external hard drive. Ubuntu comes up and asks me to reboot I click yes; the screen goes black and I get a huge amount of errors. I waited an hour to make sure this wasn't normal, then I turned it off manually. When I turn it back on my PC no longer recognizes my main hard drive as existing no less the external one. :confused:

---

### Post by lukeiamyourfather on 2010-08-13
Don't use external drives for an operating system. The installer probably put the boot loader (GRUB) on the disk in the machine which sometimes requires some extra configuration if dual booting with another operating system.

---

### Post by Colquetzlquatl on 2010-08-13
Ok then, how do I do this configuration cause according my computer now neither my internal drive, external drive, or CD/DVD drive don't exist and I can't get out of the BIOS.

---

### Post by lukeiamyourfather on 2010-08-13
I think I misunderstood the issue. If the disks don't show up in the BIOS then you've got a hardware issue unrelated to Ubuntu. The boot loader (GRUB) wouldn't cause that issue.

---

