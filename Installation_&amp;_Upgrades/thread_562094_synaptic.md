---
title: "synaptic"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by zaden.winkler on 2007-09-28
I downloaded Kubuntu live CD and it does not come with synaptic, So i downloaded it and i can not figure how to get it fully installed. How should I attemp to install it? The notebook I am using has no access to the web so please help me in the Konsole. Thanks much

---

### Post by por100pre1 on 2007-09-29
Adept Manager is a good package manager, IMHO you should give it try.

```
kdesu adept_manager
```

This is KDE's "Add/Remove"

```
kdesu adept_installer
```

Try this for installing Synaptic:

```
sudo aptitude install synaptic
```

---

