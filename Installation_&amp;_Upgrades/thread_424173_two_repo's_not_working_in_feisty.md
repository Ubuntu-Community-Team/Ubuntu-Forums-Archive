---
title: "two repo's not working in feisty"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by JReagan1990 on 2007-04-26
every time I try to install an application, I get this error while reloading the application list.  

The error I get is:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

---

### Post by zvacet on 2007-04-26
It seems they are no longe available.Try with diferent server(software properties) or replace source list.Before you do that try 
```
sudo aptitude update
```

---

### Post by JReagan1990 on 2007-04-26
Thanks! :)

---

### Post by TheCleaner on 2007-04-27
Just FYI, I had the same problem and went into Synaptic Package Manager under "Repositories" and changed the server source from "United States" to main, and then everything worked ok.

---

