---
title: "Running 11.10 - &quot;No Updates to Install&quot; (??)"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by DiagonalArg on 2012-05-30
Update Manager is telling me "No Updates to Install" and has no mention of a distribution upgrade.   When I look under Settings>>Updates, "Notify me of a new Ubuntu version" says, "For any version".  Under  "When there are new updates" it says "Display Immediately".

Does anyone know what to make of this?  I could try via command line "do-distribution-upgrade", but I want to know what's going on.

Thanks all!
DA

---

### Post by zvacet on 2012-05-30
Is your system up-to-date?
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by DiagonalArg on 2012-05-30
Yes.  "No Updates to Install".

What I want to know is why it doesn't tell me that there is a new version of Ubuntu.

---

### Post by zvacet on 2012-06-01
If you don´t have synaptic install it.

```
sudo apt-get install synaptic
```

In synaptic > repositories>updates at the bottom of the page you will see option to upgrade to LTS or to any release.Pick **any** and after that still in synaptic press **refresh** and **mark all updates**.After that in update manager you should see message that new ubuntu release is available.

---

