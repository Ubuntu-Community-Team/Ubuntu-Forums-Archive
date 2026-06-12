---
title: "Update Error"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by danharris83 on 2011-04-08
HI when i try to update using terminal and update manager i get this error

/usr/bin/dpkg: 1: Syntax error: "&" unexpected
E: Sub-process /usr/bin/dpkg returned an error code (2)

hope someone can help.

thanks dan harris

---

### Post by Dutch70 on 2011-04-08
Try running these commands and see if that fixes it.
```
dpkg --clean-avail
```
and then...
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by danharris83 on 2011-04-08
when running ```
dkpg --clean-avail
```i get this 

bash: /usr/bin/dpkg: cannot execute binary file

edit: When doing a partial upgrade with update manager i get this error if it helps

Traceback (most recent call last):

  File "/usr/bin/update-manager", line 101, in <module>
    controler = DistUpgradeController(view, datadir=data_dir)

  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeController.py", line 126, in __init__
    self.quirks = DistUpgradeQuirks(self, self.config)

  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeQuirks.py", line 53, in __init__
    self.arch = Popen(["dpkg", "--print-architecture"], stdout=PIPE).communicate()[0]

  File "/usr/lib/python2.6/subprocess.py", line 633, in __init__
    errread, errwrite)

  File "/usr/lib/python2.6/subprocess.py", line 1139, in _execute_child
    raise child_exception

OSError: [Errno 8] Exec format error

---

### Post by Dutch70 on 2011-04-08
It's dpkg, as in debian package, not dkpg.

---

### Post by danharris83 on 2011-04-08
sorry that was just a typo still get the same error it happens when ever i try to install anything from the Ubuntu Sofware Centre

---

### Post by Dutch70 on 2011-04-08
Have you recently added RAM? 

Try these 2 commands, and that's about all I really know to try.
```
sudo dpkg install -f
```
```
sudo apt-get --configure -a
```

---

### Post by danharris83 on 2011-04-08
Thanks  for the reply I not added anything not sure wats happened I will try that when I get home tonight

---

### Post by danharris83 on 2011-04-08
I tried both of them still get the same error

/usr/bin/dpkg: 1: Syntax error: "&" unexpected

---

