---
title: "&quot;Upgrade&quot; after upgrade to 11.10"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by hipisan on 2011-10-17
Hello, I upgrade my ubuntu to 11.10 few days ago and today when I open upgrade manager I got again button "Upgrade to 11.10"
What's going on?

---

### Post by zvacet on 2011-10-18
To check witch version do you use run in terminal

```
lsb_release -a
```

If it is 11.10 then try

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hipisan on 2011-10-19
It's 11.04 but wait. Prevously i got 10.10 so maybe upgrade to 11.04 and do not jump to 11.10.

---

### Post by MARP1961 on 2011-10-19
For 'normal' Ubuntu releases you can only go up one version at a time with Distribution Upgrades.

For example: 10.10 to 11.04 **then** 11.04 to 11.10. If you want to upgrade to 11.10 online in this way you need 11.04 first.

With Long Term Support (LTS) relesases you can jump to the next LTS.

For Example: 8.04 to 10.04 **then** 10.04 to 12.04 (when 12.04 arrives next April).

If you want to upgrade directly to your desired version you need to burn a CD or create a bootable USB stick and do a fresh install (much less likely to encounter problems).

---

### Post by zvacet on 2011-10-19
So you have 11.04 right now.if you want to upgrade be sure that your system is up-to-date.

```
sudo apt-get update && sudo apt-get upgrade
```

After that you can upgrade if you want to.

---

