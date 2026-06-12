---
title: "How to update openssh 4.7 to 5.5"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by MasterCard on 2010-06-07
I use Ubuntu 8.04 Server 

It uses OPENSSH 4.7 version 
I want to upgrade from OPENSSH 4.7 to OPENSSH 5.5 

According to [https://launchpad.net/ubuntu/+source/openssh](https://launchpad.net/ubuntu/+source/openssh)

Other Ubuntu releases have updated package 

Can I use this one The  Maverick Meerkat OpenSSH                      **5.5p1-4ubuntu1           **

---

### Post by MasterCard on 2010-06-07
**OpenSSH 4.9 - 5.5** has been out for some time but unfortunately wasn't
placed into **Ubuntu 8.04** Hardy Heron.

It has a number of features which would are very interesting and should
improve security. One of the most important features introduced in 5.1
according to my view is the chroot simplification.

OpenSSH now has a chroot option built-in which allows administrators to
simplify their chroot installations a lot if they're only need SSH cli
access and SFTP. This means fewer mis-configurations and improved
overall security.

Basically, introducing a chroot setup with OpenSSH has become as simple
as adding 2-3 lines in the sshd config file.

Since Hardy Heron is supposed to be an LTS version, I'm actually really
surprised that this isn't in Hardy already. This is because the feature
I'm describing here was introduced in **OpenSSH 4.9** and Ubuntu Hardy is
apparently using an even older version.

This gives me some concerns with regards to security in Hardy Heron and
makes me (and my company) wonder if LTS is really the way to go.

---

