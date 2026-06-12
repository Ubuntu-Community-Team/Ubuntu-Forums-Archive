---
title: "Firefox problem?"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by ruvil on 2005-09-13
Hello!
This morning ubuntu wanted to update my firefox version, and i thinked.. hmm.. okay.. but under the installation i got an error message:
E: mozilla-browser:  underprocess post-installation script gave errorcode 1
E: firefox:  underprocess post-installation script gave errorcode 1
Anyone know how to "repair" firefox? Because i have tried to remove it and so and install it again.. thats not working either.
Is there i soloution to this?


/Ruvil

---

### Post by heimo on 2005-09-13
I'm not sure, but this sounds a bit like dpkg database corruption problem. These instructions have a small chance to mess your installation. This is what I'd try:
```
sudo rm -f /var/lib/dpkg/info/mozilla-firefox.*
sudo apt-get --purge remove mozilla-firefox
sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support

```

---

