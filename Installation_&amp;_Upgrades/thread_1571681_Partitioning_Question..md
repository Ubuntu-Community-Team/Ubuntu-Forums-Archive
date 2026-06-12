---
title: "Partitioning Question."
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by blue98 on 2010-09-10
If I were to use Wubi, would I be able to remove Ubuntu off of that partition and use it one more with Windows?

For instance, I have 500 gb, and if I wanted to use 20g for Ubuntu, if I changed my mind could I add the 20g to the 480g?

If it's still too confusing I'll try and explain it again, I'm not that good at this seeing in how it's been years since I've played with Ubuntu!

Thanks for your help!

---

### Post by bcbc on 2010-09-10
Wubi doesn't use partitions. It uses a virtual disk (just a large file under your windows file system). When you uninstall the wubi Ubuntu it deletes that virtual disk and you can reuse that space, the same as if you deleted any file from windows.

---

### Post by blue98 on 2010-09-10
> **bcbc said:**
> Wubi doesn't use partitions. It uses a virtual disk (just a large file under your windows file system). When you uninstall the wubi Ubuntu it deletes that virtual disk and you can reuse that space, the same as if you deleted any file from windows.

So we don't boot to it, we play it like we would on Windows?

And If I were not to use Wubi, and use the Ubuntu Partitioner, could you answer my question then?

---

### Post by oldfred on 2010-09-10
Its a little more work as you have to create the partitions for / (root) and swap or the installer does if you just want to install in space you have created. If then you do not want Ubuntu you need to first reinstall the windows boot loader to the MBR to boot windows, delete the Ubuntu partitions and re-expand the windows partition.

If you are using partitions it is best to use the windows management console to shrink the windows partition and reboot windows several times as it often wants to run chkdsk or other repairs after a resize.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Full Disk install Lucid Graphical
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by blue98 on 2010-09-10
Edit: NVM

---

