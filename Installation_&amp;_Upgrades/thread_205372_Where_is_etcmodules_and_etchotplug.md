---
title: "Where is /etc/modules and /etc/hotplug ?"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by scrut on 2006-06-28
While attempting to use Ubuntu 6.06 with AVM Fritz! Card to connect to the internet, I found several manuals referring to some Ubuntu 5.x utilizing /etc/modules and /etc/hotplug/blacklist for configuration.

However in Dapper I can't find those files / dirs. So I assume I can't apply those 5.x manuals to 6.x?

But how do I make it work then?

thanks

scrut

---

### Post by mlind on 2006-06-28
/etc/modules is there, have to be.
try
```

cat /etc/modules

```

hotplug has been deprecated in favour of udev, so it's not installed by default
and you won't need it either. modprobe contains hotplug's blacklisting
feature now. 

To find the blacklists, look at /etc/modprobe.d/ folder. Files that contain name 'blacklist'
prevent their contents (modules) from loading into kernel.

---

