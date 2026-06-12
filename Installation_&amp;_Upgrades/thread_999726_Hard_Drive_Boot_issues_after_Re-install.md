---
title: "Hard Drive Boot issues after Re-install"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by HarrisonFan on 2008-12-02
Hi,

I recently reinstalled 8.10 and now have been seeing the time that it takes for my bios to detect the hard drives take a long time (usually about 60 sec).  It will detect them eventually, and proceeds to load grub.  One thing I noticed is after the reinstall, ubuntu seems to detect both drives as /dev/sdx instead of /dev/hdx.  Any help would be great. Thanks!  

Here is my fdisk -l output:


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006b8f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         851     6835626   83  Linux
/dev/sda2             852        4865    32242455   fd  Linux raid autodetect

Disk /dev/sdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00085e3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         973     7815591   82  Linux swap / Solaris
/dev/sdb2             974        4982    32202292+  fd  Linux raid autodetect

---

### Post by Pumalite on 2008-12-02
Post your specs. Are using any kind of RAID? sda2 and sdb2 are strange.

---

### Post by HarrisonFan on 2008-12-02
Yes, I am using Raid 1 on sdb1 and sdb2.  It seems like the raid is working.  What other specs would help?  Thanks!

Here is my df output:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              6781704   3191008   3248916  50% /
tmpfs                   257136         0    257136   0% /lib/init/rw
varrun                  257136       112    257024   1% /var/run
varlock                 257136         0    257136   0% /var/lock
udev                    257136      2800    254336   2% /dev
tmpfs                   257136       180    256956   1% /dev/shm
lrm                     257136      2000    255136   1% /lib/modules/2.6.27-9-generic/volatile
/dev/md0              31948160  17060160  13277892  57% /home

---

### Post by caljohnsmith on 2008-12-02
Since you are using RAID and Ubuntu sees your HDDs as separate, I think you might find this link helpful:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

How about giving that shot and let us know how it goes.

---

### Post by HarrisonFan on 2008-12-02
I am only mirroring my /home partition and not the root partition, is this something that FakeRaid can do as well?


My current setup:
Hard drive 1:
Root Partition
Home Partition (set up as raid device)

Hard Drive 2:
Swap 
Home Partition (second part of raid device)

---

### Post by Pumalite on 2008-12-02
That's why you have a slow boot.

---

### Post by HarrisonFan on 2008-12-02
Please forgive my ignorance. Why would this configuration cause my machine to boot slowly?

---

### Post by Pumalite on 2008-12-02
Read caljohnsmith's link.
Here is one more:
[http://ubuntuforums.org/showthread.php?t=247422](http://ubuntuforums.org/showthread.php?t=247422)

---

### Post by HarrisonFan on 2008-12-02
Thank you for those links, but I still do not understand why having a separate non-mirrored root partition and a mirrored /home partition will cause my hard drives to take a long time to register in the bios.  Can I request a quick explanation?  Thanks

---

### Post by HarrisonFan on 2008-12-03
In my last reply, I meant to mention that I have read through the links provided.  I still do not see why this configuration takes a long time to boot.  I could see where if my root partition was mirrored it may take longer to boot (if the raid device must be set up before the boot can take place).  Please some more information would be helpful.

---

### Post by HarrisonFan on 2008-12-05
Is there any way to fix this without reinstalling?

---

### Post by HarrisonFan on 2008-12-06
I am still trying to figure this out.  Would my problem go away if I added a third hd and reconfigured in the following way:

HD1
----
boot partition
root partition
swap

HD2 & HD3 set up as raid 1
----
only home partition 

Thanks ahead of time for any responses.

---

