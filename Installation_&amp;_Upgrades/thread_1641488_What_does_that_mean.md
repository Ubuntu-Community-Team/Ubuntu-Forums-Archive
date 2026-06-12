---
title: "What does that mean"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by hissou86 on 2010-12-09
hi everybody,
please, what does that mean?
```
 * catchsegv: catch segmentation faults in programs
 * getconf: query system configuration variables
 * getent: get entries from administrative databases
 * iconv, iconvconfig: convert between character encodings
 * ldd, ldconfig: print/configure shared library dependencies
 * locale, localedef: show/generate locale definitions
 * rpcinfo: report RPC information

```

this is what i found when i tried to install libc-bin package at this adress : 
[http://packages.ubuntu.com/lucid/libc-bin](http://packages.ubuntu.com/lucid/libc-bin)

thanks

---

### Post by hissou86 on 2010-12-10
hi
i need to have answer because i face that thing many times when installing packages

---

### Post by Rubi1200 on 2010-12-10
Please run the following command in the terminal and post the output here if there are errors.

```
sudo dpkg --configure -a
```

Thanks.

---

### Post by hissou86 on 2010-12-10
After running dpkg --configure -a, there is nothing as output.

Thanks

---

### Post by plucky on 2010-12-10
> **hissou86 said:**
> hi everybody,
please, what does that mean?
```
 * catchsegv: catch segmentation faults in programs
 * getconf: query system configuration variables
 * getent: get entries from administrative databases
 * iconv, iconvconfig: convert between character encodings
 * ldd, ldconfig: print/configure shared library dependencies
 * locale, localedef: show/generate locale definitions
 * rpcinfo: report RPC information

```

this is what i found when i tried to install libc-bin package at this adress : 
[http://packages.ubuntu.com/lucid/libc-bin](http://packages.ubuntu.com/lucid/libc-bin)

thanks


If you open **Synaptic Package Manager** and search for **libc-bin** you will find the installed files for this package is the binaries for those programs.
To find what those programs do open a term and input ```
man getconf
man getent
man iconv
man ldd
etc
```


Good Luck

---

