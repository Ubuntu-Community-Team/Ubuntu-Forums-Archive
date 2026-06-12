---
title: "How to install Ubuntu 7.10 on a Dell Inspiron 1100 notebook"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by RedDawg on 2007-10-29
Many people have encountered problems installing Ubuntu 7.10 (Gutsy) on laptops with an Intel 82845G/GL integrated display adapter, such as the Dell Inspiron 1100. The installation is unable to detect the Intel 845GL display adapter and defaults to the "VESA" driver. Manually selecting the correct display adapter or continuing the installation using the "VESA" driver causes Ubuntu's setup to lockup.
 
**How to install Ubuntu 7.10 (Gutsy) on a Dell Inspiron 1100:**

**Change Video Memory in BIOS setup:**

[LIST=1]
[*]Make sure your Dell Inspiron 1100 notebook has been upgraded to the A32 BIOS.
[*]When you start your computer, hit F2 to enter Setup.
[*]Press Alt-P (Turn the page) until you get to the page with the video memory.
[*]Change the video memory from 1MB to 8MB.
[*]Reboot
[/LIST]
**Run Ubuntu 7.10 Setup from CD:**

[LIST=2]
[*]Run Ubuntu Setup in "Safe Graphic" mode.
[*]When Ubuntu Live finishes loading, open a "Terminal" window.
[*]Type "sudo su" to become root in the terminal window.
[*]Changed directory into /etc/X11 by typing:```
# cd /etc/X11
```
[*]Edit "xorg.conf" using "vi" editor and locate the Section called "Device".
[*]Change the Driver from "VESA" to "i810":```
From:

Section "Device"
Identifier "Generic Video Card"
Driver "VESA"
BusID "PCI:0:2:0"
 
To:
 
Section "Device"
Identifier "Generic Video Card"
Driver "i810"
BusID "PCI:0:2:0"
```
[/LIST]
**Perform Live Install Now:**

[LIST=1]
[*]Double click on the "Install" icon on the Ubuntu Live Desktop.
[*]Follow the normal install procedure. When you are done, you will have a fully functional Ubuntu 7.10 Linux OS on your Dell Inspiron 1100 notebook.
[/LIST]:KS

---

