---
title: "Upgrade requires 63MB extra space, but disk has 93BG free"
date: 2014-10-19
forum: Installation &amp; Upgrades
---

### Post by peterqb on 2014-10-19
Software updater gives an error, requiring 63.1MB more space. It seemed unlikely to me, so I checked the disk use, and Properties reveals that there is 93.5GB free.

I followed the suggestion in the dbox to use 'sudo apt-get clean' but it made no difference.

Is there a way round this? Perhaps use terminal to upgrade? It seems strange that the updater should report this statistic.

TIA

pqb

---

### Post by Elfy on 2014-10-19
Please run df -h in a terminal and paste the output here.

---

### Post by Impavidus on 2014-10-19
Let me guess... It wants more space on the /boot partition but your free space is somewhere else. There are many threads about that, and a new one is started almost daily. Use google with this search string:```
site:ubuntuforums.org space on boot partition
```

---

### Post by peterqb on 2014-10-19
> **Elfy said:**
> Please run df -h in a terminal and paste the output here.

pqb@pqb-Satellite-A110:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  107G   14G   88G  14% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.5G  4.0K  1.5G   1% /dev
tmpfs                        301M  1.0M  300M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.5G  152K  1.5G   1% /run/shm
none                         100M   32K  100M   1% /run/user
/dev/sda1                    228M  177M   40M  82% /boot
pqb@pqb-Satellite-A110:~$ 


Thanks for the reply
--
pqb

---

### Post by Elfy on 2014-10-19
As Impavidus and I thought - /boot is filling up.

You need to remove old unused kernels. 

[http://ubuntuforums.org/showthread.php?t=2248684](http://ubuntuforums.org/showthread.php?t=2248684) is from a few days ago.

Personally I'd install and use synaptic for this.

```
dpkg -l linux-image-\* | grep ^ii
``` in a terninal will give you some idea of the kernels you have installed.

---

### Post by peterqb on 2014-10-19
Thanks for the reply.

I have managed to remove some of the old kernels. Found this on google: sudo apt-get autoremove -y && sudo reboot now

Cannot download synaptic, but if the commands I used sort it, then I can do that from time to time. Updates appear to be installing OK now.

Any way of increasing the boot partition and is this a good idea?

Thanks again.
--
pqb

---

### Post by Elfy on 2014-10-19
The long and short of it is you installed with lvm/encryption - that creates a small /boot partition.

I don't use lvm nor have any experience with it - but there are ways to resize lvm - you can't use gparted to do so afaik.

Do that - then you'll be able to increase the size of /boot.

Make sure when you get upgrades that an kernel install triggers at least a memory for you to deal with older ones before you get the same issue again.

Just as a fyi - any apt-get clean or apt-get autoclean will be of no help at all in these circumstances, all they do is remove downloaded deb packages.

---

### Post by peterqb on 2014-10-21
Thanks for the replies. The encryption was set automatically, ie I had no idea it was using this when I installed.

The 'sudo apt-get autoremove -y && sudo reboot now' seemed to do the trick, and I have kept a note of that in case I need it again.

pqb

---

