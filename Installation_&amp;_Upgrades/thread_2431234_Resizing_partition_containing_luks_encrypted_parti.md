---
title: "Resizing partition containing luks encrypted partition with LVM?"
date: 2019-11-13
forum: Installation &amp; Upgrades
---

### Post by jay-7 on 2019-11-13
After deleting my windows partition, I have a complicated disk setup as follows:

Unallocate space  34 GB
/dev/sda3 <extended partition that contains my entire linux setup>
   /dev/sda5  ext4 <boot> 300 MB
   /dev/sda6  cryptsetup decrypted at boot partition, which has LVM inside for my swap and root partitions as follows.

summetj@witchblade:~$ sudo pvs
  PV                 VG     Fmt  Attr PSize   PFree
  /dev/mapper/crypt6 vgpool lvm2 a--  197.62g    0 
summetj@witchblade:~$ sudo vgs
  VG     #PV #LV #SN Attr   VSize   VFree
  vgpool   1   2   0 wz--n- 197.62g    0 
summetj@witchblade:~$ sudo lvs
  LV   VG     Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root vgpool -wi-ao---- 194.62g                                                    
  swap vgpool -wi-ao----   3.00g 


I would like to absorb the unallocated 34 GB freed up from deleting my windows partition into the root logical volume inside the /dev/sda6 cryptsetup encrypted partition, which is inside the /dev/sda3 physical partition..... see the fun I'm attempting?
[If you want to see how I got into this situation in the first place, see [https://www.summet.com/blog/2016/11/26/installing-an-encrypted-partition-with-lvm-dual-boot-on-ubuntu-16-04/](https://www.summet.com/blog/2016/11/26/installing-an-encrypted-partition-with-lvm-dual-boot-on-ubuntu-16-04/) ]

It seems to me that I SHOULD be able to do something along the lines of:
1. Expand the /dev/sda3 physical partition to take up the entire drive, including unallocated space.
2. Move the /dev/sda5 boot partition to the top of the newly enlarged /ev/sda3 physical partition.
2a. re-run update-grub to re-link to the right disk sectors for booting....

3. Enlarge /dev/sda6 (the encrypted virtual partition) to take advantage of the extra space in /dev/sda3
4. Either enlarge my PV, or add a 2nd PV inside /dev/sda6 to the VG
5. Enlarge the VG/ LV root.

Steps 3,4,5 are conceptually possible, but I don't know the commands / options to do them, and was wondering if anybody who did a lot of work with both encrypted parttions and LVM could give me some pointers (or tell me it isn't possible....)

[The other option is to blow everything away and use Ubuntu's full disk LVM install option and then restore from backups...but why copy all of that data if I don't have to, right?]

Thanks,
Jay

---

### Post by jay-7 on 2019-11-13
To answer my own question...this excellent wiki tells all!
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

