---
title: "libopenobex1 not found"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by Arador Aristata on 2007-12-24
I am trying to install Blueman through the synaptic pakage manager. This is the error it gives me:

Depends: gnome-bluetooth but it is not going to be installed
Depends: gnome-vfs-obexftp but it is not going to be installed

Ok, so I go to gnome-vfs-obexftp and try that and it tells me:

Depends: libopenobex1  but it is not installable

Problem is, I have libopenobex1 installed already. Why is it not finding it and how can I remedy this?

Thank you in advance.

---

### Post by Partyboi2 on 2007-12-24
try installing
 libopenobex1-dev
```
sudo apt-get install libopenobex1-dev
```

---

### Post by Arador Aristata on 2007-12-24
I installed libopenobex1 from the Ubuntu site, opening the download with the pakage manager and that seemed to do the trick. Will use that method as far as i can from now on. Thank you for the tip.

---

