---
title: "openssh-server broken packages"
date: 2016-01-16
forum: Installation &amp; Upgrades
---

### Post by peteraaser on 2016-01-16
Hi. When trying to install openssh-server on my ubuntu 15.04 installation I get the following:

sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:6.7p1-5ubuntu1)
                  Depends: openssh-sftp-server but it is not going to be installed
                  Recommends: ssh-import-id but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

I have tried apt-get install -f, update, upgrade, dist-upgdrade but the issue remains.
When trying to remove openssh-client I get:

sudo apt-get remove openssh-client 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libboost1.55-dev : Depends: libstdc++-4.8-dev but it is not going to be installed or
                             libstdc++-dev
 libc6 : Depends: libgcc1 but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


When using synaptic no broken packages are shown in the sidebar. If I try to install openssh-server in synaptic I get the following rather drastic measure [http://imgur.com/a/5XGfi](http://imgur.com/a/5XGfi)

---

### Post by ian-weisser on 2016-01-16
Warning: 15.04 will EOL in 2.5 weeks on February 4, 2016

openssh-client 1:6.7p1-5ubuntu1 is from the original vivid repository, not vivid-secuirty or vivid-updates. Do you have those repositories enabled? (Tip: you should!)

The "you have requested an impossible situation" error message often indicates a version conflict, usually introduced by non-Ubuntu software sources. Have you installed any software using command-line voodoo from some website? If so, what? A link to the instructions would be helpful.

Can you tell us what kinds of installs or maintenance you were doing right before you started getting these messages?

---

### Post by peteraaser on 2016-01-19
Hi, apart from installing ROS I cant think of anything. Havent run any mysterious install scripts as far as I can remember. I think I'll just cut my losses and do a fresh install of 15.10 since there doesnt seem to be an easy fix, and this is all a little over my head.

---

