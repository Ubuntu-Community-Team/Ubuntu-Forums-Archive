---
title: "Install in software Raid 0: mdadm needed"
date: 2021-12-06
forum: Installation &amp; Upgrades
---

### Post by leodp on 2021-12-06
Hi,
I'm trying to install Ubuntu 21.10 in a system with 2 SSD disks set up as RAID0.

I have already created an /dev/sda1 partition of 500MB to host /boot, plus a similarly sized /dev/sdb1  (same size for symmetry) as EFI space

In Ubuntu live I have connected to the WiFi, and installed:
```
sudo /apt-get update && apt-get install mdadm
```

to create a RAID 0 system with:
```
mdadm --create --verbose /dev/md127 --level=0 --raid-devices=2 /dev/sda2 /dev/sdb2
```


Now I'm stuck. When rebooting no sign of RAID0 disks.
I suppose I have 2 problems:

- mdadm is missing from the fresh installation. How to install mdadm also in the new system? The installer does not accept entries
- /dev/md127 is missing. Should I make it permanent (entry in/etc/fstab?)


Thanks for any help,
Leonardo

---

### Post by MAFoElffen on 2021-12-06
> **leodp said:**
> Now I'm stuck. When rebooting no sign of RAID0 disks.
I suppose I have 2 problems:

- mdadm is missing from the fresh installation. How to install mdadm also in the new system? The installer does not accept entries
- /dev/md127 is missing. Should I make it permanent (entry in/etc/fstab?)


Thanks for any help,
Leonardo
If you had installed 21.10 with RAIDx in the installer, during the installation, and indicated where the mount would be fopr it, it would have added that entry for it in the fstab for you...

Since you installed it manually, after the installation, (Yes) you have to manually add the mount to it to the fstab.

---

### Post by leodp on 2021-12-06
> **MAFoElffen said:**
> If you had installed 21.10 with RAIDx in the installer, during the installation, and indicated where the mount would be fopr it, it would have added that entry for it in the fstab for you...

Since you installed it manually, after the installation, (Yes) you have to manually add the mount to it to the fstab.

Thanks MAFoElffen. 
Yes, it's a bit more complicated than what I thought initially.

I had to start the live linux CD/USB, then partition the drives, install mdadm, create RAID0 partitions, ...
...well at the end it wouldn't have worked, because mdadm should be installed also in the freshly installed system (via chroot).

Luckily I found somebody which did almost the same thing and explained it.
Only difference: I am creating 2 partitions on the RAID0:
- one for /
- one for a LUKs encrypted filesystem, where I have my /home

Anyhow: here is the full explanation:
[https://forum.level1techs.com/t/how-to-install-ubuntu-20-04-to-linux-me-raid/154105]("https://forum.level1techs.com/t/how-to-install-ubuntu-20-04-to-linux-me-raid/154105")


The RAID0 seems to work. Photoediting with Rawtherapee is sensibly faster. hdparm read tests are as follows:
```

root@stufa:/home/casa# hdparm -tT /dev/mapper/md0p2_crypt

/dev/mapper/md0p2_crypt:
 Timing cached reads:   37514 MB in  2.00 seconds = 18785.39 MB/sec
 Timing buffered disk reads: 2278 MB in  3.00 seconds = 758.89 MB/sec


root@stufa:/home/casa# hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   35204 MB in  2.00 seconds = 17627.38 MB/sec
 Timing buffered disk reads: 476 MB in  1.17 seconds = 407.21 MB/sec


root@stufa:/home/casa# hdparm -tT /dev/sdc1

/dev/sdc1:
 Timing cached reads:   36136 MB in  2.00 seconds = 18095.86 MB/sec
 Timing buffered disk reads: 476 MB in  1.03 seconds = 460.48 MB/sec


```

Where:
/dev/mapper/md0p2_crypt is the encrypted RAID0 /home
/dev/sda1 is /boot/efi (no RAID, not encrypted) and 
/dev/sdc1 is /boot      (no RAID, not encrypted)

Hope that may help other people.

Leo

---

### Post by MAFoElffen on 2021-12-06
And curious about what was the root, "/"? That seems to be missing from that explanation...

---

### Post by leodp on 2021-12-07
> **MAFoElffen said:**
> And curious about what was the root, "/"? That seems to be missing from that explanation...

Yes, it was late.

```
root@stufa:/home/casa# mount|grep dev|grep md
/dev/md0p1 on / type ext4 (rw,relatime,errors=remount-ro,stripe=256)
/dev/mapper/md0p2_crypt on /home type ext4 (rw,relatime,stripe=256)


root@stufa:/home/casa# hdparm -tT /dev/mapper/md0p2_crypt 

/dev/mapper/md0p2_crypt:
 Timing cached reads:   44912 MB in  2.00 seconds = 22499.98 MB/sec
 Timing buffered disk reads: 2254 MB in  3.00 seconds = 750.92 MB/sec


root@stufa:/home/casa# hdparm -tT /dev/md0p1 

/dev/md0p1:
 Timing cached reads:   41446 MB in  2.00 seconds = 20760.62 MB/sec
 Timing buffered disk reads: 2434 MB in  3.00 seconds = 811.12 MB/sec

```



```
root@stufa:/home/casa# lsblk 
NAME                MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
loop0                 7:0    0     4K  1 loop  /snap/bare/5
loop1                 7:1    0  99,3M  1 loop  /snap/core/11743
loop2                 7:2    0 150,4M  1 loop  /snap/firefox/631
loop3                 7:3    0 242,3M  1 loop  /snap/gnome-3-38-2004/76
loop4                 7:4    0  54,2M  1 loop  /snap/snap-store/557
loop5                 7:5    0  61,8M  1 loop  /snap/core20/1169
loop6                 7:6    0  65,2M  1 loop  /snap/gtk-common-themes/1519
sda                   8:0    0 223,6G  0 disk  
&#9500;&#9472;sda1                8:1    0   477M  0 part  /boot/efi
&#9492;&#9472;sda2                8:2    0 223,1G  0 part  
  &#9492;&#9472;md0               9:0    0   446G  0 raid0 
    &#9500;&#9472;md0p1         259:0    0  27,9G  0 part  /
    &#9492;&#9472;md0p2         259:1    0   418G  0 part  
      &#9492;&#9472;md0p2_crypt 253:0    0   418G  0 crypt /home
sdb                   8:16   0   7,3T  0 disk  
sdc                   8:32   0 223,6G  0 disk  
&#9500;&#9472;sdc1                8:33   0 476,8M  0 part  /boot
&#9492;&#9472;sdc2                8:34   0 223,1G  0 part  
  &#9492;&#9472;md0               9:0    0   446G  0 raid0 
    &#9500;&#9472;md0p1         259:0    0  27,9G  0 part  /
    &#9492;&#9472;md0p2         259:1    0   418G  0 part  
      &#9492;&#9472;md0p2_crypt 253:0    0   418G  0 crypt /home
zram0               252:0    0 873,9M  0 disk  [SWAP]
zram1               252:1    0 873,9M  0 disk  [SWAP]
zram2               252:2    0 873,9M  0 disk  [SWAP]
zram3               252:3    0 873,9M  0 disk  [SWAP]
zram4               252:4    0 873,9M  0 disk  [SWAP]
zram5               252:5    0 873,9M  0 disk  [SWAP]
zram6               252:6    0 873,9M  0 disk  [SWAP]
zram7               252:7    0 873,9M  0 disk  [SWAP]
zram8               252:8    0 873,9M  0 disk  [SWAP]
zram9               252:9    0 873,9M  0 disk  [SWAP]
zram10              252:10   0 873,9M  0 disk  [SWAP]
zram11              252:11   0 873,9M  0 disk  [SWAP]
zram12              252:12   0 873,9M  0 disk  [SWAP]
zram13              252:13   0 873,9M  0 disk  [SWAP]
zram14              252:14   0 873,9M  0 disk  [SWAP]
zram15              252:15   0 873,9M  0 disk  [SWAP]

```

---

