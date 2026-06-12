---
title: "Cannot install openssh-server on 18.04"
date: 2018-12-11
forum: Installation &amp; Upgrades
---

### Post by sdonkney on 2018-12-11
Hi,
I am trying to install openssh-server through Synaptic. Synaptic wants to uninstall a large set of packages, almost everything that I have installed after OS Installation, which looked quite odd (and unsettling).
The output of *apt-get -s install openssh-server* is
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:7.6p1-4)
                  Depends: openssh-sftp-server but it is not going to be installed
                  Recommends: ssh-import-id but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
I have* openssh-client 1:7.6p1-4ubuntu0.1* installed.
I have absolutely no clue how to proceed. Any help would be appreciated.

---

### Post by sdonkney on 2018-12-11
I got the solution to this problem from the Ubuntu IRC channel. I had the *bionic-updates* and *security* repos disabled. Enabled these, and it worked fine.

---

