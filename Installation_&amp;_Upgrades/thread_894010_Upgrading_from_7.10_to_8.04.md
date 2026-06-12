---
title: "Upgrading from 7.10 to 8.04"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by xoom on 2008-08-18
I am attempting to upgrade from a 7.10 install to 8.04

When I run sudo apt-get dist-upgrade it stalls at:

Setting up language-support-writing-pt (1:8.04+20080328) ...
Generating locales...
  pt_BR.UTF-8... 

When I try to run anything through apt-get I get the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Running dpkg --configure -a results in:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


I'm going in circles here. any ideas?

---

### Post by jualin on 2008-08-18
Are you running the "dpkg" command with "sudo" in front of it? > sudo dpkg --configure -a

---

