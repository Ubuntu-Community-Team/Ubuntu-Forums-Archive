---
title: "upgrade 8.04 --&gt; 10.04"
date: 2011-12-12
forum: Installation &amp; Upgrades
---

### Post by granqvist on 2011-12-12
I am not really happy about things that happened during the upgrade. 
After reboot I was left with a system only working through a rescue console. 

Searched on error message "mountall.c 3204" and things started to wind up.

Followed instructions on [http://www.linode.com/forums/viewtopic.php?p=28115](http://www.linode.com/forums/viewtopic.php?p=28115)

Especially this post helped:
"1. log in to rescue shell 
 
2. mount -o remount,rw / 
 
3. mkdir /var/run/network 
     ifup eth0 
 
Networking required for apt-get. I was missing /var/run/network after upgrade, not sure why. 
 
4. apt-get install linux-image-virtual 
 
This will provide the right kernel and run update-initramfs. It will fail but that's enough to get a normal boot. 
 
5. reboot 
 
6. apt-get -f install "

Oh yes, but ifup did not work. After some searching on  the system to ensure my network card drivers were loaded I ended up in  editing /etc/udev/rules.d/70-persistent-net.rules. The upgrade process  had messed with interface numbers, making them unusable. 

Having  network up and installing a new linux image made things little better.  But I still did not get a working system. /home should be  mounted on  /dev/md0, a raid1 array, and /dev/md0 was configured in  /etc/mdadm/mdadm.conf as 
...
DEVICE /dev/sda1 /dev/sdb1
ARRAY /dev/md0 devices=/dev/sda1,/dev/sdb1 auto=yes
...

But  the upgrade process messed the device names, renaming /dev/sda1 to  /dev/sdc1, thus making /dev/md0 inactive. Finally, after editing  /etc/mdadm/mdadm.conf to look like 
...
DEVICE /dev/sdb1 /dev/sdc1
ARRAY /dev/md0 devices=/dev/sdb1,/dev/sdc1 auto=yes
...

the system seems to work as expected.

To me the upgrade process did not give a very convincing picture of ubuntu. What do you think?

Ps.

.bash_history can be helpful on systems one attends not too often.

---

