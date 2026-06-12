---
title: "how install Openssh-server in ubuntu 15.04 ?"
date: 2018-08-26
forum: Installation &amp; Upgrades
---

### Post by fbio7 on 2018-08-26
Hi 

How do I install the openssh-server in ubuntu 15.04 ? I don't want to upgrade my ubuntu to new versions.

I tried to add the reference [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)  in the source list but it didn't work.

[ATTACH=CONFIG]280861[/ATTACH]

---

### Post by Impavidus on 2018-08-26
Are you really sure you don't want to upgrade (better: fresh install) to a supported release, in particular as you want to install a program that will listen for incoming connections? 15.04 has been dead for years.

If it's just about new versions, 14.04 has a few months of support left.

---

### Post by fbio7 on 2018-08-27
Hi 

Hey impavidus thanks for answering. I have some important files in this machine and I need to get then before any movement.

I finally find a openssh-server file here [https://packages.ubuntu.com/trusty/amd64/openssh-server/download](https://packages.ubuntu.com/trusty/amd64/openssh-server/download). 

I've downloaded it, then I enter at Synaptic and install it after removing some files with this command rm -f /etc/passwd.lock /etc/group.lock /etc/gshadow.lock

---

