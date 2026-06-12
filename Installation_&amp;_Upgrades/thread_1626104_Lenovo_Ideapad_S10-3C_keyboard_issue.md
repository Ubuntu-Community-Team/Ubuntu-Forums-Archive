---
title: "Lenovo Ideapad S10-3C keyboard issue"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by jssudheer on 2010-11-19
On trying to install ubuntu netbook version 10.10 on  ideapad S10-3C, (Intel atom N455, 2gb memor,y 160 HDD, windos 7 starter edn.), the keyboard does not respond even for entering user name and password. Tried installing inside windows also. Please help.:p
Dr.Sudhir

---

### Post by thebat on 2010-11-21
hello!

I have same issue

I try find solution in 
[http://forums.lenovo.com/t5/Linux-Discussion/S10-3C-amp-linux-amp-keyboard/m-p/319367#U319367](http://forums.lenovo.com/t5/Linux-Discussion/S10-3C-amp-linux-amp-keyboard/m-p/319367#U319367)

I post the bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/677633](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/677633)

---

### Post by g_s_patra on 2011-05-22
Installed Ubuntu 11.04 in Lenovo IdeaPad S10-3c. (erased Ubuntu 10.10).
 (1) Keyboard totally locked after GRUB. External keyboard is working in full-swing 
 (2) Bluetooth is disabled by the system. (3) Battery charge-indicators static. (4) apps are crashing (especially LibreOffice). (5) A file saved in ODF, when reopened, shows font-problem - asking for UNICODE.

---

### Post by g_s_patra on 2011-05-31
the battery-indicator is showing only 'discharging'. It seems that it fails to charge at all

---

### Post by SatanClaus on 2011-07-10
> **jssudheer said:**
> On trying to install ubuntu netbook version 10.10 on  ideapad S10-3C, (Intel atom N455, 2gb memor,y 160 HDD, windos 7 starter edn.), the keyboard does not respond even for entering user name and password. Tried installing inside windows also. Please help.:p
Dr.Sudhir

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/677633](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/677633)

---

### Post by ambijat on 2012-01-19
This is the one and final solution for keyboard problems in all Linux OS on Lenovo S10-3c.

1.The main problem is the bios, but the bigger problem is that Lenovo driver & bios update site does not give you the full pack. It only gives you the file 3CCN16WW.exe . This file alone does not run and on Windows 7 (recommended) if you run it. IT will give you the error: Unable to load driver.

2. After looking for various sites, I find one Russian link that gives complete .zip package that helps you to run this 3CCN16WW.exe file. The link I am not giving here. But, those interested can request me at [EMAIL="ambijat@gmail.com"]ambijat@gmail.com[/EMAIL]. I shall give you the link.

3. Download the file unzip it and then restart computer to run BIOS and then restart then run ECFLASH. And your bios updates to version 16.

4. I am easily running my win 7 and ubuntu 11.10 side by side with keyboard working fine in Ubuntu. Next thing is Easy Camera, an ideas???

Thanks!
Ready to help all, Lenvov S10-3C becomes altogether different after this. :-)

---

