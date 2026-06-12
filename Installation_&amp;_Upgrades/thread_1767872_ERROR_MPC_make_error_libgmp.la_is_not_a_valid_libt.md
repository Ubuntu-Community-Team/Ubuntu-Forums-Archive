---
title: "ERROR :MPC make error libgmp.la is not a valid libtool"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by bhupinderjitbawa on 2011-05-26
I am trying to make mpc .
i first configured using following

```
./configure --prefix=/usr  --with-mpfr=$LFS/gcc-build/gcc-4.5.2/mpfr  --with-gmp-lib=$LFS/gcc-build/gcc-4.5.2/gmp/.libs
```

then i make using

```
root@bhupinder:/mnt/lfs/gcc-build/gcc-4.5.2/mpc# make
make  all-recursive
make[1]: Entering directory `/mnt/lfs/gcc-build/gcc-4.5.2/mpc'
Making all in src
make[2]: Entering directory `/mnt/lfs/gcc-build/gcc-4.5.2/mpc/src'

..
.
.
libtool: link: ranlib .libs/libmpc.a
[B]/bin/sed: can't read /usr/local/lib/libgmp.la: No such file or directory
libtool: link: `/usr/local/lib/libgmp.la' is not a valid libtool archive
make[2]: *** [libmpc.la] Error 1
make[2]: Leaving directory `/mnt/lfs/gcc-build/gcc-4.5.2/mpc/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/mnt/lfs/gcc-build/gcc-4.5.2/mpc'
make: *** [all] Error 2[/B]
root@bhupinder:/mnt/lfs/gcc-build/gcc-4.5.2/mpc#
```

googled a lot but not able to find solution.

---

### Post by partyk1d24 on 2011-10-24
Did you ever figure this out?

---

### Post by blackmail on 2011-10-24
I think user has aborted this thread for some time now...

---

### Post by partyk1d24 on 2011-10-24
Well then I hereby open it in honor of him :-) 

I am having the same issue per...

[http://code.google.com/p/android/issues/detail?id=21164](http://code.google.com/p/android/issues/detail?id=21164)

---

### Post by xkcdcode on 2012-08-09
Did you figure this out? I am having the same issue but only on 64-bit machine, not 32-bit.

---

