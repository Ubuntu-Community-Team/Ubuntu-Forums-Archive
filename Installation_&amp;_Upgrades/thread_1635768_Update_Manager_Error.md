---
title: "Update Manager Error"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by joerow on 2010-12-02
I'm trying to install updates using the update manager, the updates are shown in the image below. [IMG]http://img408.imageshack.us/img408/6226/screenshotosq.png[/IMG]

but when I try to install the packages I get the error:

> Requires installation of untrusted packages

The action would require the installation of packages from unauthenticated sources.

Details:
firefox firefox-branding firefox-gnome-support xulrunner-1.9.2

Not sure what I should do. I've not changed any of the repositories recently. Although I did install the firefox 4.0 beta for a while but then removed it. 

Any ideas?

Thanks

Joe

---

### Post by plucky on 2010-12-02
What does ```
sudo apt-get update
``` from a terminal show you?

---

### Post by joerow on 2010-12-02
It runs through them all then on the last line it gives:
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE

---

### Post by plucky on 2010-12-02
> **joerow said:**
> It runs through them all then on the last line it gives:

Try from a terminal ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EF4186FE247510BE
sudo apt-get update
```

If that doesn't work,post output of ```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

Good Luck

---

### Post by joerow on 2010-12-02
[QUOTE=plucky;10190331]Try from a terminal ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EF4186FE247510BE
sudo apt-get update
```

That worked great thanks!

---

