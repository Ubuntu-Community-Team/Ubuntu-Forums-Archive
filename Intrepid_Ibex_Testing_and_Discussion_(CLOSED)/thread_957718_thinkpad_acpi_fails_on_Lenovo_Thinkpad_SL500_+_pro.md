---
title: "thinkpad_acpi fails on Lenovo Thinkpad SL500 + problems possible resulting fromt this"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by David M. on 2008-10-24
Hi! 

The thinkpad_acpi module fails to load with following error: 

[on console]
FATAL: Error inserting thinkpad_acpi (/lib/modules/2.6.27-7-generic/kernel/drivers/misc/thinkpad_acpi.ko): No such device
[dmesg]
[ 3704.404953] thinkpad_acpi: Not yet supported ThinkPad detected!

Well - ok this already gives the answer :) BUT: 
i have some problems where i am not always sure weather or not these problems have something to do with the above issue   

1. My volume keys do not work (!!this has to do with thinkpad_acpi not loading!!) 

Are their any workarounds known to this?? 

2. is a quite annoying "bug", my display brightness is MUCH too low! I set the brightness to 100% but its not near as bright as in Windows or at gdm-login-screen (!sic) - yes the display gets "darker" when gdm "starts" the gnome session on successful login. The brightness-applet bar is full (Fn + Pos1/End) and in the Energy Options brightness is also set to 100%! 

Some other considered important infos for my environment: 
- Ubuntu 8.10 RC AMD64 - fresh install on a Lenovo Thinkpad SL500
- $ uname -a
Linux cr 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux
- I have the proprietary nVidia drivers 177 installed

Can anybody tell me how i could fix this? For (1) i think i have to wait for a new thinkpad_acpi package. But the display brightness bug is realy annoying and should be resolved somehow (could this be possible with this Nvidia tool?) 


David

---

