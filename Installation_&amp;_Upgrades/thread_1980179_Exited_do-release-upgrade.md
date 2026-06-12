---
title: "Exited do-release-upgrade"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by mrjonny2 on 2012-05-14
I accidentally exited do-release-upgrade using cmd+c.  It was in the middle of doing a MySQL upgrade and it was asking me about what it wanted to do with the my.cnf file  any suggestions?
Really need help with this ASAP

this is what I know is going on at the moment
```
jonny_flowers@pickles10:~$ ps aux | grep update
root     13890  0.0  0.8 147312 71656 ?        S    22:46   0:00 /usr/bin/python /tmp/update-manager-nFjl_2/precise --mode=server --frontend=DistUpgradeViewText
1000     25235  0.0  0.0   9372   884 pts/0    S+   23:12   0:00 grep --color=auto update
```

---

### Post by Gforce20 on 2012-05-15
Hah, no kidding. This just happened to me as well and I found this thread via Google. I'll let you know if I find a solution.

---

### Post by Gforce20 on 2012-05-15
Well, this might not work for you, but running
```
export DISPLAY=:0
unity
```
in a Ctrl-Alt-F* terminal brought the window back for me. Turns out the do-release-upgrade window wasn't actually closed -- Unity just crashed for whatever reason.

---

