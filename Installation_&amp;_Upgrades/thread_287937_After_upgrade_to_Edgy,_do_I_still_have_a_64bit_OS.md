---
title: "After upgrade to Edgy, do I still have a 64bit OS?"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by eschwalb on 2006-10-29
I upgraded from Dapper amd64 to Edgy last night, and when I boot now, GRUB lists 2.6.17-10 generic in addition to the older kernel, 2.6.15-27-amd64-generic.  I'm wondering how to tell if the newest kernel is still 64 bit as it no longer says amd64 explicitly.  (I upgraded by changing dapper to edgy in my sources.list, which as I've come to learn isn't the officially recommended way of upgrading).  Any recommendations on how I would go about determining this?

Thanks,

---

### Post by eschwalb on 2006-10-29
uname -r returns the following:

2.6.17-10-generic

So I think I don't have the 64bit version installed...

---

### Post by timgood on 2006-10-29
As far as I am aware the generic kernel selected by the install is 64bit.

---

### Post by jhaitas on 2006-10-29
```
uname -a
```

---

### Post by IbeeX on 2006-10-29
Where is gone AMD k8 kernel??

---

### Post by jhaitas on 2006-10-29
what?

---

### Post by eschwalb on 2006-10-29
uname -a does indicate that its the 64 version, thanks for the help

---

### Post by jhaitas on 2006-10-29
pleasure

---

