---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-02-28
forum: Installation &amp; Upgrades
---

### Post by peyman.kafaei on 2017-02-28
Hey guys,

I try to to sudo apt-get upgrade but I constantly get the following message:

```
dpkg: error processing package mount (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 mount
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I cannot do anything and I cannot install anything. Im using 16.04. Can anybody please help me! Thanks a million!

---

### Post by Bashing-om on 2017-02-28
peyman.kafaeil Hello;  Welcome to the forum .

How about trying what the package manager suggest .
in terminal "try" and run:
```

sudo apt update
sudo apt upgrade
sudo apt install --reinstall mount

```

Depending. we do what needs then.

[INDENT][INDENT]If at 1st you do not succeed ---
[INDENT][INDENT][INDENT](sky diving excepted)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

