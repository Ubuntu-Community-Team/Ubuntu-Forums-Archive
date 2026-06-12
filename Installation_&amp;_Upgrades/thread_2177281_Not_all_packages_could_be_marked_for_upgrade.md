---
title: "Not all packages could be marked for upgrade"
date: 2013-09-28
forum: Installation &amp; Upgrades
---

### Post by oygle on 2013-09-28
The software update dialog states "Not all packages could be marked for upgrade. The available upgrades may require new packages to be installed or removed. Do you want to mark upgrades that may require the installation or removal of additional packages?"

Is there a command to repair this, or is it broken packages or something ?

Oygle

---

### Post by oygle on 2013-09-28
Found a solution at post [#2]("http://ubuntuforums.org/showthread.php?t=1976267&p=11917680#post11917680")

Ran these 2 commands

```

sudo apt-get update 
sudo apt-get upgrade
```

but the Update manager was still wanting to add the Linux archive files, so ran this

```
sudo apt-get dist-upgrade
```

as there was a kernel held back.

---

