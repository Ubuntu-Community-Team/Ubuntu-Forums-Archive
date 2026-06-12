---
title: "Buid source into deb package ?"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by Vilius on 2006-07-05
And install after bilding, of course.
Is it possible ?
It's much easier to monitor which files are inslalled and so on.

thanks
vilius

---

### Post by christhemonkey on 2006-07-05
You want checkinstall
```
sudo apt-get install checkinstall 
```

It works *most* of the time,
and leaves you with a nice .deb that can be uninstalled easily in synaptic.

To use it, you just replace 'sudo make install'  with 'sudo checkinstall' (with out 's of course)

---

### Post by joft on 2006-07-05
Hi,

yes, you can download the source package for every single debian package and re-build it. Then you can install your newly build .deb files by using "dpkg -i <file>.deb".

You can list files contained in a package by using package.ubuntu.com for example. There, search for the package in question and you'll get a page where you can click on a link called "list of files" (for each architecture).

---

