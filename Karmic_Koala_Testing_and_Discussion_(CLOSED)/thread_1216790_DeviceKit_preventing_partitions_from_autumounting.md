---
title: "DeviceKit preventing partitions from autumounting"
date: 2009-07-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pt123 on 2009-07-18
In HAL initially it was problem, as not many knew how do it.  

Until someone found out:
[http://ubuntuforums.org/showpost.php?p=2605508&postcount=34](http://ubuntuforums.org/showpost.php?p=2605508&postcount=34)

involves creating this file
/usr/share/hal/fdi/preprobe/95userpolicy/10ignore-disks.fdi

and then adding this
```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
<match key="block.device" string="/dev/sda1">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
</deviceinfo>

```
Rather strange but it worked (although I haven't been able to get it to work using UUIDs).

I was wondering if this is possible in DeviceKit ( I assuming KK will use that than HAL). 

Note ability to "hide" unwanted partitions is very useful, when you testing & using different distributions. It helps declutter the places & computer menu.

---

