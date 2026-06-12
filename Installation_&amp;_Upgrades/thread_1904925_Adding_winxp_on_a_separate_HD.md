---
title: "Adding winxp on a separate HD"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2012-01-05
Despite all sorts of attempts to access my Sony Ericsson k608i phone via its USB port in Ubuntu it is not being recognised as being connected. I am therefore proposing to install WinXP on a spare HD that is in the current computer. 


Would you agree that the best way to do this is to unplug  all the other cables from the existing HD's? Install WinXP on the one remaining HD, and then reconnect the other HD's. Choose os system via the bios order of boot.

---

### Post by darkod on 2012-01-05
Yeah, you can unplug all the others to make sure windows bootloader goes to the same disk. Windows is very unintelligent about that.
But that doesn't mean you will have to choose in bios each time, it would be waste of time.

After the XP is installed and you connect the other disks, boot ubuntu as normal (first time it's still not aware of XP) and in terminal run:
sudo update-grub

It will detect the XP and make an entry in the grub2 boot menu for it. You can select what you want to boot without touching bios.

---

### Post by Rebelli0us on 2012-01-05
> **Robbyx said:**
> Despite all sorts of attempts to access my Sony Ericsson k608i phone via its USB port in Ubuntu it is not being recognised as being connected. I am therefore proposing to install WinXP on a spare HD that is in the current computer. 


Would you agree that the best way to do this is to unplug  all the other cables from the existing HD's? Install WinXP on the one remaining HD, and then reconnect the other HD's. Choose os system via the bios order of boot.

yes, unfortunately that's the safest way to do it. You **can** install Ubuntu without disconnecting anything but you must make sure to instruct the installer to put Grub on the disk **you** want and leave the windows disk untouched.

Another solution might be to run XP in a virtual machine, you can install Oracle Virtualbox through the Ubu software centre.

---

### Post by oldfred on 2012-01-05
Windows XP uses boot.ini to know which drive & partition it is installed to. If you install to sda1 and sda it will be rdisk(0). But if drive is not the first when you reinstall it you may have issues. Grub does try to map or mapdevice to change what drive Windows thinks it is one, but it is just easier to leave it as sda and let grub see Ubuntu has changed. Grub boots by UUID so changes rarely make a difference & a sudo update grub resolves those differences.

---

