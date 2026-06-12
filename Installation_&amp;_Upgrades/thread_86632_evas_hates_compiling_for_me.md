---
title: "evas hates compiling for me"
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by elglas on 2005-11-05
here be dar problem

```
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeQueryVersion'
../../src/lib/.libs/libevas.so: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make[4]: *** [evas_software_x11_test] Error 1
make[4]: Leaving directory `/root/cvs/e17/libs/evas/src/bin'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/cvs/e17/libs/evas/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/cvs/e17/libs/evas/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/cvs/e17/libs/evas'
make: *** [all-recursive-am] Error 2

```

---

### Post by mo_x on 2005-11-06
sudo apt-get install libxxf86vm-dev

---

### Post by Ubuntuud on 2006-02-10
Ah, dat is handig, dankjewel...

EDIT: Het werkt alleen niet...

Thanks, that's useful

EDIT: But it isn't working...

---

### Post by mo_x on 2006-02-10
What isn't working?

---

