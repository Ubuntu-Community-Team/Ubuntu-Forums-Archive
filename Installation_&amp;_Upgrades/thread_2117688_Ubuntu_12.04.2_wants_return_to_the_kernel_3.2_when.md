---
title: "Ubuntu 12.04.2 wants return to the kernel 3.2 when system upgrade"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by allan_sundry on 2013-02-19
Hi

Upgraded from 12.04.1 to 12.04.2 and installed LTSEnablementStack:
```

sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal 

```
All have excellent:
```

Linux ibiza 3.5.0-24-generic #37~precise1-Ubuntu SMP Thu Feb 7 13:50:53 UTC 2013 i686 i686 i386 GNU/Linux

```
Now when you update your system has come back to the old kernel:
```

$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

``````

$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic-pae linux-image-3.2.0-38-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
3 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 50,9 MB of archives.
After this operation, 181 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

How can I fix it?

---

### Post by allan_sundry on 2013-02-19
Issue has been resolved that the removal of all concerned kernel 3.2 from the system.

---

### Post by fuorviatos on 2013-02-19
Nothing really weird. Have a look [here]("http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade") for the explanation.

---

