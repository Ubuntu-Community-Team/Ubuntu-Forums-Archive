---
title: "Lucid - Update manager -- why???"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by MakOwner on 2010-11-16
I keep getting an alert for an update, but each time I try I get this:

W: Failed to fetch [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-1lucid1_i386.deb](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-1lucid1_i386.deb)
  403  Forbidden


What's the point of advertising the update if I can't install it?

---

### Post by sikander3786 on 2010-11-17
Some servers have been down yesterday for a few hours.

Go to System > Administration > Software Sources and change the server to Main.

Now from Terminal,

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

I hope you are not getting that error anymore.

---

