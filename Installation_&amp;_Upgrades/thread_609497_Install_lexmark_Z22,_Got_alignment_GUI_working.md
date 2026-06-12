---
title: "Install lexmark Z22, Got alignment GUI working"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by awalker2561 on 2007-11-11
Here's how I install the driver and the GUI

Install the lexmarkz22-z32-1.0-5.i386.rpm by converting it to deb with alien

Link the files in /usr/lib directory as root

ln -s /usr/local/lib/libvdk.so.1.2.0 libvdk.so.1
ln -s /usr/local/lib/libvdk.so.1.2.0 libvdk.so
ln -s /usr/local/lib/libvdkgnome.so.1.2.0 libvdkgnome.so.1
ln -s /usr/local/lib/libvdkgnome.so.1.2.0 libvdkgnome.so
ln -s /usr/local/lib/libvdkcompo.so.1.2.0 libvdkcompo.so.1
ln -s /usr/local/lib/libvdkcompo.so.1.2.0 libvdkcompo.so
ln -s /usr/lib/libstdc++.so.6.0.9 libstdc++-libc6.1-1.so.2 (Debian it's "/usr/lib/libstdc++.so.6.0.8 libstdc++-libc6.1-1.so.2")

Run the lexmark-foomatic-kit (reinstall something first)

Ok, so I gotten this far. Now Ubuntu won't work with the driver I install and created BUT!!! It DOES work in Debian Etch !!! So I assume this has to do with the Debian operation system. Tell me what is needed to get it to work.

---

