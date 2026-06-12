---
title: "Russian windows-1251 encoding in vfat filenames"
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by titmouse on 2005-06-06
Hi!

I can see only ???????????(invalid encoding) instead of Russian filenames in Windows vfat partitions in Nautilus.

Here is my fstab string:
/dev/hda7       /Workspace      vfat    defaults,rw,users,codepage=866,iocharset=cp1251        0       0

I've managed to enable Russian filenaming in Mandrake 10 using iocharset=microsoft-cp1251 (or windows-cp1251), but I can't in Ubuntu.

Please help.

---

### Post by ZeroA4 on 2005-06-06
I have Brazilian Portuguese vfat mounted in fstab with:

/dev/hda6  /mnt/arquivo   vfat     umask=000,codepage=850,iocharset=iso8859-15,utf8   0   0

It is showing the pt-br special caracteres corectly.
So i guess that you should add ",utf8" at the end

```
codepage=866,iocharset=cp1251,utf8
```

---

### Post by titmouse on 2005-06-07
Thanks ZeroA4, it works fine now.
,utf8 was unobvious for me and undocumented well.

For developers:
Why such things, as iocharset and codepage are not set during installation uf Ubuntu When choosing mounted partition attributes iocharset and codepage must be set to default values for previous regional settings.

---

