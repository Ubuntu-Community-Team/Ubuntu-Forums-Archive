---
title: "Default Boot to Ubuntu with Dual Boot System"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by Rob306 on 2013-02-23
I recently installed Ubuntu (dual boot) on a laptop with Windows 7. Is it possible to have the laptop boot to Ubuntu vice Windows when the system is turned on? Without having to manually select Ubuntu? 

Rob

---

### Post by carl4926 on 2013-02-23
> **Rob306 said:**
> I recently installed Ubuntu (dual boot) on a laptop with Windows 7. Is it possible to have the laptop boot to Ubuntu vice Windows when the system is turned on? Without having to manually select Ubuntu? 

Rob

It should already do that

---

### Post by oldfred on 2013-02-23
It should do that after 10 sec.

The number of seconds it waits is a setting in grub, but some that have changed to 0 then have issues ever getting back into grub menu particularly if boot issues. A setting of -1 sets it to wait until you press a key.

       gksudo gedit /etc/default/grub
    
# this setting is 10 second timeout.
GRUB_TIMEOUT=10

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Or you can use grub customizer.
       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

---

### Post by Old_Grey_Wolf on 2013-02-23
This appears to be a WUBI install. WUBI boots into Windows by default.

---

### Post by Old_Grey_Wolf on 2013-02-23
If it is WUBI, I found this in the [WubiGuide in Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide").

"Ubuntu is not installed as the default boot option, you have to select it in the Windows boot menu." ... "In Windows 7, go to Control Panel > System and Security > System > Advanced system settings (on the left). Then click Settings under Startup and Recovery. If you want, you can change the timeout as well. Be aware that changing the timeout to zero (0) may cause issues booting into Windows. It is preferable that the value be set at 10 or higher."

---

