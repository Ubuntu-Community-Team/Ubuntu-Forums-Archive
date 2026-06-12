---
title: "how can I remove the ubuntu boot loader ?"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by pumber on 2010-01-07
I have my ubuntu removed but not the boot loader. How can I remove it ?

Thank you !

---

### Post by kansasnoob on 2010-01-07
> **pumber said:**
> I have my ubuntu removed but not the boot loader. How can I remove it ?

Thank you !

Need more info, what other operating system(s) are on the machine?

---

### Post by pumber on 2010-01-07
WinXP Prof only !

---

### Post by kansasnoob on 2010-01-07
If you have your Win XP recovery/installation disc look here:

[http://www.ehow.com/how_5602134_restore-master-boot-record.html](http://www.ehow.com/how_5602134_restore-master-boot-record.html)

If not, but you do have an Ubuntu Live CD we can use that but I'd first need you to boot the Live CD and post the output from terminal of:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

