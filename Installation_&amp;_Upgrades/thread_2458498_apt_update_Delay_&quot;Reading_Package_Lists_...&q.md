---
title: "apt update Delay &quot;Reading Package Lists ...&quot;"
date: 2021-02-25
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2021-02-25
I've noticed on one of my computers when I run ```
apt update
``` the command runs normally, updating the package lists but when it has finished downloading the lists and gets to the ```
Reading Package Lists ...
``` There is a significant delay. It seems to stall at 97% take two minutes or more to complete. I wonder if there is something going on that shouldn't be. 
Looking at System Monitor nothing much seems to be going on.

---

### Post by dino99 on 2021-02-27
How much free space is available ? Do you use a swap directory or partition ? Maybe you should clean the system via autoclean/autoremove too.

---

### Post by rsteinmetz70112 on 2021-02-28
I ran autoclean and autoremove, in fact I usually run them after every upgrade.

```
~# swapon
NAME                TYPE SIZE USED PRIO
/var/swap/swap.file file  32G   0B   -1
```


```
#df
/dev/mapper/hamlet-root   144366248  93847664   43162168  69% /

```

I don't think space is a problem.
I suspect it's something in the dpkg database but I don't know how to find it.

---

