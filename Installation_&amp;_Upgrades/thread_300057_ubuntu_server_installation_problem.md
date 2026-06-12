---
title: "ubuntu server installation problem"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by discoveringlinux on 2006-11-15
ok here is one for you guys :D 

I have an old Dell poweredge server that I have installed the workstation version of ubuntu on (version 6.06), which works just fine. 

I noticed that there is a server version of ubuntu as well and decided to give it a try. So I begin the installation, and it says it doesnt have a module (driver) for my hardware raid configuration. 

Now I really haven't looked into the details of this raid setup, but I do know it is 3 drives in raid 5 controlled by a scsi pci card. I cant remember the vendor atm...

So I cancel the install and I have been looking high and low on the internet to find out how to find out what module this install would be using to see if I can get it on a floppy and use it during the server install. 

Does anyone know which directory or perhaps ls command could get me that info? It seems that when it comes to hard drives in linux, its all about partitioning and not the driver modules.

Thanks for your help.

---

### Post by yabbadabbadont on 2006-11-15
lsmod is the command to list the currently loaded modules.  Unless they were compiled for the exact same kernel, you wouldn't be able to copy them from one system to use on another though...

---

### Post by discoveringlinux on 2006-11-15
Thanks for that. I am really looking for something that I can compare to. There is a list of drivers that the server install says it has and wants me to pick one. Of course, I have no idea which one it is, so I thought I would try and see what this installation used and see if that module is on the list. I also found this command: cat /proc/scsi/sg/version
30533 3.05.33 [20050908]

although I am not sure if it will help me. I will give the lsmod a look over though.

---

