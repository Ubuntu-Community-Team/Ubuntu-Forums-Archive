---
title: "Grub Issues"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by meatwad64 on 2007-09-15
I installed ubuntu and not thinking it installed grub on my pata drive which isn't a big deal but i want to take that disk out of this machine and install grub on the disk that actually has the OS. I don't need to dual boot at all. I tried doing grub-install and doing setup (hd1) from inside the grub cmd line but after I reboot it sees the regular options but it gets stuck booting up. Anyone have any idea why this shouldn't work? If i try to boot off the first disk that had grub installed on it the system still boots but the disk that i installed grub on after the install can't boot into ubuntu correctly for some reason. The last thing that shows up is something about modprobe loop with binfmt.

Any ideas?

---

### Post by confused57 on 2007-09-15
> **meatwad64 said:**
> I installed ubuntu and not thinking it installed grub on my pata drive which isn't a big deal but i want to take that disk out of this machine and install grub on the disk that actually has the OS. I don't need to dual boot at all. I tried doing grub-install and doing setup (hd1) from inside the grub cmd line but after I reboot it sees the regular options but it gets stuck booting up. Anyone have any idea why this shouldn't work? If i try to boot off the first disk that had grub installed on it the system still boots but the disk that i installed grub on after the install can't boot into ubuntu correctly for some reason. The last thing that shows up is something about modprobe loop with binfmt.

Any ideas?

Try booting to the drive with Ubuntu, highlight your first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then press "b" to boot...this change is temporary, but is easily made permanent in your /boot/grub/menu.lst.

---

