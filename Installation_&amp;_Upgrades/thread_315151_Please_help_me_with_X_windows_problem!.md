---
title: "Please help me with X windows problem!"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by chuugokujin on 2006-12-08
I can never install Ubuntu 6.10 on my PC.
It always says something wrong with my x-server!
But there is nothing wrong if I use other Distributions such as SUSE or Mandriva.

AMD 64 3000+
2G Memory
ATI Radeon x850

Thanks !

---

### Post by aysiu on 2006-12-08
I'd stick with SuSE or Mandriva, then. Hardware detection should be one of the main reasons you pick a particular distro over another. That said, you can also try one of the tricks here:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by chuugokujin on 2006-12-08
Thanks dude.I think I should stick with other ditro then.

---

### Post by wpshooter on 2006-12-08
Try installing from the ALTERNATE (text based) CD instead of the DESKTOP (live CD) version.

---

### Post by UberGeekInc on 2006-12-09
> **chuugokujin said:**
> I can never install Ubuntu 6.10 on my PC.
It always says something wrong with my x-server!
But there is nothing wrong if I use other Distributions such as SUSE or Mandriva.

AMD 64 3000+
2G Memory
ATI Radeon x850

Thanks !

Perhaps a binary ATI driver?  

If you tried another distro that works, snag the /etc/X11/xorg.conf.  Install Edgy - follow the wiki about installing ATI driver:

   [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Then compare the xorg.conf from the other distro to the installed.  With luck, the previous step will have you up and running.

---

