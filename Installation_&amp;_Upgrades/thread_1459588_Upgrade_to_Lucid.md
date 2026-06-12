---
title: "Upgrade to Lucid"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2010-04-21
I installed 10.04 alongside the old version and now want to un-install it.Do I just delete it using Disk Utility? Or can I do it another way?

---

### Post by zvacet on 2010-04-21
You can delete that partition with Ubuntu live CD.After that you will probably need to [reinstall grub.]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

---

### Post by mcoleman44 on 2010-04-21
Yeah, you would have to reinstall Grub which isnt all that hard. Im not sure if this will work, but I would try reinstalling Grub to your current partition before you restart or make any changes.

---

### Post by dontgetshocked on 2010-04-21
I deleted the old kernels and headers thru synaptic but the new os was still there.also which cd to use,the old one or the new one? Then can i delete the partitions using disk utility?

---

### Post by mcoleman44 on 2010-04-21
Wait, are you saying you want to delete the lucid partition or your old one?

---

### Post by dontgetshocked on 2010-04-21
YES the Lucid one.

---

### Post by mcoleman44 on 2010-04-21
Boot from a live cd. Doesnt matter which one. And delete the lucid partition using either gparted or disk utility. You may not have to reinatall grub, buy Im not sure.

---

### Post by oldfred on 2010-04-21
It is slightly easier to reinstall grub from the system you want to keep, but you can do it from a liveCD. The grub in the MBR will be the last install unless you specified otherwise during the install.

reinstall from working system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

