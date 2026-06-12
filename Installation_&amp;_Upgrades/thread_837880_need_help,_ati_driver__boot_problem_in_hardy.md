---
title: "need help, ati driver / boot problem in hardy"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by lilbluegremlin on 2008-06-22
i am running hardy heron and trying to install drivers for my ati card so that it will run direct rendering.
so far it has not let me install any ati drivers, i have tried the ati driver from the hardware driver which loaded fine but when i rebooted it went to the black screen again after after loading but before the login screen.

i have also tried the ati driver installer from ati's site for linux computers.
i used
Code:

 $ sudo sh ati-driver-installer-8-6-x86.x86_64.run

to run the file which installed fine. it did put out after i was done that the DKMS part of installation failed. i'm not sure what that means.
when i restarted after doing this it again went to the black screen after loading but before log in. ill keep trying different methods of installing the ati drivers but any help would be amazingly awesome!

after all that i then tried  the installation guide from
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way")
and also enabled the ati driver from the hardware driver.
this combination then did allow me to reboot and load Ubuntu with the ati driver from the hard wear driver enabled. however its not the actual ati driver its the mesa driver.

---

