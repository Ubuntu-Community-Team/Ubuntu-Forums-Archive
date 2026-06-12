---
title: "using lvm to create raid ( lvcreate --type raid5 --size xxxG myvg0)"
date: 2014-10-09
forum: Installation &amp; Upgrades
---

### Post by rperkins on 2014-10-09
Hello

What is the consensus of creating and maintaining raid arrays through lvcreate as opposed to mdadm?

currently I am running a mdadm array and not using lvm.
Now I am replacing the hard drives so am considering utilizing lvm for flexibility.
Best I can tell putting LVM on top of mdadm is more common than the reverse

However I see that lvm has its on mechanism to utilize raid.
Is this commonly used ?
What are the advantages and disadvantages ?

It appears it would make the raid easier to grow but how is a bad disk handled  ?

specifically I am using a 4 drive array that currently is in a raid10 config, although that is not set in stone.  I see the latest RHEL 6.4+ supports raid10 in this configuration but the manpage for ubuntu lvcreate does not mention raid10.  My question is more general in nature considering whether to even use lvm to create the raid array

[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Logical_Volume_Manager_Administration/raid_volumes.html#create-raid](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Logical_Volume_Manager_Administration/raid_volumes.html#create-raid)

TIA

---

### Post by rperkins on 2014-10-13
I was able to create a raid10 array from within lvm using  a variation of this example
lvcreate --type raid10 -l 1020 -i 2 -m 1 --nosync -n lvm_raid10 vg0

which was taken from this wiki
[http://wiki.gentoo.org/wiki/LVM#LVM_RAID10](http://wiki.gentoo.org/wiki/LVM#LVM_RAID10)

I had a little trouble as I created GPT partition table on my physical drives, but did not create any partitions.  pvcreate did not like that and 'filtered' the drives.  I blanked out the partition table and then pvcreate would accept the drives

after getting the raid10 setup from within lvm the array functioned properly.  Some things I noticed
1. you couldnt monitor the raid status @ /proc/mdstat
2.  LVM appears to use the 'device mapper' and uses that internally. There were 9 device nodes created in dev in the format of /dev/dm-0 through /dev/dm-8 . 1 of the devices appeared to be the logic volume, 4 were the PV's , and 4 were some metadata devices.  This is all an assumption based on the symbolic link structures.  I couldnt access any of these device directly but maybe it could be done through the device mapper interface.
3.  the above gentoo link did cover how to recover from a bad disk.

For myself I'm just going to create a standard mdadm raid device and lay lvm on top of this.  I can see the advantage of using one tool to setup the entire structure but am going to stick with the tried and true for now.

---

