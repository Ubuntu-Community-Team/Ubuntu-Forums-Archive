---
title: "my old computer is not PAE(Physical Address Extension ) and I have Windows XP"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by spi_ on 2013-05-01
hello, my old computer is not PAE(Physical Address Extension ) and I have Windows XP, is possible to make USB with persistent mode in new version lubuntu?

---

### Post by sudodus on 2013-05-01
It depends ...

If it is a Pentium M CPU, it actually has pae capability, but is not announcing it (no pae flag). Right now I'm testing a special version of Lubuntu Raring (13.04), that works with Pentium M CPUs.

But if it is another (very old) cpu without pae, it really is without it, and the last version of Ubuntu that works is 12.04 LTS. To be more accurate, Xubuntu 12.04 LTS is supported until April 2015. Lubuntu is actually the best flavour for old computers (lightest foot-print), but 12.04 is unfortunately supported only until October 2013.

---

### Post by MAFoElffen on 2013-05-01
Then there's another branch that has non-pae kernel in Raring and will also continue that support in the future... Puppy. Right now that is Upup Raring 3.8.7 with non-PAE 3.8.7 kernel. You could always use that kernel "back-up" on lubuntu or xubuntu 12.04 non-PAE, pin it... then release upgrade to 13.04... retaining that kernel (theoretical/untested)? Thinking pinning works... but I don't know how pinning's behavior work's during a do-release-upgrade.

---

### Post by 2F4U on 2013-05-01
I also own two machines that do not have PAE. However, there are some Linux  distributions which still support such old hardware. Among them are  Bodhi Linux (based on Ubuntu 12.04, look for the non-pae install image), openSUSE, Archlinux, Archbang  (based on Archlinux). I am using Archbang on my machines because it is  very light, but since it is based on Arch and being rolling release it  is certainly not for everyone.

---

### Post by MAFoElffen on 2013-05-01
@2F4U-
LOL... Yes- One of my test servers is an HP LP1000R with dual Pentium III processors that I keep saying I'm going to retire... but it just keeps doing it's job.

---

### Post by Redalien0304 on 2013-05-01
> **sudodus said:**
> It depends ...

If it is a Pentium M CPU, it actually has pae capability, but is not announcing it (no pae flag). Right now I'm testing a special version of Lubuntu Raring (13.04), that works with Pentium M CPUs.

But if it is another (very old) cpu without pae, it really is without it, and the last version of Ubuntu that works is 12.04 LTS. To be more accurate, Xubuntu 12.04 LTS is supported until April 2015. Lubuntu is actually the best flavour for old computers (lightest foot-print), but 12.04 is unfortunately supported only until October 2013.

Very cool sudodus can we get a link maybe? or more info?  i would interested in testing it on  my Dell latitude d600 2gb ram Pentium M (non-pae).

---

### Post by mörgæs on 2013-05-01
> **MAFoElffen said:**
> ...One of my test servers is an HP LP1000R with dual Pentium III processors...

Then there's no PAE problem. All Pentium 3 and 4 have PAE.

---

### Post by sudodus on 2013-05-13
[SIZE=6]Lubuntu-fake-PAE[/SIZE]

Hello all Pentium M users,

Please visit the preliminary wiki page  [https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)   and tell me what you think.

---

