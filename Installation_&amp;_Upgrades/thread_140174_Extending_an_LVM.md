---
title: "Extending an LVM"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by Nate53085 on 2006-03-05
I'm trying to extend my root partition in LVM.  I have:

1)Installed Ubuntu, during partitioning told it to use LVM (250G drive)
2)Installed a 2nd 250G drive
3)   pvcreate /dev/hdb (second harddrive)
      vgextend Ubuntu /dev/hdb
      lvextend -L+235G /dev/Ubuntu/root

4) lvs says:

LV     VG     Attr   LSize   Origin Snap%  Move Copy%
root   Ubuntu -wi-ao 464.14G
swap_1 Ubuntu -wi-ao   1.38G

5) vgs says:

VG     #PV #LV #SN Attr  VSize   VFree
Ubuntu   2   2   0 wz--n 465.53G    0

6) file root claims:
root: symbolic link to `/dev/mapper/Ubuntu-root'

7) mount claims:
/dev/mapper/Ubuntu-root on / type ext3 (rw,errors=remount-ro)

8.) df claims:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/Ubuntu-root
                     238688872   3206472 223357628   2% /
tmpfs                   258244         0    258244   0% /dev/shm
tmpfs                   258244     12588    245656   5% /lib/modules/2.6.12-10-3 86/volatile
/dev/hda1               233335     19162    201725   9% /boot

I am confused...the root partition is extended correctly, and that the symlink to Ubuntu-root is correct. Why is Ubuntu-root not the full (approximately) 500G?  Any help would be greatly appreciated.

---

### Post by roshan.s on 2006-03-05
You need to resize the actual filesystem that lives on the LV. Use the resize2fs command to do this (it also works on ext3). E.g. "resize2fs /dev/Ubuntu/root" will resize the filesystem to fill the partition.

IMPORTANT: It is best to run this command on an unmounted filesystem. While this might work on a mounted partition, its fairly uncertain. Since you're trying to resize your root filesystem, you need to either do it from the live CD (make sure root is really unmounted) or from the rescue mode on the install CD.

---

### Post by Nate53085 on 2006-03-05
Just tried that, it tells me:

couldn't find valid filesystem superblock

Also, I just realized that umount /dev/mapper/Ubuntu-root DIDN'T unmount the FS while in recue mode.  I was required to mount a fs in order to run in rescue mode, and Ubuntu-root was the only one I could mount.  I'm confused...


Edit::

Okay, this is how it worked.

Boot live cd
open a terminal
sudo e2fsck -f /dev/Ubuntu/root
sudo resize2fs /dev/Ubuntu/root

and it worked,  thanx alot for your help.  I really appreciate it.

---

