---
title: "Advanced Installation 2 Drives (12.04)"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by RezPix on 2012-07-23
Hello, Currently I have 60GB SSD and a 750GB Normal Hard drive. I wish to install the Ubuntu OS onto my 60GB SSD and have all my files being put onto the 750GB drive. I am getting confused over what size do all the partitions have to be e.g root, home, swap. As I heard that all programs were put into /root. And when I'm adding the partitions do I just use the free space on the 750GB drive and will it pick it up as /home. Thanks, and any advice would be greatly appreciated.
Thanks.

---

### Post by darkod on 2012-07-23
You will have to use the manual method to install on two disks. Linux works with mount points, and doesn't care much whether the partition are on one, two or three disks. However, you have to plan it good.

First of all, the swap partition (if any) should go to the hdd, not the ssd.
The / partition (root) should be on the ssd to take advantage of the speed.

You can even set /home to be on the ssd so that the program settings are loaded faster.

On the hdd you can have one or more partitions, like data partitions, etc. If you decide to have a large /home it will have to be on the hdd too because the ssd is only 60GB.

One example of having a data partition is to have a partition on the hdd that you will assign as mount point /data when installing. That space will be available under /data in the ubuntu filesystem.

---

### Post by RezPix on 2012-07-23
Ok, thanks! I did what you said, but Installed the Root (/) onto my SSD and put the swap and Home onto my HDD. After installing everything went great! Thanks for the help!

---

