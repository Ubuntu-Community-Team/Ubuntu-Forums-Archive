---
title: "list of debian packages available in ubuntu?"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by malarky on 2007-01-04
I'm trying to get proftpd on my ubuntu server LAMP box using the way described in a few howto's i've seen:

```
sudo apt-get install proftpd
```

And I'm getting the error:

```
E: Couldn't find package proftpd
```

apt-get has worked fine all day and i've pulled down a load of packages with no trouble. What am I doing wrong? Is it just the package name? Is there a way to get apt-get to list packages by partial name? Fink on OS X does this I think.

Thanks,
s

---

### Post by meng on 2007-01-04
Enable universe repositories!!!
If you want to look for packages, you can use Synaptic to search for packages in your enabled repos.
Another way is to search [packages.ubuntu.com]("http://packages.ubuntu.com")

---

### Post by 23meg on 2007-01-04
Make sure [the Universe repository is enabled]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html").

---

### Post by malarky on 2007-01-04
Thanks, should have used the wiki. Found what i needed here:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

