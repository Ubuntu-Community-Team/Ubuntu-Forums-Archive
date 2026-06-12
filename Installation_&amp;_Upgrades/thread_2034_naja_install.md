---
title: "naja install ?"
date: 2004-10-25
forum: Installation &amp; Upgrades
---

### Post by PaTTeX on 2004-10-25
hi guys (first sorry for my bad english ;) )
i have installed openssl 
but
i can't launch naja  [http://www.keyphrene.com/products/naja/](http://www.keyphrene.com/products/naja/)
```

root@julien:/home/julien # naja
OpenSSL: missing methods
No OpenSSL
```

please help me  :-k 
thanks in advance

---

### Post by Fabian on 2004-10-25
You installed OpenSSL ([www.openssl.org](www.openssl.org)) or PYOPENSSL-EXTENDED? :-)

---

### Post by PaTTeX on 2004-10-25
[QUOTE=Fabian]You installed OpenSSL ([www.openssl.org](www.openssl.org)) or PYOPENSSL-EXTENDED? :-)[/QUOTE]

openssl !
i can't install PYOPENSSL-EXTENDED

```
/home/julien/pyOpenSSL-extended-0.5.1 # python setup.py install
 Traceback (most recent call last):
  File "setup.py", line 13, in ?
    from distutils.core import setup, Extension
ImportError: No module named distutils.core

```

one idea ?

---

### Post by Fabian on 2004-10-25
You installed all prerequisites?

---

### Post by PaTTeX on 2004-10-26
[QUOTE=Fabian]You installed all prerequisites?[/QUOTE]

i can't install the last  : pyOpenSSL-extended-0.5.1
```
$ python setup.py build
Traceback (most recent call last):
  File "setup.py", line 13, in ?
    from distutils.core import setup, Extension
ImportError: No module named distutils.core

```

---

