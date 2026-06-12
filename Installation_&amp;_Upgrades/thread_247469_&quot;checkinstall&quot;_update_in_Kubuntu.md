---
title: "&quot;checkinstall&quot; update in Kubuntu"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by srunni on 2006-08-30
Hi,

Adept is showing a package called "checkinstall" that it doesn't select by default for upgrade, even though it's available. It states the status as "upgradable," but the requests "no change." When I select "Request Upgrade," I'm told I have to remove the package "installwatch." As checkinstall's description is "installation tracker" and installwatch's description is "Track installation of local software," I'm guessing they both do the same thing. Does this mean that I should switch to checkinstall, or use installwatch?

Thanks

---

### Post by mlind on 2006-08-30
if you look at checkinstall package description using apt-cache
```

apt-cache show checkinstall | less

```

You'll find out that earlier version depended on installwatch (>> 0.6). New package from backports **Conflicts: installwatch** which means this package must be removed in order to satisfy the install requirements.

---

### Post by srunni on 2006-08-30
Oh, I see. Well then, I guess I'll just upgrade and remove installwatch. Thanks for the apt-cache tip by the way. I'll be sure to look at that the next time I run into a similar problem.

---

