---
title: "issue upgrading from 12.04 to 14.04 and the same only for php 5.3 to 5.4"
date: 2015-11-23
forum: Installation &amp; Upgrades
---

### Post by giuliano3 on 2015-11-23
after doing 
sudo apt-get update && sudo apt-get dist-upgrade
i received this message:

E: Could not perform immediate configuration of "python-minimal" For more information, see "man 5 apt.conf" to the "APT :: Immediate-Configure" (2).

after long google-ing i didn't found any functioning solution.

thanks
Giuliano

---

### Post by Bashing-om on 2015-11-23
giuliano3; Hello; Welcome to the forum .

Please show the complete outputs - Between Code Tags - of the terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
so we have the error in contect.

Then let us suppose we have a source conflict with python.
show:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
 to verify the sources.

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]so a tale is told
[/INDENT][/INDENT]

---

