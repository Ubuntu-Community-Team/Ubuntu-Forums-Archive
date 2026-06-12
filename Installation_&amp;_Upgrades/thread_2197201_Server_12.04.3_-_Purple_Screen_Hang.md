---
title: "Server 12.04.3 - Purple Screen Hang"
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by chrisb009 on 2014-01-02
Installed Ubuntu Server 12.04.3 64 bit - installation went fine. After the system rebooted I applied all updates. Now the system is slower than Winblows 98SE during boot. During boot; it displays the GRUB menu a split second then finally displays the installed GUI. Any idea what disastrous distro update could cause this?

-Chris

---

### Post by Matthew_Penny on 2014-02-19
Similar issue:  Dell GX520 with 4 GB RAM and 3 GHZ processor.  No other OS. Installed just fine, and then hangs at purple screen. Have to push pwr for 10 sec to shut down, reboot, given options about recovery etc.  Select generic and it boots, mostly.  Really annoying.

---

### Post by mörgæs on 2014-02-20
Which screen card do you use? Please post the output from 

```
lspci | grep -i vga
```

---

### Post by Matthew_Penny on 2014-02-21
Matthew Here - solved.  added RAM and did not clean contacts first....ubuntu wants hardware in proper shape.  Sorry, should have thought of that.

---

