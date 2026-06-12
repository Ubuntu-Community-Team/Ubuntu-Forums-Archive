---
title: "Moved root to xfs lv and having problems expanding"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by buppaclaus on 2010-03-23
Hi all,

Although I've been dabbling for a while I'm somewhat of a newbie so bear with me:

Rather than rebuild my Hardy Server due to root being full, I followed suggestions to create another logical volume on the volume group and put root there.

I must have missed some fundamental step.  Although the partition appears to be functional, the defined space isn't visible and I am stumped:

$sudo df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/mapper/vg--server1-lv--root
                       4582064   4533388         0 100% /
varrun                 1895524       248   1895276   1% /var/run
varlock                1895524         0   1895524   0% /var/lock
udev                   1895524       140   1895384   1% /dev
devshm                 1895524         0   1895524   0% /dev/shm
lrm                    1895524     42056   1853468   3% /lib/modules/2.6.24-24-generic/volatile
/dev/md2                482090    154435    302763  34% /boot
/dev/mapper/vg--server1-lv--tmp
                       5201536    141528   4797864   3% /tmp
/dev/mapper/vg--server1-lv--var
                       5201536    555088   4384304  12% /var
/dev/mapper/vg--server1-lv--srv
                     104031520    192252  98596388   1% /srv
/dev/mapper/vg--server1-lv--home
                     416126128 366913876  28243292  93% /home

$ sudo lvdisplay -v /dev/vg-server1/lv-root

    Using logical volume(s) on command line
  --- Logical volume ---
  LV Name                /dev/vg-server1/lv-root
  VG Name                vg-server1
  LV UUID                s4Dh7I-EXeD-x4BZ-p4Kj-RzIP-ps6X-hUN4Hx
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                15.00 GB
  Current LE             3840
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:4

---------------------------------------------------------------------------------

Here are the steps I followed to get to this point (or at least the steps I think I followed - these commands were between a few hundred others!):

1.. Create a logical Volume for root (I have several on the vg-server volume group already), and setup with xfs filesystem:

$ sudo lvcreate vg-server --name lv-root --size 15G
$ sudo mkfs -t xfs /dev/vg-server1/lv-root

2. Create mount point and mount:

$ sudo mkdir /mnt/new_root
$ sudo mount /dev/vg-server1/lv-root  /mnt/new_root

3. Copy everything from root, originally on /dev/md3 to the new logical volume

$ sudo cp -ax /. /mnt/new_root

4.  Expand the logical volume (4.4 Gyg was full so made it 15 Gyg, 1K Blocksize):
$ sudo xfs_growfs -D 15000000 /mnt/new_root/

5. Modify /etc/fstab:

## OLD
# UUID=b7583666-b305-4363-a4af-694641efcab4 /               ext3  
    relatime,errors=remount-ro 0       1
## NEW
/dev/vg-server1/lv-root                   /               xfs    relatime,errors=remount-ro 0       1

6.. Modify /boot/grub/menu.lst:
$ sudo vi /boot/grub/menu.lst
%s/root=\/\dev\/md3/root=\/\dev\/\vg-server\/lv-root
:wq

7. Restart.

I've been searching forums and the net without success - any help would be appreciated.

Thanks,
Buppaclaus.

---

### Post by dstew on 2010-03-23
I don't know a great deal about logical volumes, but I have played with them a little. I don't understand why, you would have to grow the file system in lv-root, since you specified the partition size as 15 GB when it was created. What was the indication that the filesystem was only 4.4 GB?

Also, I note that in the df output the names of the volume groups, and the logical volumes, have two hyphens in them: dev/mapper/vg--server1 for example, and lv--root. But, in the lvdisplay command, and the other commands, the argument names have only one hyphen in it, /dev/vg-server1/lv-root. Maybe that is just my ignorance, that the names are for different things. But it is something I saw. Is that OK?

---

### Post by buppaclaus on 2010-03-31
> **dstew said:**
> I don't know a great deal about logical volumes, but I have played with them a little. I don't understand why, you would have to grow the file system in lv-root, since you specified the partition size as 15 GB when it was created. What was the indication that the filesystem was only 4.4 GB?

Also, I note that in the df output the names of the volume groups, and the logical volumes, have two hyphens in them: dev/mapper/vg--server1 for example, and lv--root. But, in the lvdisplay command, and the other commands, the argument names have only one hyphen in it, /dev/vg-server1/lv-root. Maybe that is just my ignorance, that the names are for different things. But it is something I saw. Is that OK?

Hi Dstew,
Thanks for responding, and sorry it has taken so long to get back to you - The partition size is 15GB, yet the df returns:

/dev/mapper/vg--server1-lv--root
                       4582064   4533388         0 100% /

i.e. the lv-root partition is at 100% capacity, and there is nothing available.

I don't think the problem is the size of the partition, rather how much of the partition is visible and hence available.

Regarding the names, yes the volume group and logical volumes were all originally named with a single hyphen. I think the system "adds" these two names together to give the unique device name, and puts its own hyphen between the vg and lg names, escaping the user hyphens by doubling them up so that you can tell for instance that /var is volume group vg-server1 and logical volume lv-var rather than possibly volume group vg and logical volume server1-lv-var if the device name were just vg-server1-lv-var.

---

