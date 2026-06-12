---
title: "can you upgrade 12.04 to 14.4.1"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by rhendrix9 on 2014-08-03
I have 12.04 lts newly installed nothing important or that i mind loosing
It's in virtual machine.
i could just blow it away and start clean, but i thought i'd upgrade.
I did;

sudo apt-get update
.
.
.
Fetched 155 kB in 2s (61.3 kB/s)
Reading package lists... Done

then;
user@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@ubuntu:~$ 

It doesn't look like it works.
Am I missing something?

---

### Post by Bucky Ball on 2014-08-03
dist-upgrade doesn't. It's not used for that. There have been issues with 14.04.1 release which may or may not effect you so perhaps best to stick where you are for the moment. Anyhow, the command you are looking for is:

```
sudo do-release-upgrade
```

... from memory.

---

