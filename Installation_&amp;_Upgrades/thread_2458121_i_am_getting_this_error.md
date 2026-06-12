---
title: "i am getting this error"
date: 2021-02-16
forum: Installation &amp; Upgrades
---

### Post by ritvikop on 2021-02-16
sudo apt-get install openjdk-8-jre
[sudo] password for ritvik:    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 openjdk-8-jre : Depends: openjdk-8-jre-headless (= 8u282-b08-0ubuntu1~18.04) but it is not going to be installed
 ulauncher : Depends: python3-pyinotify but it is not going to be installed
             Depends: libkeybinder-3.0-0 but it is not going to be installed
             Depends: gir1.2-keybinder-3.0 (>= 0.3) but it is not going to be installed
             Depends: gir1.2-appindicator3-0.1 but it is not going to be installed
             Depends: python3-distutils-extra but it is not going to be installed
             Depends: python3-levenshtein but it is not going to be installed
             Depends: python3-websocket but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by CelticWarrior on 2021-02-16
```
[COLOR=#000000]You might want to run 'apt --fix-broken install' to correct these.[/COLOR]

```

---

### Post by ritvikop on 2021-02-16
ok it worked

---

