---
title: "Error building dependency tree after upgrade"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by andremmf on 2011-10-17
Hello,

I've just upgraded from 11.04 to 11.10 and i got this problem.
I've created a script to upgrade my system 
```

sudo apt-get update -m
sudo apt-get dist-upgrade -y
sudo apt-get autoclean -y
sudo apt-get autoremove -y
sudo apt-get update -m 

```
And i used it right after the upgrade, rebooted and tried to reinstall gnome with "sudo apt-get install gnome", but it stops on "Building dependency tree...0%" and after a few seconds it returns to terminal command input.
Can someone help me?
Thanks in advance.

---

