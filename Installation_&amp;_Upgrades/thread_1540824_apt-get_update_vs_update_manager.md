---
title: "apt-get update vs update manager"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by anandchhetri on 2010-07-28
I used the command sudo apt-get update and then a series of updations were done.  But again when i went to    System>Adminstrator>Update Manager, many updates were available.  On clicking update again a series of updates were done.  
Can anybody explain the difference? As i thought the CLI update was all that was required.

---

### Post by snowpine on 2010-07-28
"sudo apt-get update" contacts the server and refreshes the list of available software. It does **not** download or install any available upgrades.

To do so from the command line (equivalent of running the Update Manager):

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

