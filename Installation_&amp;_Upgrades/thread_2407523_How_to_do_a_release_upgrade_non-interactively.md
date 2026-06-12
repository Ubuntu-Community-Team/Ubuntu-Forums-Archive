---
title: "How to do a release upgrade non-interactively?"
date: 2018-12-05
forum: Installation &amp; Upgrades
---

### Post by godatum2 on 2018-12-05
Am trying up upgrade 14.04 to 16.04 with the command ```
sudo do-release-upgrade -f DistUpgradeViewNonInteractive
```

But it still gives me prompts for updating certain /etc/ files. Tried this but fails as it doesn't accept some of the prompts ```
sudo sh -c 'echo "yN\yN\yes\yes\nN\yes\nN\nN\nN\nN\nN\nN\nN\N\yN\yN" | DEBIAN_FRONTEND=noninteractive /usr/bin/do-release-upgrade -f DistUpgradeViewNonInteractive'
```

---

### Post by Frogs Hair on 2018-12-05
_May_ be related.

[https://ubuntuforums.org/showthread.php?t=2265877](https://ubuntuforums.org/showthread.php?t=2265877)

---

### Post by Autodave on 2018-12-05
I cannot answer your question....sorry.  But I can tell you that upgrading from one release to another seldom works without problems.  You are usually better served by backing up anything that you need to keep and doing a clean install.  18.04 is out now and if you were to install that, you would be good for at least 5 more years.

---

### Post by Frogs Hair on 2018-12-05
> **Autodave said:**
> I cannot answer your question....sorry.  But I can tell you that upgrading from one release to another seldom works without problems.  You are usually better served by backing up anything that you need to keep and doing a clean install.  18.04 is out now and if you were to install that, you would be good for at least 5 more years.

Great advice if you have the option.

---

### Post by godatum2 on 2018-12-07
> **Frogs Hair said:**
> _May_ be related.

[https://ubuntuforums.org/showthread.php?t=2265877](https://ubuntuforums.org/showthread.php?t=2265877)

Thanks, yes adding those lines worked.

---

