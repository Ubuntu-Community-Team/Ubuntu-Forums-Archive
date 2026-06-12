---
title: "libc6-dev-i386 dependency problem"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by ilya-savitski on 2014-08-09
While installing libraries to compile ncmpcpp i got next error 
```

You might want to run 'apt-get -f install' to correct these.The following packages have unmet dependencies:
 gcc-4.8-multilib : Depends: libc6-dev-i386 (>= 2.11) but it is not installed
 lib32ncurses5-dev : Depends: lib32c-dev
 lib32tinfo-dev : Depends: lib32c-dev
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.19-0ubuntu6.1) but it is not installed
E: Unmet dependencies. Try using -f.

```

```

sudo apt-get -f install
...
Preparing to unpack .../libc6-dev-i386_2.19-0ubuntu6.1_amd64.deb ...
Unpacking libc6-dev-i386 (2.19-0ubuntu6.1) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.19-0ubuntu6.1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/fpu_control.h', which is also in package libc6-dev-amd64 2.19-0ubuntu6.1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.19-0ubuntu6.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried a lot of ways to fix it. Please help me

---

### Post by dave131 on 2014-08-10
So does it change any if you:

sudo apt-get install libc6-dev-i386 lib32c-dev

and then try to install again?

---

### Post by ilya-savitski on 2014-08-10
Thank you for your reply.


The result 

```

Errors were encountered while processing: /var/cache/apt/archives/libc6-dev-i386_2.19-0ubuntu6.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 

```

---

### Post by ian-weisser on 2014-08-10
> **ilya-savitski said:**
> 
```
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.19-0ubuntu6.1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/fpu_control.h', which is also in package libc6-dev-amd64 2.19-0ubuntu6.1
```

Two packages cannot provide the same file. Ever.
If two packages provide the same file, they *conflict*, and only one can be installed at a time.

libc6-dev-i386 and libc6-dev-amd64 conflict. They both provide '/usr/include/fpu_control.h'

The error is trying to tell you that the system cannot (and *will never be able to*) install libc6-dev-i386 while you have libc6-dev-amd64 installed.
It doesn't really get 'fixed'. You must choose which one you really want installed on your system.


Is there a reason you want both on your system?
Are you really doing multi-arch development? It's possible to do multiarch development on Ubuntu...but not that way.

---

### Post by ilya-savitski on 2014-08-10
I have just deleted all the packages that caused the problem, re-installed the libraries compilation process needs and here we are. Thank you for your time

---

