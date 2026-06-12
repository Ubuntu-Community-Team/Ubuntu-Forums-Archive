---
title: "USB install can't see flash drive files"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by Spyder810 on 2010-11-23
Hi I recently decided to install Ubuntu (ubuntu-10.10-desktop-i386.iso) to my 16GB flash drive (was fat32 originally, tried ntfs as well had boot issues,went back to fat32) to boot from it using the method on [this]("http://www.ubuntu.com/desktop/get-ubuntu/download") page using the Universal USB Installer. Install worked great, Ubuntu works great, problem is I can't see the rest of the files on my flash drive. Any help would be appreciated. Thanks :)

---

### Post by C.S.Cameron on 2010-11-23
Look in Filesystem/cdrom.
In 10.10 these are read only when booting from the flash drive.
You can access then with: ```
gksu nautilus
```

---

### Post by Spyder810 on 2010-11-23
Thanks! Never figured it would be under cd.

---

### Post by C.S.Cameron on 2010-11-24
The USB install is an image from a CD.
Took me a while to figure out myself.

---

