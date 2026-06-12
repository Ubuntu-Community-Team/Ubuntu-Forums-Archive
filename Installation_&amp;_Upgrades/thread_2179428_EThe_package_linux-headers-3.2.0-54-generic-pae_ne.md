---
title: "E:The package linux-headers-3.2.0-54-generic-pae needs to be reinstalled, but I can't"
date: 2013-10-08
forum: Installation &amp; Upgrades
---

### Post by drpjkurian on 2013-10-08
When I open the update manager, I get the following pop up message

```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package linux-headers-3.2.0-54-generic-pae needs to be reinstalled, but I can't find an archive for it.'

```

My release of Ubuntu is as below
Description: Ubuntu 12.04.3 LTS
Release: 12.04

The package information of update manager is as below

Installed: 1:0.156.14.11
  Candidate: 1:0.156.14.11
  Version table:
 *** 1:0.156.14.11 0
        100 /var/lib/dpkg/status

---

### Post by drpjkurian on 2013-10-08
May I Know how to install the package, I downloaded the the package, but not able to install by software centre because it crashes whenever i try installing the package

---

### Post by mörgæs on 2013-10-08
What happens if you close all windows and run

```
sudo apt-get update
sudo apt-get dist-upgrade

```
?

---

### Post by drpjkurian on 2013-10-08
Hi
I will let you know later, For I'm in college right now. Thanks for the reply

---

### Post by drpjkurian on 2013-10-09
Thank you, Thank you!
It solved the issue

I was also asked by the system to try ```
sudo apt-get -f install
```

---

