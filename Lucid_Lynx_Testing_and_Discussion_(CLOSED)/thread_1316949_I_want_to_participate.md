---
title: "I want to participate"
date: 2009-11-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by YosefKaro on 2009-11-06
I have a laptop that I can use for testing purposes and I followed the steps outlined in the thread "How to upgrade Karmic to Lucid" [http://ubuntuforums.org/showthread.php?t=1304585](http://ubuntuforums.org/showthread.php?t=1304585) and it appeared to do the upgrade however, it still looks like Karmic to me. If I do uname -a I get: Linux yos-laptop 2.6.32-2-generic #2-Ubuntu SMP Sat Oct 31 17:07:12 UTC 2009 i686 GNU/Linux  So, am I on Lucid yet or not?  If not, please let me know what more I need to do.

-Yos

---

### Post by whoop on 2009-11-06
> **YosefKaro said:**
> I have a laptop that I can use for testing purposes and I followed the steps outlined in the thread "How to upgrade Karmic to Lucid" [http://ubuntuforums.org/showthread.php?t=1304585](http://ubuntuforums.org/showthread.php?t=1304585) and it appeared to do the upgrade however, it still looks like Karmic to me. If I do uname -a I get: Linux yos-laptop 2.6.32-2-generic #2-Ubuntu SMP Sat Oct 31 17:07:12 UTC 2009 i686 GNU/Linux  So, am I on Lucid yet or not?  If not, please let me know what more I need to do.

-Yos

There are not much changes yet, let alone visual ones.
Do this in terminal to make sure:
```

cat /etc/issue

```

It should say lucid there.

---

### Post by philinux on 2009-11-06
> **YosefKaro said:**
> I have a laptop that I can use for testing purposes and I followed the steps outlined in the thread "How to upgrade Karmic to Lucid" [http://ubuntuforums.org/showthread.php?t=1304585](http://ubuntuforums.org/showthread.php?t=1304585) and it appeared to do the upgrade however, it still looks like Karmic to me. If I do uname -a I get: Linux yos-laptop 2.6.32-2-generic #2-Ubuntu SMP Sat Oct 31 17:07:12 UTC 2009 i686 GNU/Linux  So, am I on Lucid yet or not?  If not, please let me know what more I need to do.

-Yos

2.6.32.2 is lucid.

Have you got a launchpad account for reporting bugs.

I would recommend reading the sticky posts.

---

### Post by YosefKaro on 2009-11-06
Thank you very much:  Ubuntu lucid (development branch) \n \l  :p

-Yos

---

### Post by YosefKaro on 2009-11-06
Yes, I already have a launchpad account and I have already reported a few bugs on Karmic when I used it on wubi...one of which was confirmed and will appear as an update in the near future (I hope).  ;)

-Yos

---

### Post by VMC on 2009-11-06
what does '/etc/lsb-release' show. Here's mine:

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu lucid (development branch)"

---

### Post by YosefKaro on 2009-11-06
Ditto  :D

-Yos

---

