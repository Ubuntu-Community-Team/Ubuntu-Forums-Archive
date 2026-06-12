---
title: "Making startup disks"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by rohit raj on 2010-08-06
I have cd of kubuntu 9.10. I have installed kubutnu 9.10 from it and using apt-get upgraded to kubuntu 10.04. Now kubuntu 10.04 works perfect on my system. Now my problem is that i want to dual boot with windows. If i install windows. Grub menu gets corrupted. 

If i create a startup disk in kubuntu 10.04. Then will whenever i want to again install kubuntu, will it install kubuntu 10.04 or kubuntu 9.10. If not what is the way to completely back up my installation. If copy my root folder in a hard disk. Will i will be able to recover my system.

---

### Post by ajgreeny on 2010-08-06
All you will need to do after installing windows is restore grub
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) for grub2 or
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) for legacy grub, then for grub2 run ```
sudo update-grub
```or for legacy grub, edit the menu to add a windows entry.

There is no need to re-install ubuntu or kubuntu.

---

### Post by rohit raj on 2010-08-06
Thanks a lot

---

