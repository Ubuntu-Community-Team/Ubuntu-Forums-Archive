---
title: "How to Upgrade from Dapper 6.06 LTS (from May 25th) to Current"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by jrmint on 2006-06-02
hey there:

I upgraded my machine to the Dapper LTS on May 25th  (pre launch edition) and I was wondering if there is a way to migrate from that install to the official release?

update-manager (with or without the -d) do not show any updates available in repositories.

ANy ideas? Is an upgrade necessary?

Thanks

---

### Post by lcg on 2006-06-02
[QUOTE=jrmint]I upgraded my machine to the Dapper LTS on May 25th  (pre launch edition) and I was wondering if there is a way to migrate from that install to the official release?[/QUOTE]
Just open a terminal and execute the following commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

This updates the list of packages first and then installs all the updated packages to give you a current Dapper.

HTH,
Lars

---

