---
title: "Is it possible to reduce my ubuntu primary partition"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by sureshsaragadam on 2011-11-17
[SIZE=2]Hi Forum,

With default installation of Ubuntu 11.10 on my Laptop,[/SIZE] [SIZE=2]
It has occupied the full 500 GB,

[/SIZE][SIZE=2]$*sudo fdisk -l /dev/sda*

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968564735   484281344   83  Linux
/dev/sda2       968566782   976771071     4102145    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       968566784   976771071     4102144   82  Linux swap / Solaris


Now i need to reduce the '[/SIZE]  [SIZE=2]**sda1**' which is my **primary partition**,

I have a Ubuntu 11.10 USB Startup Disk. [/SIZE] [SIZE=2]
Booting from my Startup Disk, Can i reduce my sda1 with gparted tool? 

And later, Can i safely boot my laptop?[/SIZE]

---

### Post by raja.genupula on 2011-11-17
yeah you can use gparted for that and it is safe . no problem will rise .

all the best.

---

### Post by Mark Phelps on 2011-11-17
No partition work is absolutely safe ... there is always the possibility of something going wrong.

Also, GParted can take a LONG time with large partitions, so:
1) Don't abort or interrupt the process before it finishes, even if it keeps running for HOURS
2) Make sure that your laptop is on AC power, not Battery, as power failures while in progress will leave your partitions corrupted.

---

### Post by sureshsaragadam on 2011-11-17
[SIZE=2]Yes It worked fine, After resizing my primary Ubuntu partition with external Ubuntu using gparted,
[/SIZE]
And it  tool lot of time, Now my hard-disk can be utilized far better,

As i booted from the external ubuntu, with gparted 

1. delete both 'sda5', 'sda2'  (both swap and extended partitions)
2. resize the sda1 (which is the primary partition, don't delete this)
3. create your own partition lay out.
4. apply for the changes.
5. get ready to wait for a long time to get job done.

so:
1) Don't abort or interrupt the process before it finishes, even if it keeps running for HOURS
2) Make sure that your laptop is on AC power, not Battery, as power  failures while in progress will leave your partitions corrupted. 	


[SIZE=2][B]$fdisk -l /dev/sda
[/B][/SIZE]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0002e658

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   253962239   126980096   83  Linux
/dev/sda2       253962240   460685311   103361536   83  Linux
/dev/sda3       460685312   563902463    51608576   83  Linux
/dev/sda4       563902464   976773119   206435328    5  Extended
/dev/sda5       563904512   636569599    36332544   83  Linux
/dev/sda6       636571648   709375999    36402176   83  Linux
/dev/sda7       709378048   778901503    34761728   83  Linux
/dev/sda8       778903552   823226367    22161408   83  Linux
/dev/sda9       823228416   856393727    16582656   83  Linux
/dev/sda10      856395776   864784383     4194304   82  Linux swap / Solaris

[SIZE=3]Now i have my partitions ready for multi-boot.[/SIZE]

---

