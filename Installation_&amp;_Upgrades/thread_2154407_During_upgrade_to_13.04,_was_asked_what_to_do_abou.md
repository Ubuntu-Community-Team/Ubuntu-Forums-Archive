---
title: "During upgrade to 13.04, was asked what to do about Samba config file"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by AtariBaby on 2013-06-14
During my upgrade, a message from "debconf" popped up, in regards to "samba server and utilities" asking what I wanted to do about conflicts with my smb.cnf file. Among the options were keeping the existing file and a 3-way merge. I tried the 3-way merge which failed, and so I selected to keep the existing file.

I'm something of a n00b still, but I *think* samba is kind of important, because the machine is on a mixed-OS network and does lots of interacting with other machines. I seem to remember getting everything working in 12.10 was not without difficulties.

I'm wondering if I need to do anything or leave as is, assuming I don't discover something has been broken in the upgrade process!

---

### Post by dino99 on 2013-06-14
you still can check its configuration, from a terminal, run:

sudo dpkg-reconfigure samba

.... and try some exchange on the network to know if its working as expected

---

### Post by Rebelli0us on 2013-06-14
If your network shares still work fine I wouldn't worry about it.  During updates the installer ofter asks techno-gibberish questions, just select to "keep existing ..."

---

