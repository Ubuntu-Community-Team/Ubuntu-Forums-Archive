---
title: "Removing Program"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by 0ptiK on 2005-10-22
Hi all,

I installed Tiger the other day and it's not working, now I want to remove it ... problem is, being a linux newbie, I don't know the command; anyone?

I believe the command has something to do with dist, -r dist or something?

And just one more thing; do you use the same command to remove any program?

Thanks in advance.

---

### Post by aysiu on 2005-10-22
Tiger? As in Mac OS X Tiger?

---

### Post by adwait on 2005-10-22
normally to remove any program you installed using apt-get, you can use
```
sudo apt-get remove <packagename>
```

If you installed using dpkg, then u can use
```
sudo dpkg -r <packagename>
```

---

### Post by 0ptiK on 2005-10-23
Don't think so aysiu, but not entirely sure; all I know is that it's a security tool.

I originally downloaded it from TAMU at CIS Network Group ... before realising it was listed in Synaptic, so I reinstalled it from Synaptic and it works now; so I guess I can use Synaptic to uninstall it if need be.

Thanks Adwait, I'll keep that in mind for next time; I just recall from a thread I read a while back something about remove dist or something. 

Thanks again for the advice guys. ;)

---

