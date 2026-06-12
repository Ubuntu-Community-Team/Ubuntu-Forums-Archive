---
title: "sources.list"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by jayprakash on 2005-08-14
Hi,
first sorry if this question was already answered but I realy don't have now time to search. Please help me.

From the beggining in the sources was cdrom ubuntu (kubuntu in my case), but I don't want to always take the CD everywhere I go (but I have internet nearly everywhere (I have a notebook)), so I have commented the line " deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted ".
But after it begun to go crazy.
After every reboot is the sources.list all commented, it looks like it is the deafault but all the added sources are there but commented, and on the reboot on tty1 it asks me from which country I am. It wants to make the sources.list file a new.
Even if I go thru all the confirmations and the new sources.list is made, on the reboot it is again commented.

Please what to do that it works.

---

### Post by jasmuz on 2005-08-14
When you modify the list, do you save it, and if so do you run sudo apt-get update?

---

### Post by jayprakash on 2005-08-14
I tryed all combinations:
Save list, reboot
Save list, synaptic update, reboot
the setup on tty1, ...
Synaptic - sources , ...

every time is the sources.list "defaulted"

---

### Post by Thulemanden on 2005-09-12
I wonder if he saves it as root

---

