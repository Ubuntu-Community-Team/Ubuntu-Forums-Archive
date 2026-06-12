---
title: "recover deleted partition"
date: 2018-11-03
forum: Installation &amp; Upgrades
---

### Post by shenchang on 2018-11-03
hi all, 
i have a ssd harddisk hdb partitioned into 4
1: primary, start: 0-32-33 , end :124-140-16, size sect:1998848

2: prim swap, S: 124-140-17, e: 4108-93-17,size sect:64000000

3:was logic disk, has an ext4 part in it.  it was deleted accidently the logic.  i was thinking to make it as a prim part.

4: prim boot, S:15051-44-34,e:15566-19-5,size sect :8271872
 the filesystem was in hdb3.
the box cannot reboot now so i am using rescue-boot disk boot.  
gparted shows the old hdb3 as unallocated.

i use testdisk P to list file, nothing found.  i used parted to rescue from hdb3 start  sector to end sector.  it does not work.

i can use testdisk to mark it as L, LOGIC DISK.  

part 1,2,4 are ok.  have files in there.
what is next ?

---

### Post by oldfred on 2018-11-03
Post these, if drive is sda:
       sudo parted /dev/sda unit s print 
      
 sudo sfdisk -d /dev/sda

---

