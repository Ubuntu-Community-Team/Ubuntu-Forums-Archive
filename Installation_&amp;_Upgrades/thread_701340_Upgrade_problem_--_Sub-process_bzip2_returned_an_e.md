---
title: "Upgrade problem -- Sub-process bzip2 returned an error code (2)"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by kerristallax on 2008-02-19
I have been trying to update from 7.04 to 7.10 (Kubuntu) on my Dell E1505 recently, and when I run Adept Manager -> Version Upgrade, it goes for a while and then stops with these errors:

```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)

Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
```

Originally, there were some other errors in the process, but I got rid of those by unchecking everything but offical Canonical-supported packages in the "Manage Repositories" and "Software Sources" section.

---

### Post by kerristallax on 2008-02-28
It seems that this is a rare problem, but I was able to get it to stop appearing by deselecting all but the Canonical-supported software, and changing the download server from "United States" to "Main Server."  I am backing up my personal files and will upgrade in the near future if all goes well -- wish me luck!

This is on my Dell e1505, so hopefully I will not have post-upgrade hardware issues.  Wish me luck!

---

