---
title: "help wanted for partitioning hard disk"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by dss.chandra on 2010-02-02
I have  a Ubuntu 9.04 installation on my hard disk , partitioned as follows
```

Filesystem         Size    Used   Avail Use%   Mounted on
/dev/sda1           142G   4.2G   9.1G  32%       /
tmpfs                 988M     0      988M  0%     /lib/init/rw
varrun                988M  120K    988M   1%     /var/run
varlock               988M    0       988M   0%       /var/lock
udev                  988M  160K     988M  1%      /dev
tmpfs                 988M    76K     988M  1%     /dev/shm
lrm                   988M   2.2M     986M  1%    /lib/modules/2.6.28-15-generic/volatile

```I want to have a dual boot hard disk of ubuntu and windows . Can you please tell me what steps I should follow ?

---

### Post by dabl on 2010-02-02
Here is guidance:  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by oldfred on 2010-02-02
You are just showing the mounted space in Ubuntu.

show this listing:
 sudo fdisk -lu

What version of windows?

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

APC various dual boot graphical install
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)
Installing Ubuntu 9.10 Step-by-step installation tutorial with screenshots
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
Jaunty Jackalope / Windows7 Ultimate MultiBoot 'C' (with checkbox graphic for vista/7) 
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

