---
title: "missing modules for kernel 3.2.0-24-generic"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by veilig on 2012-05-03
I just upgraded from 11.10 to 12.04, everything seemed to go ok, I finished and everything was fine, then after a reboot all hell broke loose.

I can't boot into my 3.2.0-24-generic kernel, all it does is load up to the login screen and then I loose control of my mouse and keyboard (they won't move or type).

I have to boot into a previous kernel for anything to work.

I tried running some updates to my system, but I was getting an error

```
FATAL: Could not load /lib/modules/3.2.0-24-generic/modules.dep: Not a directory
```
So I checked out the ```
/lib/modules
``` directory to see whats going on

```
&#9492;&#9472;(23:24:%)&#9472;&#9472; ls -la                                           &#9472;&#9472;(Thu,May03)&#9472;&#9496;
total 28
drwxr-xr-x  5 root       root        4096 May  2 23:51 ./
drwxr-xr-x 27 root       root       12288 May  3 23:22 ../
drwxr-xr-x  5 root       root        4096 May  3 00:26 2.6.31-22-generic/
drwxr-xr-x  5 root       root        4096 Jan 19 12:52 2.6.32-28-generic/
drwxr-xr-x  5 root       root        4096 May  3 23:01 2.6.38-13-generic/
c-wS-w---x  1 1744863507 161358036 172, 0 May  6  1927 3.2.0-24-generic
```
WHOA, what in the world happened to my 3.2.0-24 kernel? I don't know

any one know what I can do to fix this?

---

### Post by carl4926 on 2012-05-04
You should still be able to boot the previous kernel.
Try forcing the -24 kernel to install again

---

### Post by veilig on 2012-05-04
How do I force that?

---

### Post by carl4926 on 2012-05-04
Install synaptic
find the package
right click > mark for reinstallation
apply

---

### Post by veilig on 2012-05-05
unfortunately it didn't work.

---

### Post by veilig on 2012-05-05
Sorry, spoke to soon - I missed the correct one to install, it did work!

Thanks for your help!

---

### Post by carl4926 on 2012-05-05
> **veilig said:**
> Sorry, spoke to soon - I missed the correct one to install, it did work!

Thanks for your help!
Excellent news

---

