---
title: "From Maverick To Oneric - Bypass Natty"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by rykel on 2011-07-04
Hi, when Oneric is available in October 2011, how do I upgrade directly from Maverick to Oneric - bypassing Natty?

Natty does not work at all on my hardware, and I hope Oneric will work as well as Maverick.

---

### Post by akand074 on 2011-07-04
Download and burn Oneric onto an empty disc. During the installation there should be a step called "upgrade Ubuntu 10.10" I believe. I know you can't bypass natty if you are installing from the update manager, but I think you can from the burned ISO. I could be wrong.

---

### Post by rykel on 2011-07-05
In my case, I no longer have a CD-ROM drive, and being an old laptop, my BIOS does not allow me to Boot Up from USB either.

---

### Post by mastablasta on 2011-07-06
you can use PLOP boot manager to boot from USB using floppy or stick it on hard disk and then use hard disk too boot form USB. or you can modify grub.

---

### Post by rykel on 2011-07-06
> **mastablasta said:**
> you can use PLOP boot manager to boot from USB using floppy or stick it on hard disk and then use hard disk too boot form USB. or you can modify grub.

PLOP looks exactly just like what I need! However, in the README file, it warns Linux users NOT to install GRUB to the MBR...

[LIST=1]
[*]How do I know if my GRUB is currently in the MBR?
[*]If so, how do I safely and quickly move GRUB out of the MBR?
[/LIST]

---

