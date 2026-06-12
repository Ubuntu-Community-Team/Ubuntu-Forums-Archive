---
title: "why aren't apps on my Gutsy machine kept current?"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by RgnKjnVA on 2008-01-11
I thought the point of the Update Manager and Synaptic was to provide a no-brainer method of keeping apps up to date. However, GIMP just got updated from rc3 today though GIMP 2.4 was  released a long time ago. I also notice that audacious is out of date as well as some other apps on my machine. Why is this? Is there something I don't have configured? Is there a way to tell what repository an app uses, audacious for example? 'apt-get update' doesn't find the latest version. :confused:

---

### Post by balaknair on 2008-01-11
hi
even though an application may be updated it may not be immediately served up on the official Ubuntu repositories since it has to be tested for compatibility, stability and reliability by the Ubuntu team before it is released as an official Ubuntu package. This is to ensure that an update doesn't break other packages and to prevent regressions. Software on these repositories is supported by the Ubuntu team, so they try to make sure it's OK(and that any dependencies are OK too) before releasing the update packages as 'official'.
If you want to try out the latest version of an app even before it's tested by the Ubuntu team you can do so by enabling the the pre-released updates and unsupported updates in software sources(System menu> Administration> Software sources--> updates). You can also enable other repositories in software sources--> Third party software. Keep in mind though that this stuff has not been tested by the Ubuntu team, and may be buggy.

---

### Post by RgnKjnVA on 2008-01-11
ah! OK thx

---

### Post by domeboy on 2008-01-13
Thanks for the hellp!:)

---

### Post by TBerben on 2008-01-13
Have you enabled the backports repository? It contains newer versions of aplications which should be more or less stable and safe to use with ubuntu. The address is included in /etc/apt/sources.list but it is commented out by default. To enable it just remove the '#' from the lines containing the backport repository address

---

### Post by RgnKjnVA on 2008-01-13
thx TBerben,  the backports have been enabled but still didn't find the update to Audacious. I learned to search for repositories and got it installed. Then I disabled the repo so I wouldn't pick up any other updates.

---

