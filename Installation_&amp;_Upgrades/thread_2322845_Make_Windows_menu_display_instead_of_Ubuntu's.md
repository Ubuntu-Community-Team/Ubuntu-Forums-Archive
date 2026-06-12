---
title: "Make Windows menu display instead of Ubuntu's"
date: 2016-04-30
forum: Installation &amp; Upgrades
---

### Post by Stinger392039 on 2016-04-30
Hi, I am new to Ubuntu and have been off to a rough start.  The installation went smooth, I choose to run Ubuntu 16.04 alongside Windows 7 Pro (x64).  When I rebooted, the Ubuntu boot menu came up with Ubuntu and Windows, but Windows would never load.  I finally fixed that using Boot Repair, only now the Ubuntu boot menu always boots first and I am wondering if I can change that, so the Windows boot menu displays.  Windows is working and I know EasyBCD can do this, but I am wondering if someone can guide me in this.  I appreciate your help and any advice using Ubuntu.

Tim

---

### Post by yancek on 2016-04-30
You would have to first install the windows boot code to the MBR if you are using MBR boot if you want to use the windows bootloader.    If you want the windows bootloader to boot both windows and Linux, you can go through the process explained at the link below.  Not as simple as update-grub.

[https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)

If you want Grub to boot windows by default, you would change the line below in the /etc/default/grub file to reflect the number of the windows menuentry.  The example below shows zero which means the first entry in grub.cfg.

> GRUB_DEFAULT=0

---

### Post by Stinger392039 on 2016-04-30
What I want is instead of the Ubuntu boot menu to display, I want the Windows boot menu to appear.  Currently, Ubuntu's boot menu appears with two listings for Windows, the second one, which actually works.

---

