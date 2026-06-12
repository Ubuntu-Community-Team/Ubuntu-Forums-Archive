---
title: "Which is better? Install Ubuntu 18LTS on Win10 or install Win10 on Ubuntu18LTS?"
date: 2019-02-03
forum: Installation &amp; Upgrades
---

### Post by mal0n3m on 2019-02-03
I'm trying to do a dual boot on my computer and after reading and going through this forum for instructions, it seems that having dual boot on your system can be complicated and if you do it wrong, you will mess up your GRUB. What is the preferred way of having both OS on your computer?  Ubuntu 18LTS on Win10 or Win10 on Ubuntu18LTS?

---

### Post by Topsiho on 2019-02-03
First install Windows, then install Ubuntu.
Windows doesn't see Ubuntu during install, so if you install Ubuntu first, and then Windows, you can only boot into Windows.

Topsiho

---

### Post by yancek on 2019-02-03
Not sure what you mean by "on" unless you are referring to virtual software.  In that case, it should not matter.  If you are installing both systems without using virutalization, then installing windows first would be simpler.  Your post indicates that you have nothing currently installed on the drive(s), correct?  If you install windows 10 first, I would suggest you read the Ubuntu documentation on dual booting with windows 10 at the link below before you begin the Ubuntu installation.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-02-03
Just be sure to install both in UEFI boot mode, if newer hardware that is UEFI.
Both Windows & Ubuntu install in the boot mode that you boot install media, UEFI or CSM/BIOS/Legacy.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

