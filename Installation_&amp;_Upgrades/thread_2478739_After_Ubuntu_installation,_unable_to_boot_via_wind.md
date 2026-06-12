---
title: "After Ubuntu installation, unable to boot via windows"
date: 2022-09-04
forum: Installation &amp; Upgrades
---

### Post by kamalrajgr on 2022-09-04
hi Team,
After installing Ubuntu in windows PC with dual boot option, i still could not see the option to boot via windows.  It is by default going in Ubutu.  Attached is the log from boot repair for advise.
[https://paste.ubuntu.com/p/Tr7jXWm5WD/](https://paste.ubuntu.com/p/Tr7jXWm5WD/)
Thanks,
Kamal Raj

---

### Post by tea for one on 2022-09-04
When you power on the PC, do you not see the Grub menu?

---

### Post by yancek on 2022-09-04
If you don't see a menu, read the link below which is the Grub Manual, particularly the GRUB_TIMEOUT_STYLE section.

[https://www.gnu.org/software/grub/manual/grub/html_node/Simple-configuration.html](https://www.gnu.org/software/grub/manual/grub/html_node/Simple-configuration.html)

Which version of windows do you have?  If it is 8, 10 or 11, it should be an EFI install and you should have an option in the BIOS firmware to select windows.

---

