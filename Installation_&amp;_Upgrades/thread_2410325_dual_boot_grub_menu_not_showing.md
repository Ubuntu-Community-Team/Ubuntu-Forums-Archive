---
title: "dual boot grub menu not showing"
date: 2019-01-14
forum: Installation &amp; Upgrades
---

### Post by elias.g on 2019-01-14
[http://paste.ubuntu.com/p/7BdcNhDdfw/](http://paste.ubuntu.com/p/7BdcNhDdfw/)
after a lot of trial, ubuntu reapir gave me
 the above url to fix...plz help if u encounter the same

---

### Post by yancek on 2019-01-14
You did not install Grub to the MBR of the drive so you have windows code there.  You can either configure windows with bcdedit to create a menuentry for Ubuntu to boot it explained at the link below:

[https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)

OR, you can accept the recommendation from Boot Repair and install Grub from the Ubuntu on sda5 to the MBR as the grub.cfg file already has an entry for windows.

---

