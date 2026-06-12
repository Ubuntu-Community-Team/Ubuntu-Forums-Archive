---
title: "c compiler problem."
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by freemanty on 2007-02-13
anybody can help me with this:

I am trying to install a package, here is the error:
checking for C compiler default output file name... configure: error: C 
compiler cannot create executables

I check the config.log file, which indicate :
configure:1660: $? = 1
configure:1683: checking for C compiler default output file name
configure:1686: cc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory

How to fix this..  Thanks!

---

### Post by jpeddicord on 2007-02-13
Type `sudo apt-get install build-essential` in a terminal. That will install everything you need to compile that program.

Jacob

---

### Post by freemanty on 2007-02-13
Works.. 

many thanks!

---

### Post by ranjan392b on 2007-03-28
I did what you had suggested and I got this error :

[COLOR="Cyan"]$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
[/COLOR]

Please help me out! This is really starting to frustrate me

---

### Post by taurus on 2007-03-28
Try

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

p.s.  What's up with the color?

---

### Post by ranjan392b on 2007-03-28
Thans man it worked.....
sorry about the color man.....chose the wrong one!

---

### Post by ranjan392b on 2007-03-28
Thanks man it worked.....
sorry about the color man.....chose the wrong one!

---

