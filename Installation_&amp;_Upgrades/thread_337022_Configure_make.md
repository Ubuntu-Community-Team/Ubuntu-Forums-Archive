---
title: "Configure make"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by Gelupah on 2007-01-12
How can I configure "make" to use the right - 386 - headers?

> 
sudo make
make: *** /lib/modules/2.6.17-10-generic/build: No such file or directory.  Stop.
rt2500.ko failed to build!
make: *** [module] Error 1


I removed the generic headers (make doesn't seem to work with them) , uninstalled make etc, thinking by reinstalling it it would then chose the 386 directory, but no such luck. Haven't reinstalled generic headers.

Spent all day on this stupid problem, just want to compile some drivers! Any help is greatly appreciated!

---

### Post by jd65pl on 2007-01-12
```
'uname' -a
```

Will show you the header info.

There may be a better way tho

---

### Post by Gelupah on 2007-01-12
I get the following:

> 
Linux LSF 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux


---

### Post by jd65pl on 2007-01-12
Try this to install the headers

```
sudo aptitude update
sudo aptitude install linux-headers-$(uname -r)

```

---

### Post by Gelupah on 2007-01-12
Thanks, but the problem is not installing the headers, it's getting "make" to use the correct ones!

Any ideas?

---

### Post by arnieboy on 2007-01-12
> **Gelupah said:**
> Thanks, but the problem is not installing the headers, it's getting "make" to use the correct ones!

Any ideas?
make greps your kernel version and looks for the corresponding kernel dev packages path. Just follow jd65pl's instructions and do a make again

---

### Post by Gelupah on 2007-01-13
Thanks, I've tried but seem to have no such luck:

> 
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `rt2500-cvs-2007011207/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
rt2500.ko failed to build!
make: *** [module] Error 1


Am I right in saying it should be using 386 headers? And if so How can I get it to?!

Thanks

---

### Post by Gelupah on 2007-01-16
Anyone? Please?

---

