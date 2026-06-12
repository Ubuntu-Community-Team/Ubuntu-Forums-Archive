---
title: "Get error using build-essential"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by mzar on 2007-12-04
Hi all,

I got this error when using build-essential. Any idea how to solve it? :confused:

```
banie@feisty-fawn:~/deluge$ sudo apt-get install build-essentialReading package lists... Done
Building dependency tree       
Reading state information... Done
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
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```

---

### Post by mzar on 2007-12-05
No reply?

---

