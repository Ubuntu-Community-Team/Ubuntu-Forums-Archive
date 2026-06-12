---
title: "Encrypted private directory is not setup properly"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by Proberts042 on 2013-03-14
After using this setup of 12.04 server for a while when one day I encountered this:

***********************
paul@www:~$ dir
Access-Your-Private-Data.desktop  README.txt


paul@www:~$ less README.txt
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private

paul@www:~$ sudo ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly

paul@www:~$ sudo su
[sudo] password for paul:
root@www:/home/paul# ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly

*****************

I have looked for a couple of days and I can't seem to find a way to take care of this. I think I would like to un-encrypt these home directories. Oh yes, and I should be seeing the directories for the ten or so users that I have, and I do not.

Thanks to anyone for your help.

---

### Post by Proberts042 on 2013-03-19
Because there has been no response to this thread I have moved the issue to the Security Discussions area.

---

