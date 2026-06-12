---
title: "[SOLVED] cpio error viewing initrd"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by bdk6m2007 on 2008-02-17
Hello-

I'm trying to view the contents of the initrd.gz that comes with the server install disk.  I'm getting an error from cpio when trying to decompress the file:

```

brian@ralph:/local/tmp$ sudo gzip -dc ../initrd.gz | cpio -id
cpio: dev/console: Cannot mknod: Operation not permitted
cpio: dev/null: Cannot mknod: Operation not permitted
25369 blocks

```


Any ideas on why I'm getting this error?

---

### Post by bdk6m2007 on 2008-02-18
Ok well it turns out this isn't really an error, it's just complaining that it can't create the devices (which it shouldn't be able to do).  Everything else decompressed fine, I just never saw anywhere that this is an OK error.

---

