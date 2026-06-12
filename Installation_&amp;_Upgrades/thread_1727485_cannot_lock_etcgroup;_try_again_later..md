---
title: "cannot lock /etc/group; try again later."
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by sandy0594 on 2011-04-12
When i was trying to install Oracle in Ubuntu 10.10..i am getting the below errors,can someone kindly let me know what's the cause of these errors

```


sandy@ubuntu:~$ apt-get install gcc libaio1 libc6 libstdc++5 make lesstif2 lesstif2-dev rpm
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
sandy@ubuntu:~$ groupadd oinstall
groupadd: cannot lock /etc/group; try again later.




```

---

### Post by oldos2er on 2011-04-12
Try ```
sudo apt-get install gcc libaio1 libc6 libstdc++5 make lesstif2 lesstif2-dev rpm
```

When installing packages you need to use sudo to give yourself temporary admin privileges. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

