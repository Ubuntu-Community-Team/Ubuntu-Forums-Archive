---
title: "deleted my /sbin/insmod"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by HectorG on 2009-12-09
Im not sure if this is the correct place to poist this...

I mistakenly deleted my /sbin/insmod file is there a way to recover this file by reinstalling a package?

---

### Post by phillw on 2009-12-09
> **HectorG said:**
> Im not sure if this is the correct place to poist this...

I mistakenly deleted my /sbin/insmod file is there a way to recover this file by reinstalling a package?

Hi,

I *think* it should be on your LiveCD, you'd need to boot with the LiveCD of your version of Ubunut and copy it over to your hard drive.

Regards,

Phill.

---

### Post by sisco311 on 2009-12-09
> **HectorG said:**
> Im not sure if this is the correct place to poist this...

I mistakenly deleted my /sbin/insmod file is there a way to recover this file by reinstalling a package?

yep:
```
sudo apt-get install --reinstall module-init-tools
```

EDIT: btw, 

```
dpkg -S /sbin/insmod
```
lists the package which provides /sbin/insmod

---

### Post by HectorG on 2009-12-10
That worked THANK YOU!!!!

---

