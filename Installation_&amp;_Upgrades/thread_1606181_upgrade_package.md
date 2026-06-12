---
title: "upgrade package"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by raunhar on 2010-10-26
Ubuntu Version 10.04
There are certain packages which show marking for upgrade. 
But how do i upgrade them.
I cannot put a mark on them. 
Please help.

---

### Post by alexandari on 2010-10-26
They may be blocked or something...

either way,if you think they are not,run this in the terminal

```
 sudo apt-get update && sudo apt-get upgrade 
```

---

### Post by raunhar on 2010-10-26
Did this.
Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by dino99 on 2010-10-26
the easy way is with synaptic: system admin synaptic, or with update-manager

---

### Post by raunhar on 2010-10-26
How do I login as root.
OR
Can i downgrade the files to the previous version, as the upgraded files have stopped the internet- both wireless and wired. The upgraded files were for network manager

---

