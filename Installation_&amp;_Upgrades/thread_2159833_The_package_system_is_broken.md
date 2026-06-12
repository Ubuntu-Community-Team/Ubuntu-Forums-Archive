---
title: "The package system is broken"
date: 2013-07-04
forum: Installation &amp; Upgrades
---

### Post by shubham822 on 2013-07-04
Every time I update I get this error, Software Center also doesn't work. 

[ATTACH=CONFIG]244403[/ATTACH]

And this one in the notification bar every time I boot.
[ATTACH=CONFIG]244404[/ATTACH]

Any help will be appreciated!
THANKS IN ADVANCE!:KS

---

### Post by shubham822 on 2013-07-04
A partial upgrade from update manager seems to have fixed the problem!

---

### Post by deadflowr on 2013-07-04
Yep, though partial upgrades are normally to be avoided, if you use due diligence and investigate why a partial is offered, you can figure out if it will be a big issue or not.
Even though this is for +1(the development cycle) it does lend good advice on partial upgrades for any release.
[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)

---

### Post by grahammechanical on 2013-07-04
Just for the curious among us, did you follow the advice to run

```
sudo apt-get install -f
```

that command is supposed to fix broken dependency problems.

regards.

---

