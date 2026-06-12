---
title: "Beryl compiling problems"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by jpe2000 on 2007-02-16
I'm using Ubutnu 6.06 Dapper LTS right now and I'm having some compiling problems with Beryl. Please help me.

Here's my error code:

```
In file included from ../include/beryl-settings.h:8,
                 from main.c:24:
../include/beryl.h:57:26: error: GL/glxtokens.h: No such file or directory
make[2]: *** [main.lo] Error 1
make[2]: Leaving directory `/home/josh/Desktop/beryl-core-0.1.9999.2/libberylsettings'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/josh/Desktop/beryl-core-0.1.9999.2'
make: *** [all] Error 2

```



Thanks.

---

### Post by jpe2000 on 2007-02-16
Okay, never mind. I just had to download a header file. Now I have succesfuly installed it but I get an error about Xcompsite.



```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension

```

---

### Post by Devz0r on 2007-03-23
I am having the same compiling problem.  Where did you download this header file?

---

### Post by nehuenmingote on 2007-04-22
> **Devz0r said:**
> I am having the same compiling problem.  Where did you download this header file?

Here you go:

[http://cvsweb.xfree86.org/cvsweb/xc/include/GL/glxtokens.h](http://cvsweb.xfree86.org/cvsweb/xc/include/GL/glxtokens.h)

---

### Post by dj3mb3 on 2007-12-20
Hi to all,

I am in the same situation of Devz0r ...

Now I have downloaded glxtokens.h from the link, and I have put it in /urs/include/GL
so the make command don't generate other error to the output

But if I try 'make check' i have this

...
Making check in po
make[1]: Entering directory `/home/dj3mb3/Desktop/beryl/beryl-core-0.2.1/po'
rm -f missing notexist
srcdir=. ../intltool-update -m
Unmatched ( in regex; marked by <-- HERE in m/^beryl-core-esyscmd( <-- HERE ../VERSION;echo-n$VERSION/.*$/ at ../intltool-update line 307, <FILE> line 217.
make[1]: *** [check] Error 9
make[1]: Leaving directory `/home/dj3mb3/Desktop/beryl/beryl-core-0.2.1/po'
make: *** [check-recursive] Error 1

how can I resolve it?

tnks

Ps:

I'm also trying to do this with the beryl manager
...
Making check in po
make[1]: Entering directory `/home/dj3mb3/Desktop/beryl/beryl-manager-0.2.1/po'
rm -f missing notexist
srcdir=. ../intltool-update -m
Unmatched ( in regex; marked by <-- HERE in m/^beryl-manager-esyscmd( <-- HERE ../VERSION;echo-n$VERSION/.*$/ at ../intltool-update line 307, <FILE> line 117.
make[1]: *** [check] Error 9
make[1]: Leaving directory `/home/dj3mb3/Desktop/beryl/beryl-manager-0.2.1/po'
make: *** [check-recursive] Error 1

but the results are the same

tnks & bye

---

