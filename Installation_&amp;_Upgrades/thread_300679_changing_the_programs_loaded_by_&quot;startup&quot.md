---
title: "changing the programs loaded by &quot;startup&quot;"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by fabianhaerle on 2006-11-16
Hi,

I just installed ubuntu 6.10 server according to the very nice guide on [http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10). Now I want to change the programs / services loaded at startup time. Actually I don't need procmail yet but I don't want to uninstall it but just to disable it.
With the old runlevels this would have been easy. How do I do it with the new "startup" system? I don't have the time to write a complete set of scripts and I don't want to install X and Gnome.

Thanks for your help,

Fabian

---

### Post by adwait on 2006-11-16
How about using
```
sudo rcconf
```

If its not installed, you might need to install it with.

---

### Post by fabianhaerle on 2006-11-16
I just tried it. It seems to modify the current run level. Now I'm a bit confused. I thought there were no runlevels any more...???

---

### Post by adwait on 2006-11-16
I haven't upgraded yet so I don't know about run levels being removed from 6.10. I don't think they have removed run levels, perhaps eliminated the need for the user to access or change them...but not completely eliminated them . Not sure rhough..

---

