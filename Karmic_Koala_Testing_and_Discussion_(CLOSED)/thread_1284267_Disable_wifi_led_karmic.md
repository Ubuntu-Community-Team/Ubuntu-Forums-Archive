---
title: "Disable wifi led karmic"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nsac on 2009-10-06
I've figured out how to turn off the leds with this script. Seems to be working. But I can't figure out how to add the script to my startup. Adding it to init.d & running update-rc.d didn't work, neither did adding the script to my startup applications.

```
#!/bin/bash
echo none > /sys/class/leds/iwl-phy0::RX/trigger
echo none > /sys/class/leds/iwl-phy0::TX/trigger
echo none > /sys/class/leds/iwl-phy0::radio/trigger
echo none > /sys/class/leds/iwl-phy0::assoc/trigger
```

Any ideas? I can't stand that blinking led & I don't want to recompile the kernel just for that.

---

