---
title: "Not able to upgrade and install any software"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by rohkap4444 on 2012-10-26
I am Rohit and I am new to Ubuntu. I want to upgrade Ubuntu by going to System Settings--System -- Update Manager.
this error is coming:-
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

I am very frustrated as I have 5 year old laptop and I am not able to boot from USB bootable pendrive or USB CD Drive to install Ubuntu 12.04. Is there any other way so that I can do the upgrade.
:( :(

---

### Post by dino99 on 2012-10-26
Tell us what you try to ugrade (which actual ubuntu to which one)

Please post the output of (from a terminal):

cat /etc/apt/sources.list

---

### Post by jerrrys on 2012-10-26
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

---

