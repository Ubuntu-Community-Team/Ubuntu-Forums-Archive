---
title: "rename array"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2012-11-25
Ive create a raid1 array, but when the array name is /dev/md127 after reoot.

Found a few threads, and the general consensu seems to be that I can rename /dev/md127 to what I think it should be; in this case /dev/md2

Have tried the following:

      mdadm --assemble /dev/md2 /dev/sd[cd]6  --update=name

but end up with this when I do a  mdadm --examine --scan

ARRAY /dev/md/2 metadata=1.2 UUID=809b6fc3:6a99fd91:75cc2e78:78a75baf name=ml.zudiewiener.com:2
ARRAY /dev/md0 UUID=af456ebc:d5eeedc4:bddefb1d:3bdaff5e
   spares=4
ARRAY /dev/md1 UUID=d680e291:8dd417d0:bb760188:679e16e6
   spares=1

if I do the following (as suggested in one of the threads) 

     sudo mdadm --assemble /dev/md2 /dev/sd[cd]6  --update=name --name=md2

I then get this when I do a  mdadm --examine --scan

ARRAY /dev/md/md2 metadata=1.2 UUID=809b6fc3:6a99fd91:75cc2e78:78a75baf name=ml.zudiewiener.com:md2
ARRAY /dev/md0 UUID=af456ebc:d5eeedc4:bddefb1d:3bdaff5e
   spares=4
ARRAY /dev/md1 UUID=d680e291:8dd417d0:bb760188:679e16e6

What I need is for the array to be /dev/md2 (as there is no /dev/md/md2)

Appreciate any help

---

### Post by darkod on 2012-11-25
I haven't used this option but if the second try with --name=md2 creates /dev/md/md2, then have you tried something like --name=2.

---

### Post by lister171254 on 2012-11-25
Yep. have tried that too.
 
It creates the following

ARRAY /dev/md/2 metadata=1.2 UUID=809b6fc3:6a99fd91:75cc2e78:78a75baf name=ml.zudiewiener.com:2

---

### Post by darkod on 2012-11-25
Well, that is /dev/md2. Sometimes, I don't know why or when, the format in mdadm.conf is /dev/md/X which corresponds to /dev/mdX.

Try:
sudo parted -l

to display all devices and see if it says /dev/md2.

---

### Post by lister171254 on 2012-11-25
llist@ml:~$ sudo parted -l | grep "dev/md"
Disk /dev/md0: 30.0GB
Disk /dev/md1: 1936GB
Error: /dev/md2: unrecognised disk label
llist@ml:~$ sudo mdadm --detail /dev/md2

but mdadm --detail shows the following

llist@ml:~$ sudo mdadm --detail /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Sun Nov 25 10:12:36 2012
     Raid Level : raid1
     Array Size : 1920612160 (1831.64 GiB 1966.71 GB)
  Used Dev Size : 1920612160 (1831.64 GiB 1966.71 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Nov 26 00:09:09 2012
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : ml.zudiewiener.com:2  (local to host ml.zudiewiener.com)
           UUID : 809b6fc3:6a99fd91:75cc2e78:78a75baf
         Events : 19

    Number   Major   Minor   RaidDevice State
       0       8       38        0      active sync   /dev/sdc6
       1       8       54        1      active sync   /dev/sdd6

---

### Post by lister171254 on 2012-11-27
ok. figured it out.

The problem is that the creation of the array now defaults to meta-data 1.2.

That causes gparted to fail (Libparted Bug found; could not stat device /dev/md/2) 

Creating the array with --metadata=0.90 works, but has the obvious problem that this is an older version

I'll raise this as a bug

---

