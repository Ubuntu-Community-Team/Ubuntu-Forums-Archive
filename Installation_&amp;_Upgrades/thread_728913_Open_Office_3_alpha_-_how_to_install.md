---
title: "Open Office 3 alpha - how to install?"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by meuge on 2008-03-19
With the release of the OO 3.0 alpha, that finally has definable error bars, can someone please tell me how to install the thing. 

I would ideally like to install it separately, without overwriting OO 2.X

I have downloaded the .deb files, but when I try to install them normally, I get a message saying that the version I have is higher, and it will nto be installed. 

Much thanks will be given to any tips.

---

### Post by dcroxton on 2008-03-19
I just went into the directory with the debs and did 

```
sudo dpkg -i *
```

which worked fine.  The packages had different names from the OOo packages in Ubuntu, so I have them both working.  The packages were called something like "ooo-dev-*".

---

### Post by centurian on 2008-05-07
This guide worked for me... You can run different versions of OO in parallel

[http://wiki.services.openoffice.org/wiki/Run_OOo_versions_parallel](http://wiki.services.openoffice.org/wiki/Run_OOo_versions_parallel)

---

### Post by justin whitaker on 2008-05-07
The Beta is out today...might want to grab the .deb for that instead. Just saying....:)

---

### Post by meuge on 2008-05-12
> **justin whitaker said:**
> The Beta is out today...might want to grab the .deb for that instead. Just saying....:)
I know. I've been using the alpha and they've been working (almost) fine. Hopefully the beta has ironed out those bugs. 

Error bars were a deal-breaker for me... so now I am satisfied with using OO for work.

---

