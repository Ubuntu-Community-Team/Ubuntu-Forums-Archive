---
title: "Jaunty alpha6 installer and boot loader installation"
date: 2009-03-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lorebett on 2009-03-21
At the end of the installation process (Step 7 of 7) of Jaunty Alpha 6, when clicking on the Advanced button, the boot loader installation option does not leave much of a choice: either you install the boot loader on a device or you don't install it. I don't want to install the boot loader on the MBR since this would overwrite the current boot loader; in previous versions of ubuntu installations you were allowed to specify the full grub device specification, e.g., you could do (hd0,4) meaning to install the bootloader on the first sector of /dev/sda5...

This possibility is crucial if you have many linux distribution installations and you use one single main grub installation on the MBR which then "chainloads" to other grub installations (on the first sectors of specific partitions).

Anyone noticed this?

I also filed a bug report: [https://bugs.launchpad.net/ubuntu/+bug/346298](https://bugs.launchpad.net/ubuntu/+bug/346298)

---

