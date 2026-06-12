---
title: "VMWare Player disappeared in Ubuntu 10.04 64 bit"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by LPPSTechGuy on 2010-07-23
I installed VMWare Player 3.1 on Ubuntu 10.04 64 bit and had the program show up in the applications menu.  I opened and ran a prebuilt virtual machine without any problem.  After shutting down the system, the next morning Player is gone, if I try to reinstall it shows that it is already installed, and if I try to open the virtual hard drive, it says that no applications is associated with that file type.  There is no Player in the list of applications.
   
  Thanks
LPPSTech Guy

---

### Post by clrg on 2010-07-23
Open a terminal and type

```
which vmplayer
```

If it finds vmware player, it will show you the path. Most likely

```
phirt@detox:~$ whereis vmplayer
vmplayer: /usr/bin/vmplayer

```

Add an option to your menu (right-click, edit menus, new item, select the icon, name it vmware player, and put the path to vmplayer in the command field.

If you don't want to add a menu entry, just press Alt+F2, type "vmplayer" and hit enter.

---

### Post by LPPSTechGuy on 2010-07-23
CLRG,

Thank you very much, your answer brings up one other question.  Can you have more than one vmplayer?  I also have Virtual Box installed, but they seemed to coexist yesterday.

Thanks
LPPSTechGuy

---

### Post by clrg on 2010-07-23
I cannot guarantee that different virtualization products can coexist on the same machine. For example, KVM and VirtualBox don't like each other.

To answer your other question, yes, you can run many instances of vmplayer on the same machine. It depends on your resources, you can't run 5 machines with 1GB of RAM each if you only have 2GB RAM in total.

---

