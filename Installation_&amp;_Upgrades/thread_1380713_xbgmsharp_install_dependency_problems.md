---
title: "xbgmsharp install dependency problems"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by thumpszilla on 2010-01-14
Ok I am trying to install xbgmsharp as stated in title on xubuntu 9.04.  xbgmsharp is a program to extract xbox isos. **Disclaimer: no I am not pirating games simply wanting to extract the isos I made of legaly owned games and put those extracted files on my hard drive inside the xbox this is much easier for a 4 yr old to work with**. When I try to install the deb package I get this error Error: Dependency is not satisfiable: mono-classlib-1.0 I have tried sudo apt-get install mono-classlib-1.0 but get this ```
:~/Desktop$ sudo apt-get install mono-classlib-1.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mono-classlib-1.0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libmono-winforms1.0-cil libmono-system-messaging1.0-cil
  libmono-system-ldap1.0-cil libmono-sharpzip0.6-cil libmono-oracle1.0-cil
  libmono-npgsql1.0-cil libmono-microsoft7.0-cil libmono-ldap1.0-cil
  libmono-firebirdsql1.7-cil libmono-cscompmgd7.0-cil libmono-cairo1.0-cil
  libmono-bytefx0.7.6.1-cil libmono-accessibility1.0-cil libmono1.0-cil
  libmono-system1.0-cil libmono-system-web1.0-cil
  libmono-system-runtime1.0-cil libmono-system-data1.0-cil
  libmono-sqlite1.0-cil libmono-sharpzip0.84-cil libmono-security1.0-cil
  libmono-relaxng1.0-cil libmono-peapi1.0-cil libmono-data-tds1.0-cil
  libmono-corlib1.0-cil
E: Package mono-classlib-1.0 has no installation candidate
```

So I copied thos file names and pasted them after sudo apt-get install one line at at time and installed all that were not installed and other didn't install cause they were either already installed or a new version was. Then I tried to install the deb package again and got the same messege Error: Dependency is not satisfiable: mono-classlib-1.0. How can I fix this I really need to extarct some xbox iso files to transfer to my new hard drive. I also tried xbiso and had crashing problems with it as soon as I set the destination directory. I will be gone for a few day but would love to be able to fix this when I get back.. As always thanks peeps for all you great help.

---

