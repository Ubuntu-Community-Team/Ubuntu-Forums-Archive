---
title: "Edgy to Feisty upgrade issue..."
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by vkkim on 2007-05-11
So I click "upgrade" in my upgrade manager, it goes through the "fetching files" routine, then stops with an error message saying,
```
Failed to fetch file:/usr/pluto/deb-cache/./Packages.gz File not found
```

Any ideas?

---

### Post by renzokuken on 2007-05-11
run update first then try again

```
sudo apt-get update
```

---

### Post by vkkim on 2007-05-11
Nevermind, my sources.list was corrupted.  D'oh!

---

