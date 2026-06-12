---
title: "apt-get update"
date: 2020-07-27
forum: Installation &amp; Upgrades
---

### Post by amedix on 2020-07-27
Hi,

I the company where I work we have an old ubuntu installed (Ubuntu 10.04.4 LTS)

When I try to upgrade the package **openssl **it outputs:

*Reading package lists... Done*
*Building dependency tree       *
[I]Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/I]
So, I tried to update the OS with **apt-get update** I have this error message :

* gnutls_handshake() failed: A TLS fatal alert has been received.*
*Err [https://deb.nodesource.com](https://deb.nodesource.com) lucid/main Sources*
[I]  gnutls_handshake() failed: A TLS fatal alert has been received.

Any idea ?[/I]

---

### Post by coffeecat on 2020-07-27
Welcome to the forum.

Ubuntu 10.04 is so obsolete (released over 10 years ago, and out of support for over 5 years) that it would not be productive trying to troubleshoot this. If you want to install a supported release of Ubuntu on the old or newer equipment and need help with this, you are very welcome to start another thread. If you have any particular software needs, please describe these in any new thread.

Good luck.

---

### Post by ActionParsnip on 2020-07-27
What is the output of:
```

lsb_release -a
uname -a
sudo grep -R lucid /etc/apt/*

```

---

### Post by grahammechanical on 2020-07-28
For your information the software sources or repositories of Ubuntu 10.04 have been moved ever since 10.04 reached end of life. So, it is impossible to update any software package because the address of the repositories is now incorrect. But they can be changed.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Note the section on upgrading the sources.list file. You find the sources.list file at /etc/apt/ Look in the folders in the etc directory. You edit the file using Gedit.

---

