---
title: "Specific partitioning LUKS + LVM not succeeding"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by Anakinholland on 2014-08-26
Hi all,

I'm trying to do the following using 14.04 LTS:

To use in my business, using encrypted LVM preferrably, I would like something like the following (I know the details don't add up, it's a mock-up to give you an impression):

```
sda                            8:0    0 167,7G  0 disk  
&#9500;&#9472;sda1                         8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                         8:2    0     1K  0 part  
&#9492;&#9472;sda5                         8:5    0 150,5G  0 part  
  &#9492;&#9472;sda5_crypt (dm-0)        252:0    0 150,5G  0 crypt 
    &#9500;&#9472;ubun--vg-root (dm-1)   252:1    0  20,8G  0 lvm   /
    &#9500;&#9472;ubun--vg-virt (dm-1)   252:1    0 115,0G  0 lvm   /virtual
    &#9492;&#9472;ubun--vg-home (dm-2)   252:2    0  15,0G  0 lvm   /home   
&#9492;&#9472;sda6                         8:5    0   7,7G  0 part  
  &#9492;&#9472;sda6_crypt (dm-0)        252:0    0   7,7G  0 crypt     
    &#9492;&#9472;ubun--vg-swap_1 (dm-2) 252:2    0   7,7G  0 lvm   [SWAP]
```

I would like the /virtual to be XFS filesystem, as apparently there's a big speed-increase to be had for big files (which virtual machines are to the host).

I've tried the various forms I can think of, but:

When I use automatic partitioning it only makes 1 VG and creats 1 big filesystem / 
When I manually partition in the installer, I cannot create multiple LV's in a single VG. Each LV needs to be on it's own Physical Volume.
When I manually partiion in the installer without LVM, all filesystems on separate encrypted partitions, it fails at creating/mounting the XFS filesystem.
When I manually partition using parted, then assign in the installer, it fails to copy the dm-crypt.ko into the bootloader (the file is physically not present in /boot/lib) and does not create /etc/crypttab

I tried the same thing with Xubuntu, ZorinOS and Mint, but all suffer from the same symptoms (which makes sense of course). 
I tried setting up the same thing with RH-based distros, and succeed, but they are either too far behind software-wise or don't have an LTS release...

Any help with this would be greatly appreciated!

---

### Post by Anakinholland on 2014-08-26
Update: I managed to follow the "manually partiion in the installer  without LVM, all filesystems on separate encrypted partitions" but  replace XFS with ext4, no errors, purring like a kitten. Setup:

```
NAME                    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                       8:0    0 167,7G  0 disk  
&#9500;&#9472;sda1                    8:1    0   476M  0 part  /boot/efi
&#9500;&#9472;sda2                    8:2    0   238M  0 part  /boot
&#9500;&#9472;sda3                    8:3    0     1K  0 part  
&#9500;&#9472;sda5                    8:5    0  18,6G  0 part  
&#9474; &#9492;&#9472;sda5_crypt (dm-0)   252:0    0  18,6G  0 crypt /
&#9500;&#9472;sda6                    8:6    0    14G  0 part  
&#9474; &#9492;&#9472;sda6_crypt (dm-2)   252:2    0    14G  0 crypt /home
&#9500;&#9472;sda7                    8:7    0 125,7G  0 part  
&#9474; &#9492;&#9472;sda7_crypt (dm-3)   252:3    0 125,7G  0 crypt /virtual
&#9492;&#9472;sda8                    8:8    0   7,5G  0 part  
  &#9492;&#9472;sda8_crypt (dm-1)   252:1    0   7,5G  0 crypt [SWAP]

root@schuldiner:~# mount |grep -E "sda|mapper"
/dev/mapper/sda5_crypt on / type ext4 (rw,errors=remount-ro)
/dev/sda2 on /boot type ext2 (rw)
/dev/sda1 on /boot/efi type vfat (rw)
/dev/mapper/sda6_crypt on /home type ext4 (rw)
/dev/mapper/sda7_crypt on /virtual type ext4 (rw)
/dev/mapper/truecrypt1 on /media/truecrypt1 type ext4 (rw)
```

Will try tomorrow and see if I can just re-format sda7_crypt to XFS. Need to tune fstab for SSD anyway.

---

### Post by Anakinholland on 2014-08-27
The setup described in previous post is seriously unwanted. It required me to enter my encryption password 4 times at every boot...

For elimination's sake I've followed (part of, used parted instead of fdisk) [this procedure]("https://help.ubuntu.com/community/UbuntuDesktopLVM") without the encryption, and the LVM boots fine:

```
lsblk

NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                         8:0    0 167,7G  0 disk 
&#9500;&#9472;sda1                      8:1    0   476M  0 part /boot/efi
&#9500;&#9472;sda2                      8:2    0   238M  0 part /boot
&#9500;&#9472;sda3                      8:3    0 157,6G  0 part 
&#9474; &#9500;&#9472;vg_root-lvroot (dm-0) 252:0    0    20G  0 lvm  /
&#9474; &#9500;&#9472;vg_root-lvhome (dm-1) 252:1    0    15G  0 lvm  /home
&#9474; &#9492;&#9472;vg_root-lvvirt (dm-2) 252:2    0 122,6G  0 lvm  /virt
&#9500;&#9472;sda4                      8:4    0     1K  0 part 
&#9492;&#9472;sda5                      8:5    0   7,5G  0 part [SWAP]

mount | grep vg_root

/dev/mapper/vg_root-lvroot on / type ext4 (rw,errors=remount-ro)
/dev/mapper/vg_root-lvvirt on /virt type xfs (rw)
/dev/mapper/vg_root-lvhome on /home type ext4 (rw)

grep -vE "^#|^$" /etc/fstab

/dev/mapper/vg_root-lvroot /               ext4    errors=remount-ro 0       1
UUID=8954e7e2-cb49-406c-b830-34f6307d0e9c /boot           ext2    defaults        0       2
UUID=CBDC-9CA6  /boot/efi       vfat    defaults        0       1
/dev/mapper/vg_root-lvhome /home           ext4    defaults        0       2
/dev/mapper/vg_root-lvvirt /virt           xfs     defaults        0       2
UUID=09f3972b-ea2a-465f-9197-c2bb243b312c none            swap    sw              0       0
```

Hoorah!

So, now to try once again wíth encryption.

***sidenote:** /dev/sda4 is the extended partition on which the logical partition /dev/sda5 resides.*

---

### Post by Anakinholland on 2014-08-28
In the end, I managed to solve it by using the default install and then edit the LVM from a LiveCD-session:

```
root@schuldiner:~# lsblk /dev/sda
NAME                             MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                                8:0    0 167,7G  0 disk  
&#9500;&#9472;sda1                             8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                             8:2    0   244M  0 part  /boot
&#9492;&#9472;sda3                             8:3    0   167G  0 part  
  &#9492;&#9472;sda3_crypt (dm-0)            252:0    0   167G  0 crypt 
    &#9500;&#9472;xubuntu--vg-root (dm-1)    252:1    0    20G  0 lvm   /
    &#9500;&#9472;xubuntu--vg-swap_1 (dm-2)  252:2    0   7,9G  0 lvm   [SWAP]
    &#9500;&#9472;xubuntu--vg-home (dm-3)    252:3    0    15G  0 lvm   /home
    &#9492;&#9472;xubuntu--vg-virtual (dm-4) 252:4    0 124,1G  0 lvm   /virtual
```

From the LiveCD I had to 


[LIST]
[*]open the VG (cryptsetup luksOpen) 
[*]unmount the LV "root" 
[*]resize filesystem, thén partition 
[*]mount it again as /media/something. 
[*]create the 2 new LVs "home" and "virtual", put a filesystem on them 
[*]have "home" mounted as /media/somethingelse 
[*]Copy/move the home-directory of the user you made from /media/something to /media/somethingelse. 
[/LIST]

Next, chroot to filesystem "root", and edit /etc/fstab

```
root@schuldiner:~# grep mapper /etc/fstab
/dev/mapper/xubuntu--vg-root /                       ext4    errors=remount-ro 0       1
/dev/mapper/xubuntu--vg-home /home                   ext4    errors=remount-ro 0       1
/dev/mapper/xubuntu--vg-virtual /virtual                   xfs        defaults          0       1
/dev/mapper/xubuntu--vg-swap_1 none                    swap    sw              0       0

```
Please note I still have to optimize them for SSD, plus you don't really need /home remounted as read-only.

The crypttab does not change (as it only holds the PV parition

```
root@schuldiner:~# cat /etc/crypttab
sda3_crypt UUID=7f1e5c60-407c-4a79-8764-76347e0e814f none luks,discard
```

I still don't consider it "SOLVED" per se, I would expect the installer to support a setup like mine as it doesn't really seem far-fetched? 

**edit:** [created a bug-report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1362758").

Cheers,

Anakin

---

