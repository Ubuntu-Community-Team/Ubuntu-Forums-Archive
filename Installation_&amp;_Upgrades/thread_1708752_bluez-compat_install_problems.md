---
title: "bluez-compat install problems"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by Bodwin on 2011-03-17
Hello everyone,

I am using kubuntu 10.10. I wanted to install the bluez-compat package but it always hangs on unpacking. 

I tried with apt-get, aptitude and now I am trying with manually downloading the package and executing it with the package installer. Currently the output is:
```
(Reading database ... 
dpkg: warning: files list file for package `bluez-compat' missing, assuming package has no files currently installed.
(Reading database ... 5%(Reading database ... 10%(Reading database ... 15%(Reading database ... 20%(Reading database ... 25%(Reading database ... 30%(Reading database ... 35%(Reading database ... 40%(Reading database ... 45%(Reading database ... 50%(Reading database ... 55%(Reading database ... 60%(Reading database ... 65%(Reading database ... 70%(Reading database ... 75%(Reading database ... 80%(Reading database ... 85%(Reading database ... 90%(Reading database ... 95%(Reading database ... 100%(Reading database ... 171311 files and directories currently installed.)
Preparing to replace bluez-compat 4.69-0ubuntu2 (using .../bluez-compat_4.69-0ubuntu2_i386.deb) ...
Unpacking replacement bluez-compat ...

```

It just sits there without any progress for a lot of time.

All the times it hung I had to manually delete this file: /var/lib/dpkg/lock and do sudo dpkg --configure -a because I killed apt-get (or aptitude), simple control+c would not do.

---

