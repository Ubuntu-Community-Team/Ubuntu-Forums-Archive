---
title: "computer crashes after update to 10.04"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by lenovot400 on 2010-05-31
I have a Lenovo T400 and I upgraded from 9.10 to 10.04. After the upgrade I am not able anymore to start ubuntu.

I get the Grub boot manager. After that I only see the a black screen and sometimes a few pixels. 

I tried already to remove 'quite' and 'splash' in the boot options. And I added 'nomodset' and 'fb=false'.   Nothing works. Help would be greatly appreciated.

---

### Post by lenovot400 on 2010-05-31
I tried some more things as recomanded [here. ]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

I used the Kernel 2.6.31, instead of 2.6.32. When I the additionally removed 'quite'and 'splash' in the boot options. I got to see my mouse coursor after the boot procedure. But that was it.

---

### Post by lenovot400 on 2010-05-31
I can get into ubuntu using the the Kernel 2.6.31 and the recovery mode (recovery mode of 2.6.32 doesn't work). Then I have to start the failsave graphics mode.

I change my xorg.conf, to include

> 
Section "Device"
        Identifier      "Configured Video Device"       
        Driver  "vesa"
        Option  "DRI" "false"
EndSection



I had hoped that this would sovle the problem but it doesn't. Now my starting screen is purple and I do not see my mouse coursor.

---

### Post by lenovot400 on 2010-06-01
I now installed the newest driver for my ATI Radeon Graphics Card.

Changing the xorg.conf to:
> 
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
        Option          "DRI" "false"
EndSection


I still only get somewhere starting the 2.6.31 Kernel and I again have to start in the failsafeX mode.

the logfile says

> 
...
Fatal server error:
no screens found 


---

