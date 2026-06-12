---
title: "ubuntu and windows 7"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by matious89 on 2011-04-17
Hi all, 

I have problem with installing ubuntu together with windows 7. Windows was installed before installing ubuntu 10.10. The issue is that I run ubuntu installator everything is working, installation finished successfully, then is the button to restart the computer after ubuntu installation I clicked restart, and only windows 7 is starting, no booting menu, no grub, no windows loader menu. 

I've tried installing from CD and USB the same results. During instalation I've choose to use entire disk for instalation. 

My computer configuration: 2HDD, one on SATA Primary (Win7) the other one ATA Primary (Disk for Ubuntu), both system x64. 

What i've made wrong?

---

### Post by TheExposedOne on 2011-04-17
you need to edit the boot loader in windows

---

### Post by Quackers on 2011-04-17
Welcome to UF.
Where did you install grub to?
Please boot from the live cd/usb and select "try ubuntu" and then connect to the internet. Then go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

