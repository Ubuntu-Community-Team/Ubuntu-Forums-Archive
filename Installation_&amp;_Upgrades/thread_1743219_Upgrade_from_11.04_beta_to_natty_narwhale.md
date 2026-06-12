---
title: "Upgrade from 11.04 beta to natty narwhale"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Thebear on 2011-04-29
installed 11.04 beta about 3 weeks ago(or maybe it was beta 2, not sure how to tell) with no problems other than my machine would not run unity.  MY computer is a Asus 1201HA netbook. No doubt the GMA 500 graphics card will not run unity ever. But I am okay with that. However, now I can't seem to upgrade to the current version.  Upgrade manager suggests a partial upgrade but it cannot find the majority of the packages and aborts the upgrade.  Is anyone else experiencing this problem.

---

### Post by mörgæs on 2011-04-29
Never do a partial upgrade. 

Just apply all normal updates, and you will get to the final version. There might be some delay in downloading right now, as the servers are heavily loaded.

---

### Post by Thebear on 2011-05-01
thanks for the advice, but I dont see where I am offered a choice. The partial upgrade seems to be the only option

---

### Post by mörgæs on 2011-05-01
What happens if you boot the machine and run
```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```?

---

### Post by Thebear on 2011-05-01
thanks those commands seem to solve my problem,

---

### Post by mörgæs on 2011-05-01
Good, please mark the thread 'solved'.

---

