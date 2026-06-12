---
title: "libc6, libfreetype6 and libcairo issues"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by eXt on 2006-08-16
Hi all

I'm facing a problem with gtk fonts rendering which is something like [here]("http://forums.debian.net/viewtopic.php?t=7856&sid=9664155c6dffa88f4a47a4ec9bf7e94a").

To solve this I tried to update libcairo but then synaptic has complained that libfreetype6 should be in higher version. libfreetype6 was not available in repos so I took one from packages.debian.org (libfreetype6_2.2.1-2_i386.deb) and.. I tried to install it. Installation raised an error about libc6 version so I downloaded newer libc6 (libc6_2.3.6-15_i386.deb). Installation of libc6 raised an error also :/

Now the problem: synaptic (apt-get in general) complains that I've got 3 broken packages in my system (libc6, libc6-dev, libc6-i686). It is not able to repair broken packages automatically. Command like "apt-get -f install libc6=2.3.6-0ubuntu20 libc6=2.3.6-0ubuntu20" (found [here]("http://www.ubuntuforums.org/archive/index.php/t-186570.html")) fails because of: "libfreetype6: Requires: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is going to be installed.".

How to correct these packages??

---

### Post by zxee on 2006-08-16
I don't know how to resolve the gtk font issue. but maybe the answer to the broken packages is just to remove them and then re-install through apt or synaptic. dpkg -r might be helpful if apt balks.

---

### Post by mlind on 2006-08-16
If you upgraded libc6, you're pretty much knee deep in trouble.
You should reinstall Dapper's libc6 and recompile any packages that depend on higher version.

---

### Post by eXt on 2006-08-17
Thanks for answers. I can't remove libc because it is a base for plenty other packages. I know that I've to reinstall it but I just don't know how - even -f switch doesn't allow me to do that. More hints?

---

### Post by mlind on 2006-08-17
> **eXt said:**
> Thanks for answers. I can't remove libc because it is a base for plenty other packages. I know that I've to reinstall it but I just don't know how - even -f switch doesn't allow me to do that. More hints?

```

sudo aptitude remove libc6

```
Only accept the solution which downgrades libc6.

---

### Post by eXt on 2006-08-18
Thanks a lot!

Aptitude solved libc problem \\:D/ My all fonts also appeared.. don't know why. I think that reenabling antyaliasing helped here. Fonts are smoother and bolder hmm... uglier, but the most important thing is that system is usable again. Thanks!

---

