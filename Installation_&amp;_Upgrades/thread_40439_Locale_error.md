---
title: "Locale error"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by shmk on 2005-06-09
When I start gnome I got this error

"Language it_IT.UTF-8 does not exist, using system default"

Probably I have installed/uninstalled some module that make this mistake...
Someone can give me a hand to fix it ?

Thx

---

### Post by zAo on 2005-06-09
try
```
sudo dpkg-reconfigure locales
```

I only have Solaris and AIX here, so I cannot test it. Otherwise try 'locale' in stead of 'locales'.

---

### Post by shmk on 2005-06-09
I tried to install locales package from synaptic but got this error:

[I]The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in preferencies

locales:
 Depends: glibc-2.3.2.ds1-20ubuntu13[/I]

And I cannot see glibc-2.3.2.ds1-20ubuntu13 in synaptic... and I haven't found it in *packages.ubuntu.com* too...  ](*,)

---

### Post by Alexander Kirillov on 2005-06-09
[QUOTE=shmk]I tried to install locales package from synaptic but got this error:

[I]The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in preferencies

locales:
 Depends: glibc-2.3.2.ds1-20ubuntu13[/I]

And I cannot see glibc-2.3.2.ds1-20ubuntu13 in synaptic... and I haven't found it in *packages.ubuntu.com* too...  ](*,)[/QUOTE]
 Try disabling backports and marillat repository if you have them - I suspect that synaptic is trying to get locales from backports, which has newer version but is also causing dependency problems.  You should be fine with locales package from usual hoary repository

---

### Post by shmk on 2005-06-09
[QUOTE=Alexander Kirillov]Try disabling backports and marillat repository if you have them - I suspect that synaptic is trying to get locales from backports, which has newer version but is also causing dependency problems.  You should be fine with locales package from usual hoary repository[/QUOTE]
 DOH !
I have installed libc6 and locales for breezy... but they give me errors on hoary, is there a method to reinstall the right hoary version without lose all packages that depens from them ?

---

### Post by Alexander Kirillov on 2005-06-09
[QUOTE=shmk]DOH !
I have installed libc6 and locales for breezy... but they give me errors on hoary, is there a method to reinstall the right hoary version without lose all packages that depens from them ?[/QUOTE]
 I believe synaptic gives you an option of forcing "upgrade" to a given version rather than the latest: select the package, then in "package" menu, select "Force version". Never tried it myself, though.

---

### Post by shmk on 2005-06-11
[QUOTE=Alexander Kirillov]I believe synaptic gives you an option of forcing "upgrade" to a given version rather than the latest: select the package, then in "package" menu, select "Force version". Never tried it myself, though.[/QUOTE]

Perfect,
Thx  :)

---

