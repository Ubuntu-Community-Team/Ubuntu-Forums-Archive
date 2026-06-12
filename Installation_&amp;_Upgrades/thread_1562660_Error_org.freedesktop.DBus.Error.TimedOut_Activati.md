---
title: "Error org.freedesktop.DBus.Error.TimedOut: Activation of org.freedesktop.PackageKit"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by W00ster on 2010-08-27
Every time I run apt-get, the following message is shown and I can not find out what to do to resolve it:

"Error org.freedesktop.DBus.Error.TimedOut: Activation of org.freedesktop.PackageKit timed out"

Not sure what the implications are of this timeout or if it has any implications at all but I;d like to figure out how to resolve it and I can not find anything useful by Googling either.

```

Hit http://us.archive.ubuntu.com maverick-proposed/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-proposed/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-proposed/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-proposed/universe i386 Packages
Error org.freedesktop.DBus.Error.TimedOut: Activation of org.freedesktop.PackageKit timed out
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done

```Any help is very welcome!

---

### Post by W00ster on 2010-08-28
Bump!

Nobody else seeing this message?

---

### Post by eugene_wolfe on 2011-10-28
I have it too, but don't know any solution...
Somebody can help us?

I use Kubuntu 11.10.

---

### Post by neovens79 on 2012-01-01
=== Workaround for this bug until PK 0.7.2 is released ===
Just execute this command to remove the broken plugin:
sudo rm /usr/lib/packagekit-plugins/libpk_plugin-update-check-processes.so
This will disable the check for running processes before an update is done too, but usually this shouldn't be a problem.

---

