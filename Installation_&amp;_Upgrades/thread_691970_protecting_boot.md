---
title: "protecting /boot"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by FunkyRes on 2008-02-09
Howdy - I'm a CentOS user and have been a Red Hat based distro user since RH 5.1

I'd like to give Ubuntu a shot and play with it, but there's this nasty rumor going around that the Ubuntu installer insists upon wiping /boot - a rather rude thing for it to do. Is this the case?

I'd really prefer to throw the ubuntu kernel and initrd into the same /boot as my CentOS and Fedora kernel, using the same grub file, etc. - is there a way I can preserve my /boot (like I can when installing CentOS or Fedora) or am I going to need to install ubuntu w/o a /boot and then manually move files over?

I don't care if grub.conf is initially replaced - I just don't want /boot formated.

---

### Post by taurus on 2008-02-09
Not sure where you've heard that rumor but if you want to use the same /boot. then just mount that partition as /boot and DO NOT format it.  In this case, you should pick Manual when you get to the partition part during the installing process.

---

### Post by bikeman01 on 2008-02-09
tis true

[http://ubuntuforums.org/showthread.php?p=4300077#post4300077](http://ubuntuforums.org/showthread.php?p=4300077#post4300077)

---

