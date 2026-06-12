---
title: "Resizing the root partition in Ubuntu"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by mayank2013 on 2013-03-12
Hi I am fairly new user to Ubuntu and recently installed 12.10
But during installation, i was checking the partition space and it by default kept 930 GB to Ubuntu partition

Can you guys suggest how do i go about fixing it and what should be the ideal partition...

So now the current status is :

Partition     File System   mount point             Size                      Used            Flags
/dev/sda1    ext4                  /                       923.5 GB               20 GB             Boot
        sda2     extended                                  8 GB
        sda 5    Linux Swap                              8 GB

Please help out, after this i need to create a new virtual box for Windows 7 , bcoz lot of my ollege work is in wondows

---

### Post by oldfred on 2013-03-14
Moved to your own thread, old one was old.

I prefer to make / (root) 25GB and then allocate remaining parts of drive to /home or data. I have seen some with separate partitions for VMs, but have not done that myself.

You can shrink / with gparted from LiveCD.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

      
 Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

