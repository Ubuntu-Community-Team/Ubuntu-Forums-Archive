---
title: "ROOT and USR Directories full"
date: 2015-11-25
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2015-11-25
I have suddenly hit a problem.  My ROOT and USR Directories are full and there is no room on the Hard Drive to enlarge them.  Not only that they are showing as quite huge and I don't know why.

HD = 230Gb
SDB1= 167.29Gb, 117.32Gb used = Windows install
SDB3 = 35.39Gb, 35.37Gb used = ROOT
SDB2 = 20.41Gb, 18.5Gb used = /USR
SDB4 = 9.78, = SWAP

HOME and Documents are all on another HD.....

I have tried sudo apt-get autoremove which only removed a small file
sudo apt-get autoclean and clean do not work as there is no space.......
Tried to use "Residual config" in Synaptic Package Manager but that fails due to being full.

Can anyone help?
I need to free space and understand what is filling up the directories......

---

### Post by deadflowr on 2015-11-25
Do you regularly clean your old kernels, fully?
Kernels images reside in the /boot folder (and modules usually reside in the /lib/modules folder), but the headers usually reside in the /usr/src folder
While the /boot folder might be light in space used, the lib/modules folder and the /usr/src folders might be a little heavier in space used.
Something like this
```
du -h --max-depth=0 /usr/src /boot /lib/modules
```
should show the basic space used in all 3 areas.
(I'm spitballing something to look at, not that it will be helpful at all)

Also note that the apt-get autoclean clears the /var/cache/apt/archives folder of out-of-date installation packages that where once downloaded during an update some time ago.
It does not clean the full archives, but only the packages where a newer version is available.
Case in point, it won't clean out packages where only one version exists, but will if 2 or more do.
As an example, firefox downloads a fully new package every time it updates, so the archives fill up with older versions.
The autoclean will remove those older versions, but keep the latest/newest one.
If that makes sense.

Of course, on the other hand apt-get clean, does clean out the full archive folder, in a scorched earth kind of way...

---

### Post by Jonners59 on 2015-11-25
CHeers
From time to time I do a clear out, but not in a while
I tried the cmd```
du -h --max-depth=0 /usr/src /boot /lib/modules
``` and this is what I got:
```
498M    /usr/src
161M    /boot
675M    /lib/modules

```

Just tried ```
dpkg -l | grep linux-image-
``` and got

```
rc  linux-image-3.19.0-25-generic                                3.19.0-25.26                                          amd64        Linux  kernel image for version 3.19.0 on 64 bit x86 SMP
rc   linux-image-3.19.0-26-generic                                3.19.0-26.28                                          amd64        Linux  kernel image for version 3.19.0 on 64 bit x86 SMP
rc   linux-image-3.19.0-28-generic                                3.19.0-28.30                                          amd64        Linux  kernel image for version 3.19.0 on 64 bit x86 SMP
rc   linux-image-3.19.0-30-generic                                3.19.0-30.34                                          amd64        Linux  kernel image for version 3.19.0 on 64 bit x86 SMP
ii   linux-image-3.19.0-31-generic                                3.19.0-31.36                                          amd64        Linux  kernel image for version 3.19.0 on 64 bit x86 SMP
ii   linux-image-4.2.0-16-generic                                 4.2.0-16.19                                           amd64        Linux  kernel image for version 4.2.0 on 64 bit x86 SMP
ii   linux-image-4.2.0-17-generic                                 4.2.0-17.21                                           amd64        Linux  kernel image for version 4.2.0 on 64 bit x86 SMP
ii   linux-image-4.2.0-18-generic                                 4.2.0-18.22                                           amd64        Linux  kernel image for version 4.2.0 on 64 bit x86 SMP
rc   linux-image-extra-3.19.0-25-generic                          3.19.0-25.26                                          amd64        Linux  kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc   linux-image-extra-3.19.0-26-generic                          3.19.0-26.28                                          amd64        Linux  kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc   linux-image-extra-3.19.0-28-generic                          3.19.0-28.30                                          amd64        Linux  kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc   linux-image-extra-3.19.0-30-generic                          3.19.0-30.34                                          amd64        Linux  kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc   linux-image-extra-3.19.0-31-generic                          3.19.0-31.36                                          amd64        Linux  kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii   linux-image-extra-4.2.0-16-generic                           4.2.0-16.19                                           amd64        Linux  kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii   linux-image-extra-4.2.0-17-generic                           4.2.0-17.21                                           amd64        Linux  kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii   linux-image-extra-4.2.0-18-generic                           4.2.0-18.22                                           amd64        Linux  kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii   linux-image-generic                                          4.2.0.18.20                                           amd64         Generic Linux kernel image
```

But ```
sudo apt-get autoclean
```
Gives me:
```
Reading package lists... Error!
E: Write error - write (28: No space left on device)
E: Can't mmap an empty file
E: Failed to truncate file - ftruncate (9: Bad file descriptor)
E: The package lists or status file could not be parsed or opened.
```
Which does not look good.  Something looks wrong here too.

---

### Post by Bashing-om on 2015-11-25
Jonners59; Hello, again ..:)

Maybe more at play than a space issue .. maybe it is addressing to the space, as in out of inodes ?
What returns:
```

df -h
df -i

```


[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-11-25
Let's also see the output of ```
mount && df -h
``` as I am wondering if you have a separate /boot partition which is now full.

---

### Post by Jonners59 on 2015-11-25
Hiya Bashin-on
Good to see you......  
ANd thanks AJGreeny for dropping in

Machine is getting unworkable.  I was wondering if it was creating files and directories that should be in "Documents" or some of the apps, like Crossover were creating temp files that have just been building up...  but where.

INTERESTING!!!  Just noticed this AM (it is 3:30AM here) that ROOT has dropped upon reboot to only 15Gb!!!!!!!!!!  SO is OK today.

```
df -h
```

```
Filesystem                Size  Used Avail Use% Mounted on
udev                      7.9G     0  7.9G   0% /dev
tmpfs                     1.6G   23M  1.6G   2% /run
/dev/sdb3                  35G   15G   19G  44% /
/dev/sdb2                  20G   19G  910M  96% /usr
tmpfs                     7.9G   19M  7.9G   1% /dev/shm
tmpfs                     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                     7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda5                  97G   33G   59G  37% /home
/dev/sda1                  37G  134M   35G   1% /home/baronipc/Backup
/dev/sda3                 331G  136G  196G  41% /home/baronipc/Desktop/Documents
/dev/sdb1                 168G  118G   50G  71% /home/baronipc/Windows
cgmfs                     100K     0  100K   0% /run/cgmanager/fs
//192.168.1.50/documents  688G  497G  157G  77% /media/Server
tmpfs                     1.6G   32K  1.6G   1% /run/user/1000

```

```
df -i
```

```
Filesystem                  Inodes  IUsed     IFree IUse% Mounted on
udev                       2047754    628   2047126    1% /dev
tmpfs                      2051792    985   2050807    1% /run
/dev/sdb3                  2321984  57996   2263988    3% /
/dev/sdb2                  1338240 600480    737760   45% /usr
tmpfs                      2051792     65   2051727    1% /dev/shm
tmpfs                      2051792      9   2051783    1% /run/lock
tmpfs                      2051792     17   2051775    1% /sys/fs/cgroup
/dev/sda5                  6406144 188559   6217585    3% /home
/dev/sda1                  2441216    113   2441103    1% /home/baronipc/Backup
/dev/sda3                205029208  24075 205005133    1% /home/baronipc/Desktop/Documents
/dev/sdb1                 52880340 407396  52472944    1% /home/baronipc/Windows
cgmfs                      2051792     13   2051779    1% /run/cgmanager/fs
//192.168.1.50/documents  45793280 192291  45600989    1% /media/Server
tmpfs                      2051792     26   2051766    1% /run/user/1000

```

```
mount && df -h
```
```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8191016k,nr_inodes=2047754,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1641436k,mode=755)
/dev/sdb3 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb2 on /usr type ext4 (rw,relatime,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=22,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
sunrpc on /run/rpc_pipefs type rpc_pipefs (rw,relatime)
nfsd on /proc/fs/nfsd type nfsd (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda5 on /home type ext4 (rw,relatime,data=ordered)
/dev/sda1 on /home/baronipc/Backup type ext4 (rw,relatime,data=ordered)
/dev/sda3 on /home/baronipc/Desktop/Documents type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1 on /home/baronipc/Windows type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
//192.168.1.50/documents on /media/Server type cifs (rw,relatime,vers=1.0,cache=strict,domain=SERVER,uid=1000,forceuid,gid=0,noforcegid,addr=192.168.1.50,unix,posixpaths,serverino,mapposix,acl,rsize=1048576,wsize=65536,actimeo=1)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1641436k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
Filesystem                Size  Used Avail Use% Mounted on
udev                      7.9G     0  7.9G   0% /dev
tmpfs                     1.6G   31M  1.6G   2% /run
/dev/sdb3                  35G   16G   18G  49% /
/dev/sdb2                  20G   19G  910M  96% /usr
tmpfs                     7.9G   19M  7.9G   1% /dev/shm
tmpfs                     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                     7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda5                  97G   33G   59G  37% /home
/dev/sda1                  37G  134M   35G   1% /home/baronipc/Backup
/dev/sda3                 331G  136G  196G  41% /home/baronipc/Desktop/Documents
/dev/sdb1                 168G  118G   50G  71% /home/baronipc/Windows
cgmfs                     100K     0  100K   0% /run/cgmanager/fs
//192.168.1.50/documents  688G  497G  157G  77% /media/Server
tmpfs                     1.6G   32K  1.6G   1% /run/user/1000

```

---

### Post by Jonners59 on 2015-11-26
Interesting update....  As I have been working through some MS Word docs and Excel spreadsheets so I have been getting warnings that ROOT is full, again.

Updated info......  Why does ROOT fill up?

```
df -h
```
```
Filesystem                Size  Used Avail Use% Mounted on
udev                      7.9G     0  7.9G   0% /dev
tmpfs                     1.6G  111M  1.5G   7% /run
/dev/sdb3                  35G   35G     0 100% /
/dev/sdb2                  20G   19G  910M  96% /usr
tmpfs                     7.9G   19M  7.9G   1% /dev/shm
tmpfs                     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                     7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda5                  97G   33G   59G  37% /home
/dev/sda1                  37G  134M   35G   1% /home/baronipc/Backup
/dev/sda3                 331G  136G  196G  41% /home/baronipc/Desktop/Documents
/dev/sdb1                 168G  118G   50G  71% /home/baronipc/Windows
cgmfs                     100K     0  100K   0% /run/cgmanager/fs
//192.168.1.50/documents  688G  497G  157G  77% /media/Server
tmpfs                     1.6G   32K  1.6G   1% /run/user/1000

```

```
df -i
```
```
Filesystem                  Inodes  IUsed     IFree IUse% Mounted on
udev                       2047754    628   2047126    1% /dev
tmpfs                      2051792   1001   2050791    1% /run
/dev/sdb3                  2321984  58101   2263883    3% /
/dev/sdb2                  1338240 600480    737760   45% /usr
tmpfs                      2051792     64   2051728    1% /dev/shm
tmpfs                      2051792     10   2051782    1% /run/lock
tmpfs                      2051792     17   2051775    1% /sys/fs/cgroup
/dev/sda5                  6406144 188654   6217490    3% /home
/dev/sda1                  2441216    113   2441103    1% /home/baronipc/Backup
/dev/sda3                205028572  24097 205004475    1% /home/baronipc/Desktop/Documents
/dev/sdb1                 52880340 407396  52472944    1% /home/baronipc/Windows
cgmfs                      2051792     13   2051779    1% /run/cgmanager/fs
//192.168.1.50/documents  45793280 192291  45600989    1% /media/Server
tmpfs                      2051792     26   2051766    1% /run/user/1000
```

```
mount && df -h
```
```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8191016k,nr_inodes=2047754,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1641436k,mode=755)
/dev/sdb3 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb2 on /usr type ext4 (rw,relatime,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=22,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
sunrpc on /run/rpc_pipefs type rpc_pipefs (rw,relatime)
nfsd on /proc/fs/nfsd type nfsd (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda5 on /home type ext4 (rw,relatime,data=ordered)
/dev/sda1 on /home/baronipc/Backup type ext4 (rw,relatime,data=ordered)
/dev/sda3 on /home/baronipc/Desktop/Documents type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1 on /home/baronipc/Windows type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
//192.168.1.50/documents on /media/Server type cifs (rw,relatime,vers=1.0,cache=strict,domain=SERVER,uid=1000,forceuid,gid=0,noforcegid,addr=192.168.1.50,unix,posixpaths,serverino,mapposix,acl,rsize=1048576,wsize=65536,actimeo=1)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1641436k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
Filesystem                Size  Used Avail Use% Mounted on
udev                      7.9G     0  7.9G   0% /dev
tmpfs                     1.6G  111M  1.5G   7% /run
/dev/sdb3                  35G   35G     0 100% /
/dev/sdb2                  20G   19G  910M  96% /usr
tmpfs                     7.9G   19M  7.9G   1% /dev/shm
tmpfs                     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                     7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda5                  97G   33G   59G  37% /home
/dev/sda1                  37G  134M   35G   1% /home/baronipc/Backup
/dev/sda3                 331G  136G  196G  41% /home/baronipc/Desktop/Documents
/dev/sdb1                 168G  118G   50G  71% /home/baronipc/Windows
cgmfs                     100K     0  100K   0% /run/cgmanager/fs
//192.168.1.50/documents  688G  497G  157G  77% /media/Server
tmpfs                     1.6G   32K  1.6G   1% /run/user/1000
```

---

### Post by deadflowr on 2015-11-26
Perhaps you can glean some usefulness from this thread:
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by Jonners59 on 2015-11-26
Can't even boot into the machine properly, now.  Half the apps don't work....  GGggrrrrr  Shall take a look, Cheers

OK, so booted using Grub Repair  WOuld not allow me to do anything so just booted in again, this time with LiveCD.
The Windows NTFS partion will not allow me to do anything and has a "!" warning.  So I deleted it - I will have GRUB issues I know.  I am currently just enlarging the two directories "/" and "/USR" by 10Gb just so as I can open the machine.  Once done I shall recreate the NTFS for my WIndows and thenboot in to GRUB REPAIR and fix the GRUB (I hope).

I can then boot back in and work from the live machine.

OK, I am back!  That took a lot longer, and not perfect temp fix.  DOes not allow me in under normal login have to use the Advanced / UPSTART option...  also just noticed that having added 10Gb, she is showing Root as full again.  I think this must be a log fiile....  Shall follow link below

---

### Post by Jonners59 on 2015-11-26
OK have found large and one very large file in VAR/

The 40Gb file repeats:
[HTML]E [23/Nov/2015:16:20:05 +0000] PDF: File "/usr/lib/cups/filter/commandtops" has insecure permissions (0100775/uid=0/gid=0).
E [23/Nov/2015:16:20:05 +0000] SittingRoomPrinter: File "/usr/lib/cups/filter/epson-escpr-wrapper" has insecure permissions (0100775/uid=0/gid=0).
W [24/Nov/2015:07:57:01 +0000] CreateProfile failed: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/HTML]

I am deleting the contents of the files....  Seems to have worked, but can't find any obvious ones in /usr it just seems to be that size.

/usr/lib/ =10Gb with
/usr/lib/x86_64-linux-gnu/ = 2.2Gb
/usr/lib/debug/ = 4.4Gb

/usr/share/ = 6.3G with
/usr/share/doc/ = 1.4Gb

but no single file from what I can see.

Update:

Finding problems.
I can not copy across documents, even MS WOrd, and Chromium is not working well, LinkedIn for instance does not load properly.

---

### Post by Bashing-om on 2015-11-26
Jonners59; Hey !

Given this situation, I can fully expect that logging is running amuck .
Bet something is screaming and writing the errors to the log files.
What do you find:
```

cd /var/
sudo du -sx * | sort -n

```

Either one large file - somewhere- OR many files containing the same same info .

[INDENT][INDENT]let the hunt begin
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-11-27
> **Bashing-om said:**
> Jonners59; Hey !

Given this situation, I can fully expect that logging is running amuck .
Bet something is screaming and writing the errors to the log files.
What do you find:
```

cd /var/
sudo du -sx * | sort -n

```

Either one large file - somewhere- OR many files containing the same same info .[INDENT][INDENT]let the hunt begin
[/INDENT]
[/INDENT]



Hiya Bashin-on
So glad you are helping, I am at whits end.  Trying to apply for jobs and I can't even cut n past!!!  ALso I doing my fix I have broken my log-in and have to use Advanced -> Upstart

Results of
```

cd /var/
sudo du -sx * | sort -n

```

```

0    lock
0    run
4    local
4    mail
4    metrics
4    opt
3424    www
9112    backups
24056    tmp
33500    crash
90324    spool
259136    cache
842488    lib
34739808    log

```

ROOT is now zero Mb space and /usr/, I have no idea how it has got so large or if that matters.  I have only ever known it to get to 5Gb or 7Gb.....

```
sudo find /var -name '*' -size +1G
```
```
/var/log/cups/error_log
```

```
sudo du -h /var/log
4.0K    /var/log/backup
208K    /var/log/clamav
124K    /var/log/apache2
6.5M    /var/log/dist-upgrade/20151126-1705
7.8M    /var/log/dist-upgrade
68K    /var/log/postgresql
33G    /var/log/cups
4.0K    /var/log/boot-sav/log/2015-11-26__09h37boot-repair51/sdb1
1.1M    /var/log/boot-sav/log/2015-11-26__09h37boot-repair51/sdb
40K    /var/log/boot-sav/log/2015-11-26__09h37boot-repair51/sda
4.0K    /var/log/boot-sav/log/2015-11-26__09h37boot-repair51/sda1
16K    /var/log/boot-sav/log/2015-11-26__09h37boot-repair51/sdb3
4.0K    /var/log/boot-sav/log/2015-11-26__09h37boot-repair51/sda3
4.0K    /var/log/boot-sav/log/2015-11-26__09h37boot-repair51/sda5
4.0K    /var/log/boot-sav/log/2015-11-26__09h37boot-repair51/sdb2
1.2M    /var/log/boot-sav/log/2015-11-26__09h37boot-repair51
4.0K    /var/log/boot-sav/log/2015-11-26__09h56boot-repair14/sdb1
1.1M    /var/log/boot-sav/log/2015-11-26__09h56boot-repair14/sdb
40K    /var/log/boot-sav/log/2015-11-26__09h56boot-repair14/sda
4.0K    /var/log/boot-sav/log/2015-11-26__09h56boot-repair14/sda1
20K    /var/log/boot-sav/log/2015-11-26__09h56boot-repair14/sdb3
4.0K    /var/log/boot-sav/log/2015-11-26__09h56boot-repair14/sda3
4.0K    /var/log/boot-sav/log/2015-11-26__09h56boot-repair14/sda5
4.0K    /var/log/boot-sav/log/2015-11-26__09h56boot-repair14/sdb2
1.3M    /var/log/boot-sav/log/2015-11-26__09h56boot-repair14
2.5M    /var/log/boot-sav/log
4.0K    /var/log/boot-sav/mbr_backups
2.5M    /var/log/boot-sav
80K    /var/log/unattended-upgrades
4.0K    /var/log/gdm
4.0K    /var/log/partimage
4.0K    /var/log/samba/cores/nmbd
4.0K    /var/log/samba/cores/smbd
4.0K    /var/log/samba/cores/winbindd
16K    /var/log/samba/cores
192K    /var/log/samba
4.0K    /var/log/hp/tmp
8.0K    /var/log/hp
32K    /var/log/apt-cacher
580K    /var/log/apt
4.0K    /var/log/asterisk/cdr-csv
4.0K    /var/log/asterisk/cdr-custom
373M    /var/log/asterisk
4.0K    /var/log/efax
4.0K    /var/log/skytools
96K    /var/log/ConsoleKit
4.0K    /var/log/ntpstats
188K    /var/log/upstart
4.0K    /var/log/speech-dispatcher
28K    /var/log/lightdm
12K    /var/log/fsck
4.0K    /var/log/system-image
34G    /var/log
```

The log file just says the following over and over so must be a CUPs issue.
[PHP]E [26/Nov/2015:17:14:50 +0000] PDF: File "/usr/lib/cups/filter/commandtops" has insecure permissions (0100775/uid=0/gid=0).
E [26/Nov/2015:17:14:50 +0000] SittingRoomPrinter: File "/usr/lib/cups/filter/epson-escpr-wrapper" has insecure permissions (0100775/uid=0/gid=0).
E [26/Nov/2015:17:14:50 +0000] SittingRoomPrinter: File "/usr/lib/cups/filter/epson-escpr-wrapper" has insecure permissions (0100775/uid=0/gid=0).
E [26/Nov/2015:17:14:53 +0000] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [26/Nov/2015:17:14:53 +0000] Notifier for subscription 357 (dbus://) went away, retrying![/PHP]

---

### Post by Jonners59 on 2015-11-27
YYyyeeeee, HHHHAAAA !  FIXED... :-)

SO first found the iffy file(s)
```
sudo find /var -name '*' -size +1G
```
```
/var/log/cups/error_log
```

The entered it with gedit to find what was in its contents...
```
sudo gedit /var/log/cups/error_log
```

Noted the contents and assumed the permissions were wrong on /usr/
```
[COLOR=#000000][COLOR=#0000BB]E [/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]26[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]Nov[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]2015[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]17[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]14[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]50 [/COLOR][COLOR=#007700]+[/COLOR][COLOR=#0000BB]0000[/COLOR][COLOR=#007700]] [/COLOR][COLOR=#0000BB]PDF[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]File [/COLOR][COLOR=#DD0000]"/usr/lib/cups/filter/commandtops" [/COLOR][COLOR=#0000BB]has insecure permissions [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]0100775[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]uid[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]gid[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]).
[/COLOR][COLOR=#0000BB]E [/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]26[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]Nov[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]2015[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]17[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]14[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]50 [/COLOR][COLOR=#007700]+[/COLOR][COLOR=#0000BB]0000[/COLOR][COLOR=#007700]] [/COLOR][COLOR=#0000BB]SittingRoomPrinter[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]File [/COLOR][COLOR=#DD0000]"/usr/lib/cups/filter/epson-escpr-wrapper" [/COLOR][COLOR=#0000BB]has insecure permissions [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]0100775[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]uid[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]gid[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]).
[/COLOR][COLOR=#0000BB]E [/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]26[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]Nov[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]2015[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]17[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]14[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]50 [/COLOR][COLOR=#007700]+[/COLOR][COLOR=#0000BB]0000[/COLOR][COLOR=#007700]] [/COLOR][COLOR=#0000BB]SittingRoomPrinter[/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000BB]File [/COLOR][COLOR=#DD0000]"/usr/lib/cups/filter/epson-escpr-wrapper" [/COLOR][COLOR=#0000BB]has insecure permissions [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]0100775[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]uid[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]gid[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]).
[/COLOR][COLOR=#0000BB]E [/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]26[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]Nov[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]2015[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]17[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]14[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]53 [/COLOR][COLOR=#007700]+[/COLOR][COLOR=#0000BB]0000[/COLOR][COLOR=#007700]] [/COLOR][COLOR=#0000BB]File [/COLOR][COLOR=#DD0000]"/usr/lib/cups/notifier/dbus" [/COLOR][COLOR=#0000BB]has insecure permissions [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]0100775[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]uid[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]gid[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]).
[/COLOR][COLOR=#0000BB]W [/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]26[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]Nov[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]2015[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]17[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]14[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]53 [/COLOR][COLOR=#007700]+[/COLOR][COLOR=#0000BB]0000[/COLOR][COLOR=#007700]] [/COLOR][COLOR=#0000BB]Notifier [/COLOR][COLOR=#007700]for [/COLOR][COLOR=#0000BB]subscription 357 [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]dbus[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#FF8000]//) went away, retrying!  [/COLOR][/COLOR]
```

So I checked them by opening nautilus ```
sudo nautilus
``` in root and going first to the offending files, then folders/directories and "left click" -> "properties"

The Group was set to my ownership read and write for all so I changed it to root read

I then removed the contents of the log file - I did not remove the file!!!
```
sudo cp /dev/null /var/log/cups/error_log
```

Rebooted and all SEEMS, for now to be fixed and working including the booting up......

---

### Post by Bashing-om on 2015-11-27
Jonners59; Great !

Thar scientific method;

[INDENT][INDENT]eliminate,
And no matter how improbable
[INDENT][INDENT][INDENT]must be the cause
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-11-28
> **Bashing-om said:**
> Jonners59; Great !

Thar scientific method;
[INDENT][INDENT]eliminate,
And no matter how improbable[INDENT][INDENT][INDENT]must be the cause
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

Couldn't have done it without you guys behind me....  Thanks.

Also fixed the login only via Upstart prob.  Hope this helps someone else too

---

