---
title: "error when installing libxmlrpc-core-c3-dev"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by emanhossny on 2011-07-01
Hello,
i need to install the package libxmlrpc-core-c3-dev, so i wrote in the command line:
root@ubuntu-desktop:/home/ubuntu/Desktop# apt-get install libxmlrpc-core-c3-dev
& the following message appears:
[COLOR=Navy]Reading package lists... Done
Building dependency tree... 0%

Building dependency tree... Done
Package libxmlrpc-core-c3-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxmlrpc-core-c3-dev has no installation candidate


[COLOR=Black]can anyone help me in installing this package where i'm new to linux.?[/COLOR]

[/COLOR]

---

### Post by Rubi1200 on 2011-07-02
Try running```
 apt-get update
``` and then installing again.

You should also check your sources.list that the appropriate repositories are enabled.

On a side-note, why are you logged in as root?

There is no need to do this since sudo will take care of all your needs:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

