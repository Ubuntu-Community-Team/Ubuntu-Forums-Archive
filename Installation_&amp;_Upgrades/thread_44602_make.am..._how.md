---
title: "make.am... how?"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by Trojan1313 on 2005-06-26
How do I isntall a make.am file? The terminal says it can't find a makefile, but there is a file called make.am.

Thanks in advance.

---

### Post by Xian on 2005-06-27
Can you provide a link to the package you are attempting to install?
It would be helpful in determining what is required.

---

### Post by Trojan1313 on 2005-06-28
It's more then one program that won't install, but I can give you a link to one of the programs that I'm having problems with.

[http://www.imagemagick.org/script/download.php](http://www.imagemagick.org/script/download.php)

---

### Post by doclivingston on 2005-06-28
The reason you don't have a makefile is usually

a) you haven't done a ./configure; or
b) if you've downloaded it from CVS, you'll need to run autogen.sh (or the equivalent)

---

### Post by Trojan1313 on 2005-06-28
[QUOTE=doclivingston]The reason you don't have a makefile is usually

a) you haven't done a ./configure; or
b) if you've downloaded it from CVS, you'll need to run autogen.sh (or the equivalent)[/QUOTE]
 I have one, but it's a make.am.

---

### Post by doclivingston on 2005-06-29
If it's a real makefile, you can run make using it with
```
make -f make.am
```

---

