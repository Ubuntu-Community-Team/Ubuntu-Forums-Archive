---
title: "RT2500pci borkes suspend/resume"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zaomaster on 2009-04-17
So, on my fully updated Jaunty install, if the rt2500pci module is loaded when I suspend the computer I cannot get it wake up. If I unload the module prior to suspending, then it works properly. I've written a simple script to do this ```
#!/bin/sh

killall wicd-client

/etc/init.d/wicd stop

/etc/init.d/networking stop

modprobe -r rt2500pci
```
and
```
#!/bin/sh

modprobe rt2500pci

iwconfig wlan0 rate 54M

/etc/init.d/networking start

/etc/init.d/wicd start

wicd-client &
```

I know it's a complete hack, because I'm just not that smart when it comes to these things. Is there a way to fix this problem/proper way to unload the module at suspend?

---

