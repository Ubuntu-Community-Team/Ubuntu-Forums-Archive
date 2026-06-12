---
title: "No offer to upgrade Kubuntu 24.04"
date: 2024-08-31
forum: Installation &amp; Upgrades
---

### Post by justsomeguyinslc on 2024-08-31
I am running Kubuntu version 24.04. I'm not getting prompted to upgrade to 24.04.1. I don't want to do a fresh install, I want to update my current installation. I have scoured the internet looking for information, but have found none.

Does anyone know how I can force an upgrade to 24.04.1?

Thank you.

---

### Post by deadflowr on 2024-08-31
It's the same release so there is no offer to upgrade.
A normal software update will bring whatever updates are available and at some point will update the version number.
If the version hasn't already been updated.
Look at what 
```
lsb_release -a
```
shows

---

### Post by justsomeguyinslc on 2024-09-01
Thanks for your post. Still showing version 24.04. I performed many software updates since the new version was released yet it is not downloading the new version.

---

### Post by Bashing-om on 2024-09-01
justsomeguyinslc - Hello

24.04.1 is the newest:
```

sysop@Xm2404:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 24.04.1 LTS
Release:	24.04
Codename:	noble
sysop@Xm2404:~$ 

```

24.10 comes out next month.

[INDENT]hurry up and wait ?
[/INDENT]

---

### Post by deadflowr on 2024-09-01
You missed my point.
It's not a new release.
It's the same release your already using.
24.04 and 24.04.1 (and eventually 24.04.2, 24.04.3, 24.04.4 and 24.04.5) are all the same thing.

All this point release is is the culmination of all the updates that have happened since the initial release.
And the next point release will be a culmination of all the updates that will happen between the release of 24.04.1 and 24.04.2.
And so on.

---

