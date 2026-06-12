---
title: "Virtualbox and Intrepid Ibex"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by run1206 on 2008-10-08
Hi all,
I've recently installed Intrepid onto my laptop.  Previously, i had Virtualbox running in Hardy and it was working great.  Now after my Intrepid install, i haven't been able to get the program to run.  I recently tried to use the OSE version of VirtualBox and it hangs on the window dialog "Spawning Virtual Drive" at 0%.  

Has anyone been able to get VirtualBox to run in Intrepid?

I would even try VMWare (again) if anyone been successful with that virtual program as well.  Thanks in advance.

---

### Post by run1206 on 2008-10-08
sorry for double posting but i found out a solution to the problem.

source:[http://ubuntuforums.org/showthread.php?p=5927415#post5927415](http://ubuntuforums.org/showthread.php?p=5927415#post5927415)

turns out that the vboxdrv module wasn't install during boot, so i installed the linux headers (which i forgot to install after the upgrade :oops: )

```
sudo apt-get install linux-headers-generic
```

and during this install, it recognized that i needed to install the module and installed it.  as a double check i ran this code as well...

```
sudo modprobe vboxdrv
``` 

then i ran VirtualBox and it runs again; i'm able to run XP Home within Intrepid!! :D

hope this helps others with this issue

---

