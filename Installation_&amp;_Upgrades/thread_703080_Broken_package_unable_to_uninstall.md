---
title: "Broken package unable to uninstall"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by jitenJeet on 2008-02-21
I am unable to uninstall a broken package (ubunty gutsy 7.10) on my laptop.
package is linux-backports-modules-2.6.22-14-386
I dont have a CD, and using Nonetdebs for installation.
How can i uninstall/ repair this broken package


The error thrown is:-

FATAL :- Could not open '/boot/System.map-2.6.22-14-386 : No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
Can not find /lib/modules/2.6.22-14-386
update-initramfs: failed for /boot/initrd.img-2.6.22-14-386
dpkg : error processing linux-backports-modules-2.6.22-14-386 ( -- purge ) :
    subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
   linux-backports-modules-2.6.22-14-386

E : Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

---

### Post by zvacet on 2008-02-21
```
sudo apt-get --purge remove linux-backports-modules-2.6.22-14-386
```

or 

```
sudo dpkg --remove --force-remove-reinstreq linux-backports-modules-2.6.22-14-386
```

---

### Post by jitenJeet on 2008-02-22
Sorry :(
both the commands didnt work... returning same exit status 1.

any guess.....

---

### Post by Partyboi2 on 2008-02-22
try the workaround suggested [here]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/149836")

---

### Post by jitenJeet on 2008-02-22
Thanks mate!!!!

Creating dummy directories and then purge. It works.

---

