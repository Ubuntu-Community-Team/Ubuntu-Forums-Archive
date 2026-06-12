---
title: "Compiz -&gt; Compiz-core"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-09-15
At some point over the past weeks, compiz was replaced with compiz-core.  Now I've lost my cube.  I also can't seem to configure the settings with this new compiz-core.

Any easy way to get back to where I was short of rip and replace?

---

### Post by Jay_Bee on 2009-09-15
You did a partial upgrade which removed compiz and compiz-plugins-extra, reinstall compiz again and you're good to go.
BTW don't do the partial upgrade unless the changelog explicitly says that a package X replaces package Y, and Y is to be removed.

---

### Post by mariner09 on 2009-09-15
I certainly didn't intentionally do a partial upgrade.  I've been using synaptic and just telling it to apply the updates.  If I try to install compiz, it gives me an error indicating some dependencies can't be met.

---

### Post by Regenweald on 2009-09-15
> **mariner09 said:**
> I certainly didn't intentionally do a partial upgrade.  I've been using synaptic and just telling it to apply the updates.  If I try to install compiz, it gives me an error indicating some dependencies can't be met.

Better to use
```

sudo aptitude update

```
and 
```

sudo aptitude safe-upgrade

```

---

### Post by Jay_Bee on 2009-09-15
...or use the update-manager, it will always warn you about partial upgrades.
About your problem... you can only wait until necessary dependencies are updated and you are able to install compiz again.

---

