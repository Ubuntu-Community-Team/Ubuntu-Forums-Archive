---
title: "deep freeze"
date: 2018-02-26
forum: Installation &amp; Upgrades
---

### Post by supaboi on 2018-02-26
is it possible to use a software like deep freeze on ubuntu 17.10 so that while installation if i screw up my OS main Files it wont affect my system?

P.S: i am new to Ubuntu, using it for educational purposes, please reply soon, thanks

---

### Post by wyliecoyoteuk on 2018-02-26
Backups and sensible partitioning are the best options.
Select a separate /home partition when installing and that is where all of your personal data and configuration files will be stored.
Which means that apart from a hard disk failure, even if the main OS is trashed your data is safe. 
Linux is pretty robust, and normal users cannot install software or alter the main OS, only someone with sudo (admin ) rights can do this.
Of course if you are learning, and you have sudo rights, you may make mistakes.
It might be best to install Ubuntu in a virtual machine using Virtualbox. 
Then you can take a snapshot before you try a new application, and roll it back if there is a problem.
Of course even a full re-install only takes about 30 minutes or so.

---

