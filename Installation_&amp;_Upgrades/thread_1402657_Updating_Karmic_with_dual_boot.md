---
title: "Updating Karmic with dual boot"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by decopeland on 2010-02-09
I have Ubuntu 9.10 (kernel 2.6.31-18) on internal drive of Asus 900A netbook and Ubuntu 9.10 (kernel 2.6.31-17) on external drive (using the original Asus ssd drive and RunCore enclosure).  I have tried 3 times to update the internal drive.  Each time after installing the update on the internal drive and rebooting, it will boot into memtest.  And I can no longer boot from the external drive.  There does not seem to be a way to change the boot loader.  The only way I can run Ubuntu is to restore the image (using Clonezilla and backup file from SD card).  By the way, Clonezilla is a nice product.  I am beginning to think I will not be able to update to Ubuntu 10.4 when it is released.  I don't have a reason to update the external drive as it is used just as a backup should the internal drive fail.  Any suggestions?

---

### Post by decopeland on 2010-02-09
I have figured it out.  The external drive has to be connected when updating the internal drive to a new kernel.  Then GRUB for both drives has to be installed to see the new menu.  I was even able to configure the internal drive so that the menu is not displayed during boot if the external drive is not connected.  I hope I can keep this expertise going!

---

