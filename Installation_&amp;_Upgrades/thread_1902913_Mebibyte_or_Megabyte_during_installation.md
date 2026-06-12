---
title: "Mebibyte or Megabyte during installation?"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by spielball on 2012-01-01
I'd like to re-install my OS or install Kubuntu instead. However, I don't know if 11.10 uses Mebibyte or Megabyte when creating the partitions manually during installation?

---

### Post by darkod on 2012-01-01
I believe it's 1000x1000, not 1024x1024.

So, if you want 20GiB for example, it would be 20480MiB but you have to calculate for the install the MB something like 21474MB.

---

### Post by spielball on 2012-01-02
Thank you! I also dug around a bit more and found this:

[http://askubuntu.com/questions/465/is-it-true-that-ubuntu-will-no-longer-measure-file-size-unit-as-byte-megabyte](http://askubuntu.com/questions/465/is-it-true-that-ubuntu-will-no-longer-measure-file-size-unit-as-byte-megabyte)

Hence, Ubuntu uses the decimal interpretation, which is correct for this prefix. In other words: Ubuntu uses 10 as the base unit and not 2. Therefore, in Ubuntu, 1 MB = 10^10 byte = 1000 byte; 1GB = 10^10 MB = 1000 MB, etc.

Whereas 1MiB = 2^10 = 1024 byte. In GParted, partition sizes are displayes in GiB. But in Ubuntu's disk tool, they're displayed in GB.

I appreciate it very much that Ubuntu stays coherent there.

So, during install, if I want a 20GB partition, I simply have to enter 20000MB.

But why would the following be (assumed we'd have MiB)?
> [...] but you have to calculate for the install the MB something like 21474MB

---

### Post by darkod on 2012-01-02
Depends if you want a 20GB or 20GiB partition. In my example I wrote 20GiB which in that case would be 21474MB.

If you want 20GB (the decimal standard), yes it would be simply 20000MB.

---

