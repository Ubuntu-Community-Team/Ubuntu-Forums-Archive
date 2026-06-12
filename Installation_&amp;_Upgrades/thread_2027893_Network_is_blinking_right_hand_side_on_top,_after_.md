---
title: "Network is blinking right hand side on top, after some time its exiting ."
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by saravanang86 on 2012-07-17
Hi.,

             I installed ubuntu 12.04 
uname -a --->Linux subuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux..
I want to connect my reliance netconnect + in ubuntu 12.04 .,I installed wvdial from this link [http://www.ubuntuupdates.org/package/core/precise/main/base/wvdial](http://www.ubuntuupdates.org/package/core/precise/main/base/wvdial). 64bit deb package.
I am not able to connect internet connection ,when i restart my computer or stop /start network manager which showing right hand side relience connection that time i am executing wvdial in terminal,Network logo is blinking after some time its exiting and not able to see Reliance connection..

I tryed in another way using gnome-ppp which giving cannot open modem
Log is:
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyACM0: Permission denied
--> Cannot open /dev/ttyACM0: Permission denied
--> Cannot open /dev/ttyACM0: Permission denied




Kindly guide me .....

Regards
Saravanan.G
+91-9790025271.

---

### Post by puller on 2012-08-04
Did you try to use ```
sudo
``` before the ```
gnome-ppp
``` command?

```
sudo gnome-ppp
```

---

