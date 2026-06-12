---
title: "Major Kubuntu Alpha 6 fail"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilicuus on 2009-09-26
I just installed the Kubuntu Alpha 6 and updated it with KPackageKit, and now have a really annoying problem...... it doesn't start X on boot! It just goes straight to the console, and I have to login and use startx to get it going! :(

---

### Post by taavikko on 2009-09-26
> **ilicuus said:**
> I just installed the Kubuntu Alpha 6 and updated it with KPackageKit, and now have a really annoying problem...... it doesn't start X on boot! It just goes straight to the console, and I have to login and use startx to get it going! :(

[https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/434361](https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/434361)

---

### Post by koso on 2009-09-26
Its bug caused by KDM transition to upstart: [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/437067](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/437067) 

You can wait for fix, or try workaround from here: [http://kubuntuforums.net/forums/index.php?topic=3106656.0](http://kubuntuforums.net/forums/index.php?topic=3106656.0)

---

### Post by taavikko on 2009-09-26
> **koso said:**
> Its bug caused by KDM transition to upstart: [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/437067](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/437067) 

You can wait for fix, or try workaround from here: [http://kubuntuforums.net/forums/index.php?topic=3106656.0](http://kubuntuforums.net/forums/index.php?topic=3106656.0)

thanks for that, simple typo in config file, classic :)

---

### Post by ilicuus on 2009-09-26
> **taavikko said:**
> thanks for that, simple typo in config file, classic :)

A typo? Don't they test the updates before releasing them?

---

### Post by buzzmandt on 2009-09-26
just tried daily build from yesterday (25th), had no issues.

---

