---
title: "help unistalling"
date: 2005-05-28
forum: Installation &amp; Upgrades
---

### Post by belred on 2005-05-28
i made a mistake and let kynaptic upgrade 3 samba client related packages from the backport repository.  i was perfectly happy with the ones out of main.  when i right-clicked on the package to uninstall it, it came up with about 10 kde dependencies it also wanted to uninstall, so i cancelled because i didn't know what would happen.    my question is how do you just uninstall a single package and go back to a previous version or one from the main repository?  the version in the main section shows the backport version, so i'm at a loss.

thanks,

bryan

---

### Post by Xian on 2005-05-28
You'll have to fill in the blanks of course, but this is the command:
```
$ sudo aptitude install <pkgname>=<version>
```

To check which versions are available:
```
$ sudo apt-cache show <pkgname>
```

---

