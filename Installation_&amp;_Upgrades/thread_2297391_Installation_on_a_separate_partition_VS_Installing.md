---
title: "Installation on a separate partition VS Installing along side?"
date: 2015-10-03
forum: Installation &amp; Upgrades
---

### Post by remmas-sido on 2015-10-03
Hello guys 
Is there any advantages/disadvantages between Installing Ubuntu on a separate partition VS Installing it along side with Windows? 
what would you choose? what do you recommend?

---

### Post by deadflowr on 2015-10-03
Both methods will put it in a separate partition.

The manual installation method will allow you to be more nuanced allowing you to use/create other partitions if you want, like a separate home partition.
Among other nifty things like allowing you to place the bootloader where you want.

But the disadvantage is you need to know how to properly split and resize partitions.
So you need to actually pay attention.


The automated installation method to place it side by side simply creates a single large root partition and a swap partition. Not as nuanced.
And it places things like the bootloader where it sees fit, regardless of how you fell about it.

It has an advantage in that it knows how the split and resize the partitions it needs.
So you can simply set it and forget it, without the need to triple check you've set it properly.


Personally, I normally use a manual setup.
But I've done side by sides as well.
Both work fine.

So which one you choose depends more on who as a person you are, imo.
If you like control or things, manual is probably more apt.
But if you just want to get something to work, without fuss, then the automated way might suit you better.

Since you can see they both have strong advantages and disadvantages it can be hard to recommend one or the other.
Player's choice really...

---

### Post by Bashing-om on 2015-10-03
remmas-sido; Hello;

^^ +100

An adventure in system administration:
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  2.1G  2.4G  47% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  740K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   17M  2.0G   1% /run/shm
none            100M  8.0K  100M   1% /run/user
/dev/sda2       9.5G  2.5G  6.6G  28% /home
/dev/sda8       4.7G  617M  3.9G  14% /var
sysop@1404mini:~$
-----------------------

sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux
/dev/sdc3       204806144   266246143    30720000   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux
sysop@1404mini:~$
-------------------------

sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE=xt4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE=xt4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdc3: LABEL="ubie1504" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
sysop@1404mini:~$ 
---------------------------------

```

An example of what can be. This is for MY use case - testing and so forth. This suits my purposes very well; There are many many other alternative strategies .

System administration ->
[INDENT][INDENT][INDENT]gets as deep
[INDENT][INDENT][INDENT]as required
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

