---
title: "grube uninstall"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by collegedude10 on 2008-02-01
i had a dual boot system on my labtop with grube installed. i decided to uninstall ubuntu and put that space back onto my main partition. i used gparted.that went fine. however when i start up i get a grube error. so i guess i need to find out how to uninstall grube. through gparted i was able to load up the partition with windows on.

---

### Post by Rocket2DMn on 2008-02-01
If you no longer have Ubuntu and want windows to just load up like it did before, put in the windows cd, reboot the computer and enter the Recovery Console.  At the prompt, run
```
fixmbr
```
Windows will then restore its master boot record to normal and you will no longer have GRUB.

---

### Post by reumar on 2008-02-02
I also wish to remove Ubuntu from a windows machine - I can remove the partitions, but I need to uninstall the existing bootlader and get the windows one back, but I don't have an XP install CD. Is there any other way of doing this?

---

### Post by Pumalite on 2008-02-02
Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by collegedude10 on 2008-02-02
thanks that did it. uninstalled GRUBE, and then had to activate the partition that windows was in. the default was set to the dell utility partiton. all good now.

---

