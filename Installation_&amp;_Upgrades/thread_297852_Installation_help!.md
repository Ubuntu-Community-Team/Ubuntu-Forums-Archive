---
title: "Installation help!"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by Ptah on 2006-11-11
Hello, after installation of dapper I tried to boot into it and this is what the screen said:

uncompressing linux... ok, booting the kernal
loading, please wait...
Fatal: module unknown not found
Mount: mounting/dev/sda1 on /root failed: no such device
Mount: mounting /root/dev on /dev/static/dev failed: no such file or directory
Target file system doesn't have /sbin/init

Then further down it read
/bin/sh: can't access tty; job control turned off

Can anyone help!!

My system specs are as follows:  Dell xps 600, Windows media center,(2) Samsung HD 149 raid, 2gb ram, 7800 gtx (SLI)

---

### Post by DaveBorealis on 2006-11-11
> **Ptah said:**
> 
Mount: mounting/dev/sda1 on /root failed: no such device


Your '/etc/fstab' might be messed up.  It should have a line in it like
```
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
```

This assumes that you've installed the rood directory on sda1 partition.

Best regards,
Dave

---

### Post by Ptah on 2006-11-11
How do I correct this problem?

---

