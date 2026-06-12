---
title: "ubuntu 11.10 x64 on raid-0 ssd and lvm"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by acidrop on 2012-04-10
Hello

I'm building a new system with intel i7,12gb ram ddr3 and 2 x 160gb ssd disks.
I will use it as lab with vmware workstation an some vm guests.
I'm planning to install ubuntu 11.10 x64 as host o/s.
I need help with the partitioning/disk configuration.

I am planning an alternate cd installation with the following configuration:

/boot = 500mb -> soft-raid-1
/swap = 1gb -> soft-raid-1
/root = 30gb -> soft-raid-1
/vm = all other space -> soft-raid-0

I want this configuration so i will have redudancy for the o/s and space/speed for the VMs.

My questions are:

1. Is this possible throught the alternate cd installation or i should first make this partitioning scheme form a live cd?

2. Will I have TRIM support with this config?

3. Should I consider utilising LVM on top of RAID-1, RAID-0?

Thank you for any suggestions

---

### Post by zeljkojagust on 2012-04-10
You can use Ubuntu Server CD. On the first menu, after you select installation language, press F6 and check "Expert Install" before you click Install Ubuntu. That will give you manual partitioning option. Second, you dont need 500 MB for boot partition, 128 MB is enough. Also 16 GB max for the root would be sufficient. And last, as far as I know, you can't do LVM on a partition, but on whole block device (complete hard disk).

---

### Post by acidrop on 2012-04-10
Thank you for the clarification.

1. Can't this be done using Ubuntu Desktop Alternate CD but just with server version?

2. If I create md arrays (md0,md1,md2 etc) wouldn't these considered block devices so I can apply LVM on them?

---

