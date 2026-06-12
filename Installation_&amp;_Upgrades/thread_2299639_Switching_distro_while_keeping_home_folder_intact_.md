---
title: "Switching distro while keeping home folder intact - how to repartition"
date: 2015-10-20
forum: Installation &amp; Upgrades
---

### Post by scrivi on 2015-10-20
Hi, I have Kubuntu installed and would like to switch to Ubuntu while keeping my Home folder intact. 

This is what gParted shows about my current hard drive:
[ATTACH=CONFIG]265050[/ATTACH]

I am planning to follow the instructions from here:
[http://www.makeuseof.com/tag/upgrade-switch-linux-distros-without-losing-files/](http://www.makeuseof.com/tag/upgrade-switch-linux-distros-without-losing-files/)

How should I repartition the HD and on which partition should I install the OS? Is there anything else I should be aware of?

Thanks in advance :D

---

### Post by efflandt on 2015-10-20
Ordinarily that should work. However, it is always best to back up anything you do not want to lose before resizing partitions, because if you do not have a UPS (uninterruptible power supply) or it does not last through a power failure or someone accidentally hitting a wall or power strip switch, the resizing could fail.

Also I know nothing about lvm, so your first exercise would be to see if you can even access directories and files on your partition(s) from a live/install iso. When I was doing a fresh install of 14.04 for a 12.04 system, I recursively copied (cp -r) my entire /home/username directory to a directory that I had write permission for on an external ext4 partition (that can take a while). Then after the fresh install of 14.04 I copied that back to the new system.

Win7 on that drive already uses 3 partitions, and I was not sure if grub could be installed in an extended partition, so I cannot make any more partitions and have everything including grub in sda4 (with standard dos/win mbr, since Win7 needs that to do some updates). Although grub there is just for backup (by changing boot partition on sda). I normally boot everything from grub in the mbr of sdb from a little 12.04 backup system on SSD. I have 8 GB RAM and no swap at all, but never hibernate anyway.

---

### Post by SeijiSensei on 2015-10-20
You might be able to reclaim some of the LVM space without needing to repartition.  It's been a long time since I used LVM, but this might help:  [http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume)

---

### Post by scrivi on 2015-10-21
Thanks for the replies. To be 100% safe and make the whole process  easier I think I'll just copy the HOME folder to an external HD and  reformat instead. Should I re-partition the internal HD to make a future  distro switch easier in the future, e.g. 100Gb for the OS and the  remaining 900 for data?

---

### Post by oldfred on 2015-10-21
It depends a lot on what you want to do.

If you want to distro hop or install several Linux flavors/versions, often better to have smaller / (root) of 25GB and either separate /home or /mnt/data. I have several Ubuntu installs but keep /home inside / , but then it is tiny and easily backed up as all my data is in /mnt/data and easily mounted in every install.

But if you need full drive encryption then you have to use LVM with encryption.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

