---
title: "Problem with installation partition(s)"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by vsmirnov on 2013-08-21
So, I just installed Ubuntu 13.04 on a spare 1TB hard drive (good to be back), but I'm having an odd problem. It looks like the installation did not format the drive which was, and still is NTFS. I am starting to get low disk space warnings from the OS and the Disk Usage analyzer shows my root folder as having 15.4/18.2 GB free. Gparted, on the other hand, shows the disk (/dev/sda1) as having 931.5 GB (98%) free, all on one partition. Is there any way I can get Ubuntu to recognize the rest of the space on the partition that it is on without reinstalling the whole OS?

Here is the output of df -h :

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G   15G  1.8G  90% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G   12K  3.9G   1% /dev
tmpfs           798M  904K  797M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  2.0M  3.9G   1% /run/shm
none            100M   88K  100M   1% /run/user
/dev/sda1       932G   19G  914G   2% /host
/dev/sdf1        15G  2.0G   13G  14% /media/vadim/MYLINUXLIVE
/dev/sdc1        56G   54G  2.6G  96% /media/vadim/E0F4FFF9F4FFD030
/dev/sde1       932G  928G  3.9G 100% /media/vadim/Videos
/dev/sdb5       597G  272G  325G  46% /media/vadim/Programs

Also, in previous installs, ubuntu made a System partition, a Swap partition, and a Home partition. Does it not do this anymore, or is it some anomaly with my install? Thank you very much in advance. It's good to be back to Linux.

---

### Post by oldfred on 2013-08-21
the /host and loop are from wubi which is an install inside a Windows NTFS partition. It really is just a file root.disk.
       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

It is not a full partitioned install. As I understand now, wubi can only be installed from inside Windows, not from live installer. To get full partitioned install you have to use DVD or Flash drive.

      
 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by vsmirnov on 2013-08-21
I'm not positive, but right now it looks like my only option's going to be formatting and reinstalling from USB. I didn't realize I had to install from LiveCD/USB in order to format the drive. Thankfully UbuntuOne backups are relatively painless :) . Thank you for your help.

---

