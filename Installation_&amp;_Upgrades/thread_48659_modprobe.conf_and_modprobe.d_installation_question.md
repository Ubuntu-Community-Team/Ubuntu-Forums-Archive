---
title: "modprobe.conf and modprobe.d installation question"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by flak9 on 2005-07-13
I was following this [guide](http://www.ubuntuforums.org/showthread.php?t=25683)  trying to install my Broadcom wireless driver.  I can get the wireless card to show up in the Networking window, but when I reboot the laptop it gives me this warning.

```

WARNING: /etc/modprobe.conf exists but does not include /etc/modprobe.d/
```

When I reboot and do a modprobe ndiswrapper, I can goto the Network and see my wireless device again, but I think I only have an issue when it reboots. How can I restore modprobe.d?

I have removed the ndiswrapper source and utils through synaptic. I think that i might have possibly deleted something called modprobe.d, when I was fussing around earlier. Im not sure whats going on.  This has also affected my sound in gnome.

What should I try next?  :-?  :-?

---

### Post by Xian on 2005-07-13
Open the /etc/modprobe.conf file and add this line:
```
include /etc/modprobe.d/
```

---

