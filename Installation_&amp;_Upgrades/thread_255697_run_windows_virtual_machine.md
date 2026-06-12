---
title: "run windows virtual machine"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by u534_n4m3 on 2006-09-11
i read about this vmware server where i could run a virtual machine of a windows installation.

but the tut i read requires me to make a new windows intallation. 

is there a way to virtualy run my windows on my hda1 partition?  i have a dual boot ubuntu/xp on the same hdd.


thanks

---

### Post by dickohead on 2006-09-11
You can use VMWare through Ubuntu to run Windows, but you will need to install it INTO the VirtualMachine through VMWare. So essentially, Windows is installed into a file that VMWare runs, not a location so you can't copy files from /dev/hda1 to the VM.

---

### Post by u534_n4m3 on 2006-09-11
> **dickohead said:**
> You can use VMWare through Ubuntu to run Windows, but you will need to install it INTO the VirtualMachine through VMWare. So essentially, Windows is installed into a file that VMWare runs, not a location so you can't copy files from /dev/hda1 to the VM.

that's my problem.  i wanna know if there's a way to run my windows installation on a seperate partition.

i don't wanna reinstall it in a file.

---

### Post by dickohead on 2006-09-12
That's more a vmware issue then. As far as I know you need to install it into VMWare before using it. But you can always copy files and settings over to it afterwards.

---

