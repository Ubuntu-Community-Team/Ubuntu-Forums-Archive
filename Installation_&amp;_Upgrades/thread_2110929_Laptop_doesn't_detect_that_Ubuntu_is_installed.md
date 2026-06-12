---
title: "Laptop doesn't detect that Ubuntu is installed"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by Dream1ng on 2013-01-31
I installed Ubuntu 12.10 and it seemed to be ok - it gave me a message that it's ready and I should restart the computer and so did I. But because I left the USB there, it instalation began again. I canceled it and restarted again removing the USB - and there was BIOS only, as if a have never installed OS. :( I reinstalled Ubuntu and this time I removed the USB when restarting but again no result - there was only BIOS. I assume that the installation is fine, because when I try to install it again it says that there already is Ubuntu installed, but I can't escape from this problem - when there is no USB - no OS is detected, when the USB is there - a new installation starts. :(

---

### Post by oldfred on 2013-01-31
Welcome to the forums.

From your installer use live mode to boot into the version on the live flash drive. Then install Boot-Repair and post link to BootInfo report

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Dream1ng on 2013-01-31
Thank you very much! :) That solved the problem. Looks like Ubuntu has a great community.

---

