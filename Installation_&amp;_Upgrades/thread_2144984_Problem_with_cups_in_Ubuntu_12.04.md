---
title: "Problem with cups in Ubuntu 12.04"
date: 2013-05-14
forum: Installation &amp; Upgrades
---

### Post by stormcloud15 on 2013-05-14
I ran ```
sudo apt-get dist upgrade
``` to try to resolve some unmet dependencies. Here is the output of 
```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up cups (1.5.2-9ubuntu1) ...
ln: accessing `/usr/lib/cups/backend-available/ipp14': No such file or directory
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 cups
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
The problem with same error message persists if I try to install or remove any package. Also synaptic is not opening after dist-upgrade. Sorry if I posted it in wrong place. Thanks in advance.

---

### Post by fantab on 2013-05-14
Try:
sudo dpkg --purge cups
sudo apt-get remove --purge cups
sudo apt-get clean
sudo apt-get update

if apt-get update returns NO error then:
sudo apt-get install cups
sudo apt-get dist-upgrade

---

### Post by stormcloud15 on 2013-05-14
Yes. That worked. I had previously tried all command except first one. Thank you

---

### Post by stormcloud15 on 2013-05-14
I'm new to this forum. I couldn't find a way to change the thread tag to [SOLVED].

---

