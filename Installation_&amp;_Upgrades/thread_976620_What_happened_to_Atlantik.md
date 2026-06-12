---
title: "What happened to Atlantik?"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by Johnny K on 2008-11-09
I used the Monopoly-clone Atlantik on Ubuntu 7.04, 7.10, and 8.04. When I upgraded to 8.10, it was uninstalled.

If I try to install it via Synaptic, I get the following error message:
```
atlantik:

Package atlantik has no available version, but exists in the database.
```

If I try to install it via apt, I get this error message:
```
Package atlantik is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package atlantik has no installation candidate

```

Does anybody have any idea why it has gone missing from the repositories?

---

### Post by hansdown on 2008-11-09
There is a download for ubuntu studio.

[http://linux.softpedia.com/progDownload/Atlantik-Download-38292.html](http://linux.softpedia.com/progDownload/Atlantik-Download-38292.html)

Also, try searching synaptic for kdegames.

---

### Post by tubasoldier on 2008-11-09
Kubuntu made the amazing decision to no longer support KDE 3 from Intrepid Ibex on...
Atlantic has not been ported over to KDE 4 as of yet. 
Unfortunate on both accounts.

---

### Post by Johnny K on 2008-11-09
It looks like the package kdegames just depends a bunch of other packages, and atlantik is not one of them.

There's always gtkatlantic, a GTK port of atlantik. Hopefully though, this will push somebody to get back on board in developing atlantik. It was a great piece of software and I'd like to see development continue.

---

