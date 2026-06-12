---
title: "problem detecting intel matrix RAID10 and start intalling 10.04"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by ttomppa on 2010-06-17
Hi, 

Im trying to install ubuntu 10.04 to my raid 1+0 array. Install just sees four different hd:s

main-0
main-1 
storage-0
storage-1 

There is not showing any size or anything. 

i have set two raid arrays: main and storage, both with 4-hard-driver (raid10). Storage array is partitioned to 1TB and 400GB partitions, 400GB partition is where i want to install ubuntu. Main array has windows already. 

Where to go next?



root@ubuntu:~/src# dmraid -ay
RAID set "isw_beieefiehj_main" already active
RAID set "isw_beieefiehj_storage" already active
RAID set "isw_beieefiehj_main1" already active
RAID set "isw_beieefiehj_storage1" already active
root@ubuntu:~/src# parted_devices
/dev/sda    1000204886016    ATA SAMSUNG HD103UJ
/dev/sdb    1000204886016    ATA SAMSUNG HD103SJ
/dev/sdc    1000204886016    ATA SAMSUNG HD103UJ
/dev/sdd    1000204886016    ATA SAMSUNG HD103SJ
/dev/sde    16011542528    Kingston DataTraveler 2.0
/dev/mapper/isw_beieefiehj_storage-1    785451716608    Linux device-mapper (mirror)
/dev/mapper/isw_beieefiehj_storage-0    785451716608    Linux device-mapper (mirror)
/dev/mapper/isw_beieefiehj_main-1    214748499968    Linux device-mapper (mirror)
/dev/mapper/isw_beieefiehj_main-0    214748499968    Linux device-mapper (mirror)
root@ubuntu:~/src# ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 59 2010-06-17 11:23 control
brw-rw---- 1 root disk 252,  2 2010-06-17 11:23 isw_beieefiehj_main
brw-rw---- 1 root disk 252,  0 2010-06-17 08:38 isw_beieefiehj_main-0
brw-rw---- 1 root disk 252,  3 2010-06-17 11:23 isw_beieefiehj_main1
brw-rw---- 1 root disk 252,  1 2010-06-17 08:38 isw_beieefiehj_main-1
brw-rw---- 1 root disk 252,  7 2010-06-17 11:23 isw_beieefiehj_storage
brw-rw---- 1 root disk 252,  4 2010-06-17 08:38 isw_beieefiehj_storage-0
brw-rw---- 1 root disk 252,  6 2010-06-17 11:23 isw_beieefiehj_storage1
brw-rw---- 1 root disk 252,  5 2010-06-17 08:38 isw_beieefiehj_storage-1

---

### Post by tent405 on 2010-07-21
I'm having the same issue. 4 hard drives. Onboard RAID. 

I'll post a solution when I figure it out. Has to be something obvious...

---

### Post by ronparent on 2010-07-21
There seems to be a problem with stipe+mirror raid setups in 10.04 in general. See this thread : [http://ubuntuforums.org/showthread.php?t=1533793](http://ubuntuforums.org/showthread.php?t=1533793)

I'll be watching for a solution since this problem intrigues me. Good luck.

---

