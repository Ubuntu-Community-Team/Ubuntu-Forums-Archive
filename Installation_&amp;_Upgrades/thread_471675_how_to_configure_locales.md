---
title: "how to configure locales?"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by crixtiano on 2007-06-12
Hi, 

Im running a Feisty version 64 bits and I'm trying to install a 32bit version with chroot.

I'm following this tutorial: [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

but, when I try to do "dpkg-reconfigure locales" an error is generated:

> root@pardal:/# dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "pt_BR:pt:en",
        LC_ALL = (unset),
        LANG = "pt_BR.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory


Please, what s going on ? And , how to fix this error?

Thank you

Cristiano

---

### Post by zvacet on 2007-06-12
**system<administration<language support>download locale** Did you do that?

---

