---
title: "apt-get install openssh-server problems."
date: 2014-05-23
forum: Installation &amp; Upgrades
---

### Post by nick113 on 2014-05-23
Hi, when I do 'sudo apt-get install openssh-server' I get these messages:

sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some requested packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libgl1-mesa-dri-lts-saucy : Depends libglapi-mesa-lts-saucy but it is not going to be installed
 libxcb1 : Depends: libxau6 but it is not going to be installed
           Depends: libxdmcp6 but it is not going to be installed
 openssh-server : Depends: openssh-client (= 1.5.9p1-5ubuntu1)
                  Recommends: xauth but it is not going to be installed
                  Recommends: ssh-import-id but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.



I don't understand what it's trying to tell me.
When I try to install libxau6, libxdmcp6, xauth or openssh-client it tells me they are already installed.

Something is screwed up - how can I get fix it so that openssh-server gets installed?

Thanks in advance

Nick

---

### Post by Ubi_one_2014 on 2014-05-23
pls supply your Ubuntu version
and post the output of:
cat /etc/apt/sources.list

---

### Post by SeijiSensei on 2014-05-23
Try running "sudo apt-get -f install" without any packages and see if that fixes your problems.

---

