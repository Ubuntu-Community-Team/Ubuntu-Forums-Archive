---
title: "How can i uninstall a program which i've compiled &amp; installed from the source before?"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by k@y@ on 2006-11-27
As you've red, i wonder how can do this?

I couldn't see those programs i've compiled and installed before in "add/remove programs" and i couldn't uninstall it with "apt-get remove"...

Any help would be appreciated.

---

### Post by frodon on 2006-11-27
You can only uninstall them through apt-get or synaptic if you used checkinstall for your compilation.
If you didn't you may be able to uninstall the apps if you go in the directory where you compiled the apps (i mean the directory with the sources) and run a : ```
sudo make uninstall
```

---

### Post by k@y@ on 2006-11-27
Thanks. I've just tried with this command but i got an error something like: "make: *** Target There is no rule to compile 'checkinstall', stopped."

ANy idea?

---

