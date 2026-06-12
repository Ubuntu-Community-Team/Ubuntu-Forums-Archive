---
title: "update manager keeps installing the same update"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by mpolito1969 on 2008-10-29
This is not the first time I notice it. Update manager is telling me I should install "linux-headers-2.6.24-21-generic" and some other "*-2.6.24-21-*" stuff but I'm sure I have already installed it a couple of weeks ago.

Have a look:

```


max@laptop:/usr/src$ ll
total 24
drwxrwsr-x  6 root src  4096 2008-10-15 22:32 ./
drwxr-xr-x 11 root root 4096 2008-07-02 12:18 ../
drwxr-xr-x 20 root root 4096 2008-09-09 22:46 linux-headers-2.6.24-19/
drwxr-xr-x  6 root root 4096 2008-09-09 22:46 linux-headers-2.6.24-19-generic/
drwxr-xr-x 20 root root 4096 2008-10-15 22:32 linux-headers-2.6.24-21/
drwxr-xr-x  6 root root 4096 2008-10-15 22:32 linux-headers-2.6.24-21-generic/


```

They are already there.

What's wrong with my update manager? Is there anything I can do to fix this problem?

Ciao,
Max

---

### Post by Pumalite on 2008-10-29
It's normal. It upgrades itself.

---

### Post by robert shearer on 2008-10-29
It's normal.
Open update manager, highlight one of the packages and read the 'Changes and Descriptions' tabs at the bottom.

You will see that the suffix has changed  -42 to -43 or something similar.

Check by opening Synaptic and searching for 'linux image'.
Note the  highest number version.
Something like "linux-image-2.6.24-21-generic 2.6.24-21.42"

then do the update and look again and it will be..
linux-image-2.6.24-21-generic 2.6.24-21.43

---

