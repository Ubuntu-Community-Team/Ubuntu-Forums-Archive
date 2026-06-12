---
title: "Alternate CD LVM install"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by brandon30x on 2007-04-20
I had no trouble installing edgy on my laptop dual booted with windows xp. Now I wanted to try feisty with LVM. So I booted and installed with the alternate install CD. At the end of the install it installs LILO (no option for GRUB??). On reboot the system says loading linux, and it hangs there for
almost 30 seconds. There is no bootsplash or option to boot into windows XP.

Does the alternate install CD not have the option for GRUB/bootsplash/dual booting or should I just give up on LVM?

---

### Post by ilautar on 2007-04-25
You have to use a non-LVM partition for /boot to get grub. Just set up a small ext2 (ext3) one dedicated to /boot.

---

### Post by brandon30x on 2007-05-04
Thank you for your answer. I already installed using the normal install cd, but hopefully anyone else who wants LVM and grub will now know.

-Brandon

---

### Post by pmocek on 2007-05-08
> **ilautar said:**
> You have to use a non-LVM partition for /boot to get grub.
 
Can someone explain why this is the case?  [GRUB has supported LVM since version 1.95]("http://grub.enbug.org/LVMandRAID").

---

