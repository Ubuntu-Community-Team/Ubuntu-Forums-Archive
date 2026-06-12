---
title: "Installing Ubuntu 12.04 LTS on Gigabyte A75M-D2H"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by GwibberFooey on 2012-05-22
Progress but still not booting Ubuntu properly....

I am trying to install Ubuntu 12.04 onto a Gigabyte A75M-D2H with an F1 socket and a AMD A8 APU. I am installing from a normal linux iso installation disk, with a normal SATA optical drive.

I went to GRUB and I selected "nomodeset" and then I selected "Install Ubuntu".  The installation seemed to go to completion. I got a GUI and I created a username and password and specified my location and my keyboard layout just like I was prompted to do.  At the end it displayed a message "Installation completed successfully. You must restart your computer to use the new insatllation." So I rebooted and I allowed the machine to (try to) boot from the hard-disk but it was not successful.  

To boot from the harddisk was a failure because a few seconds after it displays "Loading Operating System...", then output to the monitor ceases and the monitor displays its error warning "Entering Sleep Mode" or "No Video Input" or something similar.

I also tried to install from optical drive without selecting "nomodeset". In that case the installation was a failure because a few seconds after it displays "Loading Operating System..." and "Boot from CD/DVD" then output to the monitor ceases and the monitor displays its error warning "Entering Sleep Mode" or "No Video Input" or something similar.

I successfully live-booted Ubuntu when I selected "Try Ubuntu without installing" from the GRUB menu with "nomodeset" active. But when I select "Try Ubuntu without installing" from the GRUB menu with "nomodeset" inactive then within a few seconds output to the monitor ceases and the monitor displays its error warning "Entering Sleep Mode" or "No Video Input" or something similar.

Note: I can't get to GRUB without setting the optical drive as first in the boot sequence.  Booting from the harddisk does not work.  In particular, if I visit the boot menu and explicitly select harddisk as the top boot priority then the monitor displays "Loading Operating System..." but nothing more ever happens.  If I don't explicitly visit the boot menu and just allow it to try to boot from the harddisk (which has the highest boot priority by default) then the monitor displays "Loading Operating System..." for a few seconds and then output to the monitor ceases and the monitor displays its error warning "Entering Sleep Mode" or "No Video Input" or something similar.

---

### Post by sffvba[e0rt on 2012-05-22
After successful installation, and rebooting the first time, hold left shift while booting.  This will give you the grub menu. Again add "nomodeset".  Once you have booted successfully hit the "super" key and type "drivers". Run the utility and install the restricted driver for your system.

I assume it will be ATI/AMD based if it is;

After it installed open a terminal and run:

*sudo aticonfig --initial*

Reboot.


404

---

### Post by GwibberFooey on 2012-05-24
This worked or something very similar. I got my computer to work.  Many thanks.

---

