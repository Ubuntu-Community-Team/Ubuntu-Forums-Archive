---
title: "Dual Boot Ubuntu 12.04 x64 with windows server 2012"
date: 2013-07-18
forum: Installation &amp; Upgrades
---

### Post by holyfist333 on 2013-07-18
I'm Trying to Dual Boot my PC with windows server 2012 and ubuntu 12.04. But when I Insert the Ubuntu Live USB and start the installation, The install alongside windows option is missing. I don't want to erase my Windows 2012. Plz guide me here :) TY :)

---

### Post by QIII on 2013-07-18
Hello!

That option is no longer shown.  Try "Do something else".

If you haven't manually partitioned before, be sure to ask questions up front rather than later!

Cheers!

---

### Post by holyfist333 on 2013-07-18
Do something else will overwrite my windows boot file right?. I have left unallocated space for Ubuntu. I want to know how to get the grub to recognize my windows 2012 as well. I'm new to Ubuntu so a few detailed instructions will definitely help :)

---

### Post by holyfist333 on 2013-07-18
And yea . . ive tried all the default options that come with the Ubuntu installer

---

### Post by oldfred on 2013-07-18
Best to see details:

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

