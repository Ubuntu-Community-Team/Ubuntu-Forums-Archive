---
title: "edgy killed vmware :'("
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by kichimi on 2006-10-27
Ok, i upgraded to edgy last night, all went fine, went you use vmware server, and it didnt work, i thought to myself, ok, last time this happened i needed to dload the kernal headers, so i did and i reinstalled it, but it did not work, im stuck now, what should i do? Thanks in advance

---

### Post by boban on 2006-10-27
> **kichimi said:**
> Ok, i upgraded to edgy last night, all went fine, went you use vmware server, and it didnt work, i thought to myself, ok, last time this happened i needed to dload the kernal headers, so i did and i reinstalled it, but it did not work, im stuck now, what should i do? Thanks in advance

Are there some errors showing up? Did you try:

```

sudo vmware-config.pl

```

---

### Post by ampop on 2006-10-27
I have the same problem.

After upgrade to 6.10 (Edgy Eft), I did:
```
sudo apt-get install linux-headers-2.6.17-10-386
```
and:
```
sudo /usr/bin/vmware-config.pl
```
And now whem I run vmware I have this message:
```
ampop@acer-laptop:~$ /usr/bin/vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
```

There is a solution?
Thanks,

---

### Post by kichimi on 2006-10-27
I get exactly the same, and i ran ```
sudo /usr/bin/vmware-config.pl
```  after i installed it

---

### Post by Goliash on 2006-10-27
The same problem, the same tries to solve it ... can anyone help us?

---

### Post by nbx909 on 2006-10-27
see what i said here [http://ubuntuforums.org/showthread.php?p=1672356#post1672356](http://ubuntuforums.org/showthread.php?p=1672356#post1672356)

---

