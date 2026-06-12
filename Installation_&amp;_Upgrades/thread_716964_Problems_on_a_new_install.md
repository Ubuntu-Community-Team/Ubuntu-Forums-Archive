---
title: "Problems on a new install"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by KMJones1 on 2008-03-06
I have built a new machine and installed Ubuntu OK (only - no dual boot) on a small HDD (6.5GB) that I will not use for anything else, and there is a 120GB disk also. The machine is on an ethernet with 3 WinXP machines via a router.
Two questions:
1. The 120GB disk in the Ubuntu machine is brand new and it doesn't seem to appear anywhere. Presumably I have to format it etc. I want this disk to be seen by my Windows XP machines on the network so they can use it for files. How do I do this and get it recognised by all machines?
2. The Ubuntu machine sees the WinXP machines but they cannot see the Ubuntu machine. How do I fix this?
I'm quite new to Linux but can handle command line instructions etc. OK.
:confused:

---

### Post by prshah on 2008-03-06
Answers in reverse:

2) Install samba: sudo apt-get install samba (or just open Places->Network and follow the prompts).

1) Use "sudo fdisk /dev/xxx" where xxx is your 120GB hdd (sdb, hdb?). or you can use Gnome Partition Editer (Gparted), use either "Applications->Add/Remove" or "sudo apt-get install gparted" to install it 

Cheers,
PRShah

---

### Post by KMJones1 on 2008-03-07
Thanks prshah - I'll give it a try later (busy today!)

---

