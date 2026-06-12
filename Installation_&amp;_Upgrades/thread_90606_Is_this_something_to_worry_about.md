---
title: "Is this something to worry about?"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by ed_d on 2005-11-15
I have installed Ubuntu, and installed the smp kernal; but when I do an "df -h" here is the response:

ed@Loki:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              16G  2.7G   13G  18% /
tmpfs                 506M     0  506M   0% /dev/shm
**tmpfs                 506M   13M  494M   3% /lib/modules/2.6.12-9-686-smp/volatile**
/dev/sdb5              34G   10G   23G  32% /multimedia

Should I be worried about this?

---

### Post by rmjokers on 2005-11-15
I have the same thing on my system so it probably shouldnt concern you too much.  I dont know what exactly its purpose is though.

---

