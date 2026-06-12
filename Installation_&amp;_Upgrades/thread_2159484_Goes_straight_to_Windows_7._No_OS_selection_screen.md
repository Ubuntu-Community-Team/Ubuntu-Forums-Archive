---
title: "Goes straight to Windows 7. No OS selection screen."
date: 2013-07-03
forum: Installation &amp; Upgrades
---

### Post by daggerx on 2013-07-03
I installed Ubuntu 13.04 and I cannot see it. When the machine boots up it goes straight to windows 7. How do I get that menu to show up so I can select which OS I wanna go into? Please advise and thanks. Really wanna start using ubuntu again.

---

### Post by bry012 on 2013-07-03
What did your computer come with, BIOS or UEFI? UEFI tends to be a bit more difficult to dual boot with but is still possible. I do know someone who was able to have a successful dual boot on a UEFI system by reverting UEFI back to Legacy form.

---

### Post by daggerx on 2013-07-03
> **bry012 said:**
> What did your computer come with, BIOS or UEFI? UEFI tends to be a bit more difficult to dual boot with but is still possible. I do know someone who was able to have a successful dual boot on a UEFI system by reverting UEFI back to Legacy form.

Went to the bios. In the boot tab, the "uefi boot" is disabled. The "PXE rom" option is disabled as well.

---

### Post by bry012 on 2013-07-03
Maybe the grub boot loader is broken. You could try a boot-repair from the ubuntu live cd you used to install. Here is a link to the instructions: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by daggerx on 2013-07-03
> **bry012 said:**
> Maybe the grub boot loader is broken. You could try a boot-repair from the ubuntu live cd you used to install. Here is a link to the instructions: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks so much! Did the boot-repair option with the link that you send that that worked. Thank you very much for your help.

---

### Post by bry012 on 2013-07-03
You're welcome! Glad we could find such an easy fix.

---

