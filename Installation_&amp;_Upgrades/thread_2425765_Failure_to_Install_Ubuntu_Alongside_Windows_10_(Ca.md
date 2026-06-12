---
title: "Failure to Install Ubuntu Alongside Windows 10 (Cannot Install to /target/)"
date: 2019-08-29
forum: Installation &amp; Upgrades
---

### Post by shadshd on 2019-08-29
I posted earlier about issues with ACPI errors, and after fixing them for booting into a USB, I came across this error when installing Ubuntu 18.04 LTS:

The 'grub-efi-amd64-signed' package failed to install into /target/. Without the grub boot loader, the installed system will not boot.


Disk Info:
Intel 660p 512GB: Contains Windows 10 on C:, UEFI Partition, Microsoft Reserved Partition, Empty Partition for Ubuntu, WinRE Tools, Recovery Partition.
Samsung EVO 860 1TB: Contains game library on D:

Edit: I get this information from the error log after a failed installation.

[IMG]https://scontent-dfw5-1.xx.fbcdn.net/v/t1.15752-9/s2048x2048/69630328_371783706824244_9120280396410388480_n.jpg?_nc_cat=101&_nc_oc=AQnYUjtEHoKvs7ZchDZ5ilHWPbVtGSyLG7N0-r_mp6brCFqjbYUWo8gq3mwtjVXyS_jjEOIqlI3dEZYloR-qoY4w&_nc_ht=scontent-dfw5-1.xx&oh=66a3839b3af518b2a0f90971631b0a5a&oe=5E15C9D6[/IMG]

---

### Post by wildmanne39 on 2019-08-29
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by shadshd on 2019-08-29
> **wildmanne39 said:**
> Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Apologies. I was just trying to distinguish between the normal text and the error.

---

### Post by oldfred on 2019-08-30
/target is normally the ESP on your first drive, normally Windows already has an ESP which is what you want to use. If your Windows is not on first drive, sda or first NVMe drive, and you have another drive as sda without an ESP then you may get this error.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) &

---

