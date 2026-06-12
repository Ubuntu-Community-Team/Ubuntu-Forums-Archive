---
title: "ubuntu python problem.."
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by junaidsaif on 2011-06-07
hi im saif.
im using ubuntu since 2 months in office..last day i was installing python on his system...by mistake i removed the python files  supporting uubuntu..the system  was not working properly...like the gui and terminal....i had no option but format the entire system..is there any way to get those files rather than formating???im new to ubuntu and want to learn it in depth...thanx in advance..

---

### Post by doas777 on 2011-06-07
well, much of the ubuntu desktop depends on python, so when you remove it, it removes a lot of packages. the best quick answer I can give you is to reinstall the ubuntu-desktop package with this command. it will reinstall python and all the standard applications that come with ubuntu by default. it may copy over some of your config files though, so you may have to reconfigure some settings:

```
sudo apt-get install ubuntu-desktop
```

you can run this from recovery mode if you no longer have a desktop:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

