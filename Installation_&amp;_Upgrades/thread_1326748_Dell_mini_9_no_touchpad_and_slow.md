---
title: "Dell mini 9 no touchpad and slow"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by mundo on 2009-11-14
Hi,

I have upgrade from Netbook remix 9.04 to Netbook remix 9.10.  All was fine on 9.04 but I am really regretting upgrading now.

I have now touchpad. The only way I can use the mouse is to use a bluetooth mouse.

The system is running like a dog and everything is very unresponsive.

Has anyone else experienced these issues?  How can I get back to a nice fast system with everything working like 9.04?

---

### Post by mundo on 2009-11-15
OK, managed to get this working. Looks like as usual trying to upgrade was a miskake so I used GParted live USB to remove the existing Ubuntu partitions then reinstalled from USB.

The only issue I had then was that wireless would not work but I hooked it up to ethernet and then ran

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

After a reboot all was OK.

---

### Post by mundo on 2009-11-17
The only issue that I have now is a problem with mobile broadband. I have seen that other users are experiencing this issue. The issue is that is says connected and the modem stick light is on but there is no internet. After disconnecting and connecting a few times it eventually works but it's a real pain and is one of those things that makes you wish you hadn't upgraded.

---

### Post by mundo on 2009-11-18
Looks like this issue is solved now. Just a simple connection setting in Firefox, not sure if they changed the default or not in 9.10.  Anyway, just go into Firefox:

Edit>Preferences>Advanced>Network tab>Settings>Change from "Use system proxy settings" to "Auto-detect proxy settings for this network"

---

