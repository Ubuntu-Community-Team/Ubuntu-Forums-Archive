---
title: "Language Support"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by 3dmatrix on 2008-11-28
I am trying to add chinese language support since many days, but am getting the following errors, plz help !

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en/language-pack-kde-en_8.04+20080527_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en/language-pack-kde-en_8.04+20080527_all.deb)
  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh/language-pack-gnome-zh_8.04+20080527_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh/language-pack-gnome-zh_8.04+20080527_all.deb)
  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-zh/language-pack-kde-zh_8.04+20080527_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-zh/language-pack-kde-zh_8.04+20080527_all.deb)
  404 Not Found [IP: 91.189.88.31 80]

---

### Post by cariboo on 2008-11-29
Have you run:

```
sudo apt-get update
```

lately? Or tried a different mirror?

Jim

---

### Post by 3dmatrix on 2008-11-29
Thanx I updated apt and the files were installed.

---

