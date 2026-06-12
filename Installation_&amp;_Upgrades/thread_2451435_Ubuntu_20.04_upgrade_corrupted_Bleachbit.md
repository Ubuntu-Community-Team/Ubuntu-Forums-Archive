---
title: "Ubuntu 20.04 upgrade corrupted Bleachbit"
date: 2020-10-04
forum: Installation &amp; Upgrades
---

### Post by Brother_Dave on 2020-10-04
When I upgraded from Ubuntu 18.04 to 20.04, Bleachbit was run and this error came up:


Error when checking for updates: 
Traceback (most recent call last):
  File "/usr/share/bleachbit/bleachbit/GUI.py", line 1160, in check_online_updates
    updates = Update.check_updates(options.get('check_beta'),
  File "/usr/share/bleachbit/bleachbit/Update.py", line 155, in check_updates
    opener.addheaders = [('User-Agent', user_agent())]
  File "/usr/share/bleachbit/bleachbit/Update.py", line 87, in user_agent
    dist = platform.dist()
AttributeError: module 'platform' has no attribute 'dist'


Then I tried to terminal install Stacer to replace Bleachbit;
but oguzhaninan repository in Turkey is out of business !


What should I do that is easy for a Linux user and not a terminal user?
Fix Bleachbit problem ?
Install Stacer another way ?
Use another simple replacement for Bleachbit ?

---

### Post by monkeybrain20122 on 2020-10-04
Works here (bleachbit 4.0) Remove bleachbit and install the deb from its website [https://www.bleachbit.org/download/linux](https://www.bleachbit.org/download/linux) (get the .deb for 19.10)

---

### Post by Brother_Dave on 2020-10-04
Thanks ! I'll do that if someone here doesn't say how to install Stacer or another better than Bleachbit.

---

### Post by CelticWarrior on 2020-10-04
How to install Stacer? It's in the 20.04 repos...
```
sudo apt install stacer
```

---

### Post by dragonfly41 on 2020-10-04
Or here ..

[https://github.com/oguzhaninan/Stacer](https://github.com/oguzhaninan/Stacer)

---

### Post by Brother_Dave on 2020-10-04
Thanks ! Stacer installed fast in about 10 seconds. Looks good !

---

