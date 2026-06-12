---
title: "can not install. please help!"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by anthony_bu on 2007-05-12
Hi,

I'm new to linux. Try to install ubuntu on my dell xps 400 with out any luck.
I have a Raid 0 with 2 SATA hard drives (hd0 and hd2 in bios, sda and sdb in linux) using Intel on bord controllor. Can not get Raid to work. So I bought another SATA hard drive (shows as hd3 or sdc) and installed ubuntu 7.04 on it. (boot loader installed on hd0) But after reboot, I have GRUB error 21.
I have windows vista on the Raid. I don't mind to wipe it out, but I need to have dual boot.

Please help.

Thanks

---

### Post by bulldog on 2007-05-12
Install GRUB on the same hdd as you install ubuntu.
Choose in your BIOS to boot from this hdd,and you'll have ubuntu up and running.

To run windows,you need to boot from your original boot device.

---

