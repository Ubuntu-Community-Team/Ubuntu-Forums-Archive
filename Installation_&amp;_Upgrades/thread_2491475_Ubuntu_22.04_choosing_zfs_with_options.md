---
title: "Ubuntu 22.04 choosing zfs with options"
date: 2023-10-10
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2023-10-10
Installed the 22.04 with zfs. I applied  crypto with an intention to also apply compression but not yet.  I ended up with a working system.


```

sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
[sudo] password for robins: 
NAME        FSTYPE    SIZE MOUNTPOINT                            LABEL
(21 loops removed from the following)
sda                 698.6G                                       
&#9500;&#9472;sda1      ext4    645.1G /media/robins/hitachi 750gb           hitachi 750gb
&#9492;&#9472;sda2      ext4     53.6G /media/robins/Deju_dup_backup         Deju_dup_backup
sdb                 232.9G                                       
&#9500;&#9472;sdb4                  1K                                       
&#9500;&#9472;sdb5      ext4     88.4G /media/robins/mydocs                  mydocs
&#9500;&#9472;sdb6      ext4      105G /media/robins/Data inc AV             Data inc AV
&#9492;&#9472;sdb7      swap     39.5G                                       
sdc                 465.8G                                       
&#9500;&#9472;sdc1      ext4    215.2G /media/robins/32677e49-0894-4d3f-8cc4 
&#9492;&#9472;sdc2      ext4    250.6G /media/robins/bacac64a-73be-47fe-87a8 
sdd                  28.7G                                       
&#9492;&#9472;sdd1               28.7G                                       
zd0         crypto_   500M                                       
&#9492;&#9472;keystore-rpool
            ext4      484M /run/keystore/rpool                   keystore-rpool
nvme0n1             931.5G                                       
&#9500;&#9472;nvme0n1p1 vfat      512M /boot/efi                             
&#9500;&#9472;nvme0n1p2 crypto_     2G                                       
&#9474; &#9492;&#9472;cryptoswap
&#9474;           swap        2G [SWAP]                                cryptoswap
&#9500;&#9472;nvme0n1p3 zfs_mem     2G                                       bpool
&#9492;&#9472;nvme0n1p4 zfs_mem   927G                                       rpool
```
robins@robins-MS-7C96:~$

When I installed 22.04 I had set up home within nvme0n1. I did not want to do it, as I prefer to have home as a separate partition. 

Nautilus shows Home within the user robins. 

I want to restore the previous file data in .thunderbird and .mozilla which I have in a previous backup via deja dup. 

I am beginning to think that the system is not looking at the  /home folder I can see,  but instead is getting the config  files that may be in one of the partitions in nvmeon1.  I can not open any of them because I get Unable to access location eg:

```
Error mounting /dev/nvme0n1p4 at /media/robins/rpool: unknown filesystem type 'vfs_member'

```
Are users Settings incomplete? User  reports only one user "robins":  "the account is using special settings that have been defined manually, use advanced settings to tune them."

Advanced settings show:

```
Home dir /home/robins
main group robins
ID 1000
```

robins  shows: robins administrator and/or  desktop user boxes not ticked but:

```
$groups robins
robins : robins adm sudo dip plugdev lpadmin lxd sambashare vboxusers
```

So far I have not found an fstab that looks relevant to my current setup. I think I have found an earlier fstab that does not seem to relate to  zfs partitions. Does this point to the active  current fstab  being in /dev/nvme0n1p4? If so as mentioned above  I can not manually open  1p4 to see what is in there.

What is my next step?

---

### Post by #&amp;thj^% on 2023-10-10
Mine:
```
zfs list rpool/USERDATA/me_y52lko
NAME                       USED  AVAIL     REFER  MOUNTPOINT
rpool/USERDATA/me_y52lko  7.51G   206G     4.37G  /home/me

```
Robbyx please use code tags, this is not the first time we have had to ask either.
Until you fix your first post with correct tags, I'll not not support you here. (No offense meant it's just time to use the right tags)
You can manually use them like so:
```
[noparse][code]
your copied return

```[/noparse][/code]

---

### Post by MAFoElffen on 2023-10-10
+1

Or use the Advanced Editor (go advanced, adv reply, etc), select the text and use the "#" Icon from the extended tool bar to insert the Codes Tags for you... 

Will address this after that edit is done.

---

### Post by Robbyx on 2023-10-10
Did you notice that I put a comment into the posting saying that I could not see any display options? Thank you for pointing out they were in the advanced editor.

---

### Post by #&amp;thj^% on 2023-10-10
> **Robbyx said:**
> Does this point to the active  current fstab  being in /dev/nvme0n1p4? If so as mentioned above  I can not manually open  1p4 to see what is in there.

What is my next step?
IJDK yet lets peek here real quick:
```
ls -a
.              .dbus           .gtkrc-2.0     rtl8812au
..             Desktop         .hardinfo      .sudo_as_admin_successful
.asoundrc      .dmrc           .ICEauthority  surfshark-install.sh
.bash_aliases  Documents       .lesshst       Templates
.bash_history  Downloads       .local         .themes
.bash_logout   .face           .mozilla       .thumbnails
.bashrc        .fonts          Music          .var
.cache         .gksu.lock      Pictures       Videos
.cargo         .gnome          .pki           .Xauthority
.config        .gnupg          .profile       .xsession-errors
.conky         .gtk-bookmarks  Public         .xsession-errors.old

```

---

### Post by Robbyx on 2023-10-10
```
robins@robins-MS-7C96:~$ ls -a
 .          .bash_history   .cache    Documents   .lesshst   .mozilla   .profile   .ssh                        .thunderbird
 ..         .bash_logout    .config   Downloads   .local     Music      Public     .sudo_as_admin_successful   Videos
 .anydesk   .bashrc         Desktop   .gnupg      mkdir      Pictures   snap       Templates                  'VirtualBox VMs'
robins@robins-MS-7C96:~$
```

---

### Post by MAFoElffen on 2023-10-10
LOL. See, you are in your Home... Now lets explain a few things and dig a little deeper.
```

echo $HOME
sudo zfs list

```
Please post the result of those within CODE Tags.

Now let's explain a few things.

ZFS mounts are internal to the pools and datasets. They do not show up in the ftsab. Look at this output of my server:
```

mafoelffen@Mikes-B460M:~$ grep -v '#' /etc/fstab
UUID=0150-726C  /boot/efi       vfat    umask=0022,fmask=0022,dmask=0022      0       1
/boot/efi/grub    /boot/grub    none    defaults,bind    0    0
UUID=71d7e96b-af7f-40de-b145-d93873c4f0bb    none    swap    sw    0    0

```
That is the complete /etc/fstab file on that computer. 3 lines. Three mounts. Those three filesystems are the only filesystems on that machine that are not in pools and 'other than' a ZFS filesystem. So where it the rest of the filesystem and it's mounts?

They are here:
```

mafoelffen@Mikes-B460M:~$ sudo zfs list
[sudo] password for mafoelffen: 
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              297M  1.46G       96K  /boot
bpool/BOOT                                         295M  1.46G       96K  none
bpool/BOOT/ubuntu_2cwpns                           295M  1.46G      295M  /boot
datapool                                           978G  3.77T      307K  /data
datapool/DATA                                      978G  3.77T      307K  none
datapool/DATA/ubuntu_2cwpns                        978G  3.77T     10.0G  /data
datapool/DATA/ubuntu_2cwpns/ISO                    418G  3.77T      418G  /data/ISO
datapool/DATA/ubuntu_2cwpns/KVM-VM                 551G  3.77T      551G  /data/KVM-VM
kpool                                             1.56T  1.85T      279K  /KVM_Pool
kpool/KVM                                         1.56T  1.85T      279K  none
kpool/KVM/ubuntu_2cwpns                           1.56T  1.85T     1.56T  /KVM_Pool
rpool                                             18.9G   873G       96K  /
rpool/ROOT                                        14.9G   873G       96K  none
rpool/ROOT/ubuntu_2cwpns                          14.9G   873G     6.80G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   873G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   873G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   873G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      8.10G   873G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   873G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  7.82G   873G     7.31G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   873G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    172K   873G      172K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt               474M   873G      474M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             47.9M   873G     47.9M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   285M   873G      285M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   873G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.54M   873G     1.54M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 112K   873G      112K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   873G       96K  /var/www
rpool/USERDATA                                    3.94G   873G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  3.93G   873G     3.93G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        3.03M   873G     3.03M  /root

```
You see the mounts and how it is put together? To see just the mounts, we can also just return that value and the compression set for those...
```
mafoelffen@Mikes-B460M:~$ sudo zfs list -r -o name,mountpoint,compressratio,compress
NAME                                              MOUNTPOINT                RATIO  COMPRESS
bpool                                             /boot                     1.04x  lz4
bpool/BOOT                                        none                      1.04x  lz4
bpool/BOOT/ubuntu_2cwpns                          /boot                     1.04x  lz4
datapool                                          /data                     1.25x  lz4
datapool/DATA                                     none                      1.25x  lz4
datapool/DATA/ubuntu_2cwpns                       /data                     1.25x  lz4
datapool/DATA/ubuntu_2cwpns/ISO                   /data/ISO                 1.04x  lz4
datapool/DATA/ubuntu_2cwpns/KVM-VM                /data/KVM-VM              1.42x  lz4
kpool                                             /KVM_Pool                 1.24x  lz4
kpool/KVM                                         none                      1.24x  lz4
kpool/KVM/ubuntu_2cwpns                           /KVM_Pool                 1.24x  lz4
rpool                                             /                         1.41x  lz4
rpool/ROOT                                        none                      1.49x  lz4
rpool/ROOT/ubuntu_2cwpns                          /                         1.49x  lz4
rpool/ROOT/ubuntu_2cwpns/srv                      /srv                      1.00x  lz4
rpool/ROOT/ubuntu_2cwpns/usr                      /usr                      1.00x  lz4
rpool/ROOT/ubuntu_2cwpns/usr/local                /usr/local                1.01x  lz4
rpool/ROOT/ubuntu_2cwpns/var                      /var                      1.42x  lz4
rpool/ROOT/ubuntu_2cwpns/var/games                /var/games                1.00x  lz4
rpool/ROOT/ubuntu_2cwpns/var/lib                  /var/lib                  1.32x  lz4
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService  /var/lib/AccountsService  1.00x  lz4
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager   /var/lib/NetworkManager   1.03x  lz4
rpool/ROOT/ubuntu_2cwpns/var/lib/apt              /var/lib/apt              1.28x  lz4
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             /var/lib/dpkg             2.58x  lz4
rpool/ROOT/ubuntu_2cwpns/var/log                  /var/log                  4.31x  lz4
rpool/ROOT/ubuntu_2cwpns/var/mail                 /var/mail                 1.00x  lz4
rpool/ROOT/ubuntu_2cwpns/var/snap                 /var/snap                 2.84x  lz4
rpool/ROOT/ubuntu_2cwpns/var/spool                /var/spool                1.03x  lz4
rpool/ROOT/ubuntu_2cwpns/var/www                  /var/www                  1.00x  lz4
rpool/USERDATA                                    /                         1.11x  lz4
rpool/USERDATA/mafoelffen_gtg9x1                  /home/mafoelffen          1.11x  lz4
rpool/USERDATA/root_gtg9x1                        /root                     3.72x  lz4

```
You can set or change the compression method via the 'zfs set' command, if it is not set. It will not chnage what is already written, but will apply for anyhting new written to it. If you want to completely compress something, just like you would encrypt something that already exists, than back up just the data > delte what is there, and rewrite it fresh...

Now let's look deeper into this, and you will see that it is even more complex than you have seen so far:
```

mafoelffen@Mikes-B460M:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME        LABEL      SIZE FSTYPE     MOUNTPOINT MODEL
sda                    1.8T                       Samsung SSD 870 EVO 2TB
&#9492;&#9472;sda1      datapool   1.8T zfs_member            
sdb                    1.8T                       Samsung SSD 870 EVO 2TB
&#9492;&#9472;sdb1      datapool   1.8T zfs_member            
sdc                    1.8T                       Samsung SSD 870 EVO 2TB
&#9492;&#9472;sdc1      datapool   1.8T zfs_member            
sdd                  476.9G                       Crucial_CT512MX100SSD1
&#9500;&#9472;sdd1                  16M ext4                  
&#9500;&#9472;sdd2               476.3G ntfs                  
&#9492;&#9472;sdd3                 607M ntfs                  
sde                    1.8T                       Samsung SSD 870 EVO 2TB
&#9492;&#9472;sde1      datapool   1.8T zfs_member            
sdf                    1.8T                       Samsung SSD 870 EVO 2TB
&#9492;&#9472;sdf1      datapool   1.8T zfs_member            
nvme3n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme3n1p1 kpool      1.8T zfs_member            
nvme4n1              931.5G                       WD Blue SN570 1TB
&#9500;&#9472;nvme4n1p1            512M vfat       /boot/efi  
&#9500;&#9472;nvme4n1p2              2G swap       [SWAP]     
&#9500;&#9472;nvme4n1p3 bpool        2G zfs_member            
&#9492;&#9472;nvme4n1p4 rpool      927G zfs_member            
nvme1n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme1n1p1 kpool      1.8T zfs_member            
nvme6n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme6n1p1 datapool  1000G zfs_member            
nvme0n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme0n1p1 kpool      1.8T zfs_member            
nvme2n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme2n1p1 kpool      1.8T zfs_member            
nvme5n1     datapool   1.8T zfs_member            Samsung SSD 970 EVO 2TB
&#9500;&#9472;nvme5n1p1            1.3T zfs_member            
&#9492;&#9472;nvme5n1p2 datapool    10G zfs_member            
mafoelffen@Mikes-B460M:~$ sudo zpool status -v
  pool: bpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:00 with 0 errors on Sun Oct  8 00:24:01 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    bpool                                   ONLINE       0     0     0
      0196ab45-3ee2-894e-b725-39560409109f  ONLINE       0     0     0

errors: No known data errors

  pool: datapool
 state: ONLINE
  scan: resilvered 4.74G in 00:00:16 with 0 errors on Sun Oct  8 22:40:33 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

  pool: kpool
 state: ONLINE
  scan: scrub repaired 0B in 00:08:49 with 0 errors on Sun Oct  8 00:32:50 2023
config:

    NAME                                 STATE     READ WRITE CKSUM
    kpool                                ONLINE       0     0     0
      raidz2-0                           ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1  ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1  ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1  ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:14 with 0 errors on Sun Oct  8 00:24:16 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    rpool                                   ONLINE       0     0     0
      ae13efaa-d1cf-ec40-86a6-2883f0e07102  ONLINE       0     0     0

errors: No known data errors

```
6 SSD SATA drives and 7 NVMe M.2 drives... 13 drives, joined as 1 system. But only 3 lines in the fstab file. Understand now? Grub points to rpool as it's root drive, then all the ZFS mounts are applied, then the mounts in the fstab file...

If you want, I could show you more, on my other computers that are a bit more complex... Its really easy when you just undesrtand how ZFS handles it's internal mounts, how they work, and how flexible they can be.

---

### Post by MAFoElffen on 2023-10-10
You can still add another pool for your home, temporarily mounted to /mnt, and rsync the contents to it... I have two other machines here that are ZFS with separate pools for home, that I can show you as examples.

---

### Post by Robbyx on 2023-10-11
Thank you for the detailed explanation so far. It has clarified what is going on. 

Here are the further commands you asked me to run:

```
robins@robins-MS-7C96:~$ echo $HOME
/home/robins
robins@robins-MS-7C96:~$ sudo zfs list
[sudo] password for robins: 
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              287M  1.47G       96K  /boot
bpool/BOOT                                         286M  1.47G       96K  none
bpool/BOOT/ubuntu_d0ne3j                           286M  1.47G      286M  /boot
rpool                                             19.0G   872G      192K  /
rpool/ROOT                                        10.1G   872G      192K  none
rpool/ROOT/ubuntu_d0ne3j                          10.1G   872G     4.81G  /
rpool/ROOT/ubuntu_d0ne3j/srv                       192K   872G      192K  /srv
rpool/ROOT/ubuntu_d0ne3j/usr                       948K   872G      192K  /usr
rpool/ROOT/ubuntu_d0ne3j/usr/local                 756K   872G      756K  /usr/local
rpool/ROOT/ubuntu_d0ne3j/var                      5.26G   872G      192K  /var
rpool/ROOT/ubuntu_d0ne3j/var/games                 192K   872G      192K  /var/games
rpool/ROOT/ubuntu_d0ne3j/var/lib                  5.20G   872G     5.04G  /var/lib
rpool/ROOT/ubuntu_d0ne3j/var/lib/AccountsService   212K   872G      212K  /var/lib/AccountsService
rpool/ROOT/ubuntu_d0ne3j/var/lib/NetworkManager    388K   872G      388K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_d0ne3j/var/lib/apt               106M   872G      106M  /var/lib/apt
rpool/ROOT/ubuntu_d0ne3j/var/lib/dpkg             58.7M   872G     58.7M  /var/lib/dpkg
rpool/ROOT/ubuntu_d0ne3j/var/log                  51.9M   872G     51.9M  /var/log
rpool/ROOT/ubuntu_d0ne3j/var/mail                  192K   872G      192K  /var/mail
rpool/ROOT/ubuntu_d0ne3j/var/snap                 4.85M   872G     4.85M  /var/snap
rpool/ROOT/ubuntu_d0ne3j/var/spool                 308K   872G      308K  /var/spool
rpool/ROOT/ubuntu_d0ne3j/var/www                   192K   872G      192K  /var/www
rpool/USERDATA                                    8.44G   872G      192K  /
rpool/USERDATA/robins_6f9kyf                      8.44G   872G     8.44G  /home/robins
rpool/USERDATA/root_6f9kyf                         920K   872G      920K  /root
rpool/keystore                                     518M   873G     63.4M  -
robins@robins-MS-7C96:~$ 

```

---

### Post by MAFoElffen on 2023-10-11
> **Robbyx said:**
> Thank you for the detailed explanation so far. It has clarified what is going on. 

Here are the further commands you asked me to run:

```
robins@robins-MS-7C96:~$ echo $HOME
/home/robins

robins@robins-MS-7C96:~$ sudo zfs list
...
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
rpool/USERDATA                                    8.44G   872G      192K  /
rpool/USERDATA/robins_6f9kyf                      8.44G   872G     8.44G  /home/robins
...

```
There you go.

What I would do, even if you do not create a separate home on another partition, is to change your mountpoint for your home from /home/robins to /home, then create a new folder inside that with your username in that folder to move all your contents into... Then rename that dataset to /rpool/USERDATA/home.

The reason for that, is that the way the dataset is mounted is not currently wrong... But if you create another user, that user's home folder will exist out of a dataset, unless you first create a another new dataset especially for that user. If you just change the mountpoint for that and move the files and folders to adjust for that, then all the user home directories automatically are created within that dataset. (No extra work for you.) Does that make sense?

But you are planning to create another pool for a separate home right? Sort of the same concept. You are just moving data, and resetting mount points.

---

### Post by #&amp;thj^% on 2023-10-11
> **MAFoElffen said:**
>  If you just change the mountpoint for that and move the files and folders to adjust for that, then all the user home directories automatically are created within that dataset. (No extra work for you.) Does that make sense?

But you are planning to create another pool for a separate home right? Sort of the same concept. You are just moving data, and resetting mount points.
Just doesn't get any better than that. MAFoElffen is our encyclopedia on ZFS.

---

### Post by Robbyx on 2023-10-11
Of course thank you for your advice. 

Will your suggestion prevent the destruction of the /home partition  on  a reinstall?

My intention was not to create another user, but I do wish to be able to access rpool to save files.  Currently I am not being allowed to open the rpool with Nautilus. I have installed Nautilus-admin but "open as administrator"  is not an option that appears when I right click rpool. I tried to add a new right to my admin user powers but it is being refused. I have looked at my rights to create, delete files and access files in Home. I have those permissions, but they do not seem to be working. Is it something to do with the manually created  rights that I indicated in an earlier message here?

I have been dithering about how to set everything up under zfs. This is my roadmap:


Restore from deja_dup, old data  and hidden files to the  existing rpool 
After the restore  turn rpool into a mirror vdev using 3 drives?

These are the drives I have available:

> Existing nvme0n1p4  rpool as now              927gb
sda  (hd)                                                         700gb
sdb (nvme)                                                     250gb
sdc  (hd)                                                         465gb
External USB HD                                        2,000gb


About the External HD, can I turn it  off or remove the External HD without ruining the 3 vdev mirror? 


I gather that instead of whole drives I can use partitions although I have read that I should have unallocated space between partitions and I should install some intermediate vdev  to do with interfacing fast and slow drives together.

---

### Post by MAFoElffen on 2023-10-12
Let's change your perspective... rpool is mounted at root---> "/"... bpool is mounted at "/boot". When you use nautilus, you access the files system. You navigate to "/". You navigate to "/boot".

The pools and datasets are there, under the filesystem... They are storage containers, and they just work. Nautilus does not know how to read then directly, but it does need to... That would be like trying to write to a partition, between the partiton and the filesystem layers. That is not how things work logically. But as whatever user, you can read and write to the filesystem. Right?

Let my show you this:
```

mafoelffen@msi-ubuntu:~$ sudo zfs list
NAME                                             USED  AVAIL     REFER  MOUNTPOINT
bpool                                            690M  1.95G      192K  /boot
bpool/BOOT                                       688M  1.95G      192K  none
bpool/BOOT/ubuntu_2204                           688M  1.95G      688M  /boot
dpool                                           2.93M   450G       96K  /dpool
dpool/DATA                                       192K   450G       96K  none
dpool/DATA/ubuntu_2204                            96K   450G       96K  /dpool
hpool                                           2.58G   344G      192K  /home
hpool/USERDATA                                  2.58G   344G      192K  none
hpool/USERDATA/ubuntu_2204                      2.58G   344G     2.58G  /home
kpool                                            406G   493G       96K  /kpool
kpool/QEMU-KVM                                   406G   493G       96K  none
kpool/QEMU-KVM/ubuntu_2204                       406G   493G      104K  /kpool
kpool/QEMU-KVM/ubuntu_2204/ISO                   406G   493G      406G  /kpool/ISO
kpool/QEMU-KVM/ubuntu_2204/KVM-VM                 96K   493G       96K  /kpool/KVM-VM
kpool/QEMU-KVM/ubuntu_2204/images                112K   493G      112K  /var/lib/libvirt/images
kpool/QEMU-KVM/ubuntu_2204/libvirt               620K   493G      620K  /etc/libvirt/
rpool                                           17.6G   707G      192K  /
rpool/ROOT                                      17.5G   707G      192K  none
rpool/ROOT/ubuntu_2204                          17.5G   707G     7.93G  /
rpool/ROOT/ubuntu_2204/srv                       192K   707G      192K  /srv
rpool/ROOT/ubuntu_2204/usr                       488K   707G      192K  /usr
rpool/ROOT/ubuntu_2204/usr/local                 296K   707G      296K  /usr/local
rpool/ROOT/ubuntu_2204/var                      9.60G   707G      192K  /var
rpool/ROOT/ubuntu_2204/var/cache                 571M   707G      571M  /var/cache
rpool/ROOT/ubuntu_2204/var/games                 192K   707G      192K  /var/games
rpool/ROOT/ubuntu_2204/var/lib                  7.74G   707G     7.54G  /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService   240K   707G      240K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager    328K   707G      328K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt               126M   707G      126M  /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/docker            192K   707G      192K  /var/lib/docker
rpool/ROOT/ubuntu_2204/var/lib/dpkg             87.1M   707G     87.1M  /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs               192K   707G      192K  /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                  1.28G   707G     1.28G  /var/log
rpool/ROOT/ubuntu_2204/var/mail                  192K   707G      192K  /var/mail
rpool/ROOT/ubuntu_2204/var/snap                 1.20M   707G     1.20M  /var/snap
rpool/ROOT/ubuntu_2204/var/spool                 240K   707G      240K  /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                  12.3M   707G     12.3M  /var/tmp
rpool/ROOT/ubuntu_2204/var/www                   192K   707G      192K  /var/www
rpool/USERDATA                                  4.30M   707G      192K  none
rpool/USERDATA/root_2204                        4.12M   707G     4.12M  /root

mafoelffen@msi-ubuntu:~$ lsblk -e7 -o name,label,size,fstype,type,mountpoint,model
NAME        LABEL             SIZE FSTYPE     TYPE MOUNTPOINT             MODEL
sda                           3.6T            disk                        WDC WD40EZAZ-00S
&#9500;&#9472;sda1                         16M            part                        
&#9500;&#9472;sda2      Win_G             3.4T ntfs       part /home/mafoelffen/WIN_G 
&#9492;&#9472;sda3      Home_LTS        295.4G ext4       part                        
sdb                         465.8G            disk                        Samsung SSD 870
&#9500;&#9472;sdb1      System Reserved    50M ntfs       part                        
&#9500;&#9472;sdb2                      365.2G ntfs       part                        
&#9500;&#9472;sdb3                          1K            part                        
&#9492;&#9472;sdb4                        508M ntfs       part                        
sdc                           3.6T            disk                        WDC WD40EZRZ-22G
&#9500;&#9472;sdc1                        128M            part                        
&#9492;&#9472;sdc2      WIN_F             3.6T ntfs       part                        
sdd                           3.6T            disk                        WDC WD40EZAZ-00S
&#9500;&#9472;sdd1                         16M            part                        
&#9492;&#9472;sdd2      20210604          3.6T ntfs       part                        
sde                           4.5T            disk                        ST5000DM000-1FK1
&#9500;&#9472;sde1                        128M            part                        
&#9492;&#9472;sde2      WIN_H             4.5T ntfs       part /Media_H               
sdf                           7.3T            disk                                        
&#9492;&#9472;sdf1      mpool             7.3T zfs_member part                        
sr0                          1024M            rom                         HL-DT-ST DVDRAM GH24LS70
nvme0n1                       1.8T            disk                        Samsung SSD 990 PRO 2TB
&#9500;&#9472;nvme0n1p1 EFI               750M vfat       part /boot/efi              
&#9500;&#9472;nvme0n1p2 bpool               3G zfs_member part                        
&#9500;&#9472;nvme0n1p3 rpool             750G zfs_member part                        
&#9500;&#9472;nvme0n1p4                   250G swap       part [SWAP]                 
&#9500;&#9472;nvme0n1p5 hpool             359G zfs_member part                        
&#9492;&#9472;nvme0n1p6 kpool             465G zfs_member part                        
nvme2n1                       1.8T            disk                        Samsung SSD 990 PRO 2TB
&#9500;&#9472;nvme2n1p1 kpool             1.8T zfs_member part                        
&#9492;&#9472;nvme2n1p9                     8M            part                        
nvme1n1                     465.8G            disk                        PCIe SSD
&#9492;&#9472;nvme1n1p1 dpool             465G zfs_member part                        
nvme3n1                     465.8G            disk                        PCIe SSD
&#9500;&#9472;nvme3n1p1                    16M            part                        
&#9492;&#9472;nvme3n1p2                 465.7G ntfs       part                        

mafoelffen@Mikes-ThinkPad-T520:~$ sudo zfs list
NAME                                                                                        USED  AVAIL     REFER  MOUNTPOINT
backups                                                                                     224G  1.20T       96K  /zfs-backups
backups/BACKUPS                                                                             224G  1.20T       96K  none
backups/BACKUPS/ubuntu_2204                                                                 224G  1.20T       96K  /zfs-backups
backups/BACKUPS/ubuntu_2204/images-vm                                                       224G  1.20T       96K  /zfs-backups/images-vm
backups/BACKUPS/ubuntu_2204/images-vm/2023-07-25                                            224G  1.20T      224G  /zfs-backups/images-vm/2023-07-25
bpool                                                                                       431M  1.33G       96K  /boot
bpool/BOOT                                                                                  430M  1.33G       96K  none
bpool/BOOT/ubuntu_2204                                                                      430M  1.33G      430M  /boot
dpool                                                                                      2.80M   829G       96K  /dpool
dpool/DATA                                                                                  192K   829G       96K  none
dpool/DATA/ubuntu_2204                                                                       96K   829G       96K  /dpool
hpool                                                                                      56.7G   327G       96K  /home
hpool/USERDATA                                                                             56.6G   327G       96K  none
hpool/USERDATA/root_2204                                                                   2.86G   327G     2.86G  /root
hpool/USERDATA/ubuntu_2204                                                                 53.8G   327G     53.8G  /home
kpool                                                                                       451G   510G       96K  /kpool
kpool/QEMU-KVM                                                                              451G   510G       96K  none
kpool/QEMU-KVM/ubuntu_2204                                                                  451G   510G       96K  /kpool
kpool/QEMU-KVM/ubuntu_2204/ISO                                                              195G   510G      195G  /home/mafoelffen/Downloads/ISO
kpool/QEMU-KVM/ubuntu_2204/images                                                           256G   510G      239G  /var/lib/libvirt/images
kpool/QEMU-KVM/ubuntu_2204/libvirt                                                          536K   510G      536K  /etc/libvirt/
maf1_pool                                                                                  3.21G  23.4G       24K  legacy
maf1_pool/buckets                                                                            24K  23.4G       24K  legacy
maf1_pool/containers                                                                        390M  23.4G       24K  legacy
maf1_pool/containers/maf1-alpine1                                                          5.93M  23.4G     51.0M  legacy
maf1_pool/containers/maf1-archlinux1                                                       39.9M  23.4G      418M  legacy
maf1_pool/containers/maf1-centos1                                                          45.0M  23.4G      307M  legacy
maf1_pool/containers/maf1-gentoo1                                                          40.8M  23.4G     1.26G  legacy
maf1_pool/containers/maf1-jammy1                                                            200M  23.4G      367M  legacy
maf1_pool/containers/maf1-oracle1                                                          46.8M  23.4G      363M  legacy
maf1_pool/containers/maf1-tumbleweed1                                                      11.3M  23.4G      143M  legacy
maf1_pool/custom                                                                             24K  23.4G       24K  legacy
maf1_pool/deleted                                                                          2.66G  23.4G       24K  legacy
maf1_pool/deleted/buckets                                                                    24K  23.4G       24K  legacy
maf1_pool/deleted/containers                                                                 24K  23.4G       24K  legacy
maf1_pool/deleted/custom                                                                     24K  23.4G       24K  legacy
maf1_pool/deleted/images                                                                   2.66G  23.4G       24K  legacy
maf1_pool/deleted/images/00e5b3ea1e45441e3826e870870546b1b910b650c3f528955bfeaefc4f7abacb   387M  23.4G      387M  legacy
maf1_pool/deleted/images/489888eff0432135a2085d7daebfa3961bf8298b095b0a5b95d180c623604ca5  48.8M  23.4G     48.8M  legacy
maf1_pool/deleted/images/4986c7046800680c80bbbb066851495558576d014c6a280fe1caf950672208ab   319M  23.4G      319M  legacy
maf1_pool/deleted/images/4daf768f17e5b8c31474c59e13e70f2ffceed8d48862b41379dac633ca56e0c0   266M  23.4G      266M  legacy
maf1_pool/deleted/images/56f03bca1f77ec709f5f248e702334d3a37ae9e86bfc184ebb64f62fa3219df6  1.26G  23.4G     1.26G  legacy
maf1_pool/deleted/images/98b92c0a39f0c1c972a8b9f09126bd9592705ecbb9689a422908059382deff69   134M  23.4G      134M  legacy
maf1_pool/deleted/images/c14665acda2842525ec9b080baba17c3ac43225fc045ea1e52df939562c84b31   273M  23.4G      273M  legacy
maf1_pool/deleted/virtual-machines                                                           24K  23.4G       24K  legacy
maf1_pool/images                                                                             24K  23.4G       24K  legacy
maf1_pool/virtual-machines                                                                   24K  23.4G       24K  legacy
rpool                                                                                      23.0G   458G       96K  /
rpool/ROOT                                                                                 23.0G   458G       96K  none
rpool/ROOT/ubuntu_2204                                                                     23.0G   458G     8.14G  /
rpool/ROOT/ubuntu_2204/srv                                                                   96K   458G       96K  /srv
rpool/ROOT/ubuntu_2204/tmp                                                                 22.7M   458G     22.7M  /tmp
rpool/ROOT/ubuntu_2204/usr                                                                 3.18G   458G       96K  /usr
rpool/ROOT/ubuntu_2204/usr/local                                                           3.18G   458G     3.18G  /usr/local
rpool/ROOT/ubuntu_2204/var                                                                 11.6G   458G       96K  /var
rpool/ROOT/ubuntu_2204/var/cache                                                            612M   458G      612M  /var/cache
rpool/ROOT/ubuntu_2204/var/games                                                             96K   458G       96K  /var/games
rpool/ROOT/ubuntu_2204/var/lib                                                             6.37G   458G     6.21G  /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService                                              112K   458G      112K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager                                               460K   458G      460K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt                                                          102M   458G      102M  /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/docker                                                        96K   458G       96K  /var/lib/docker
rpool/ROOT/ubuntu_2204/var/lib/dpkg                                                        60.5M   458G     60.5M  /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs                                                          104K   458G      104K  /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                                                              653M   458G      653M  /var/log
rpool/ROOT/ubuntu_2204/var/mail                                                              96K   458G       96K  /var/mail
rpool/ROOT/ubuntu_2204/var/snap                                                            3.59G   458G     3.59G  /var/snap
rpool/ROOT/ubuntu_2204/var/spool                                                            336K   458G      336K  /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                                                              452M   458G      452M  /var/tmp
rpool/ROOT/ubuntu_2204/var/www                                                               96K   458G       96K  /var/www
mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e7 -o name,label,size,fstype,type,mountpoint,model
NAME     LABEL       SIZE FSTYPE     TYPE  MOUNTPOINT MODEL
sda                  1.8T            disk             Samsung SSD 870 QVO 2TB
&#9500;&#9472;sda1   {SYSTEM}    550M vfat       part  /boot/efi  
&#9500;&#9472;sda2               128M            part             
&#9500;&#9472;sda3   {Windows}   900G ntfs       part             
&#9500;&#9472;sda4               983M            part             
&#9500;&#9472;sda5                30G            part             
&#9500;&#9472;sda6                32G            part             
&#9474; &#9492;&#9472;swap swap         32G swap       crypt [SWAP]     
&#9500;&#9472;sda7   bpool         2G zfs_member part             
&#9500;&#9472;sda8   rpool       500G zfs_member part             
&#9492;&#9472;sda9   hpool     397.4G zfs_member part             
sdb                  1.8T            disk             Samsung SSD 870 QVO 2TB
&#9500;&#9472;sdb1   kpool      1000G zfs_member part             
&#9492;&#9472;sdb2   dpool       863G zfs_member part             
sdc                  1.8T            disk             Dogfish SSD 2TB
&#9492;&#9472;sdc1   backups     1.5T zfs_member part             

```
The first is my workstation. The second, my laptop. Both have separated home pools. The workstation has filesystems mounted within my home. 

Look at the second one, my laptop. Look at dpool. dpool has 3 different datasets, mounted in the different places in the filesystem. It is one pool, but the datasets can be split up, and mounted where ever you need it. It is flexible ad you can get real creative... One you understand it, and how it works.

---

### Post by Robbyx on 2023-10-12
Thank you for your advice. ([I]I thought I had replied quickly but it seems a firefox crash caused my posting  to be lost, so I posted this new version of the query that I thought was lost. I am repeating myself below. I suggest you ignore the parts you have addressed in your post #13. 

Following on from your message#13 I have just opened nautilus, gone to other locations, right clicked rpool and immediately a popup message  says: Unable to access location...unknown filesystem type 'zfs_member'[/I])

My intention was not to create another user. 

> If you just change the mountpoint for that and move the files and folders to adjust for that, then all the user home directories automatically are created within that dataset. (No extra work for you.)

If  I follow your suggestion will  /home be over written on a reinstall? If that is the case, looking at gparted for the nvme0n1 drive I think it will allow me to reduce the size of 1p4 and add a new home partition at 1p5. I can then cut and paste  the following into the new home location: 

rpool/USERDATA                                    8.44G   872G      192K  /
rpool/USERDATA/robins_6f9kyf                      8.44G   872G     8.44G  

What size should I make the home partition?

Subject to your reply  this is my roadmap:
[LIST=1]
[*] Sort out location of /home/robins
[*] Restore old data such as program settings and documents.  ( Having restored the data I can delete duplicates and free up disk space on storage media.)
[*] Change rpool to a 3 drive mirror, for security purposes. Is that possible with the following drives?
[/LIST]
[LIST=1]
[*]sda   hitachi 750gb
[*]sdb nvme     250gb
[*]sdc  hd         465gb
[*]nvme0n1       931gb
[*]external HD 2000gb
[/LIST]


I had bought the ext HD as a mobile backup device. Is it correct that in order for me to remove it I will have to remove the drive from the rpool setup? Rpool  will then become a 2 drive mirror until I reinstate the ext HDrive?

I found this helpful resource:
[https://itsjustbytes.wordpress.com/2020/05/10/zfs-command-line-reference-cheat-sheet/](https://itsjustbytes.wordpress.com/2020/05/10/zfs-command-line-reference-cheat-sheet/)

Which command should I use to deactivate the ext HD from the rpool?


Robin

---

### Post by Robbyx on 2023-10-12
I think I have found a way into rpool:
1st I tried accessing rpool via rpool that did not work. But choosing Home, a directory opened which I can access.

Why can't I directly access rpool?

---

### Post by MAFoElffen on 2023-10-12
Because "Home" in Nautilus is /home in the filesystem. rpool is a container, more like a partition, Gnome Naulitus is a file manager and see's file systems, not partitions. You mount a partition or storage container, and you look at it's filesystem... Nautilus uses udisk to make it's mounts. udisk does not know how to mount ZFS containers...

The developers of 'udisk' are not going to spend the time to figure that out, because 'they' just say there is a licensing issue dealing with ZFS... Which 'access' or 'mounting', should not violate anything, but that is their standard "out" answer for that.

To access a ZFS filsystem, you have to import the pool. Importing a pool, makes all the internal mounts and mounts the filesystem within that , to the filesystem of the target. Just like you have to mount a filesystem within a container, whether that container is a partition, LVM LV, ZFS Dataset... Then access that mounted filesystem.

I know that you see the pools mounted already in Nautilus, so the filesytem within the pools are mounted. Nautilus knows how to read the filesystem, so that is enough for you to do anything in that way of reads and writes to the "filesystem" from within Nautilus. 

The Gnome Developers themselves, the ones that maintain Gnome Nautilus, do not understand the details underneath it, but they know the basics:
[https://gitlab.gnome.org/GNOME/nautilus/-/issues/111](https://gitlab.gnome.org/GNOME/nautilus/-/issues/111)

As for, will your home be in danger during a fresh reinstall? Yes... Unless you separate it out, as a separate pool. Then you install fresh with the pool exported > Then import the home pool.

---

### Post by Robbyx on 2023-10-12
> As for, will your home be in danger during a fresh reinstall? Yes... Unless you separate it out, as a separate pool. Then you install fresh with the pool exported > Then import the home pool. 

I will come back to this if I can not put it into practice. In the meantime I am waiting for a book on zfs which might also help me understand better.

Thank you for your kind help

Robin

---

### Post by #&amp;thj^% on 2023-10-12
> **MAFoElffen said:**
> 
As for, will your home be in danger during a fresh reinstall? ]**Yes... Unless you separate it out, as a separate pool.**[/U] Then you install fresh with the pool exported > Then import the home pool.
Amen
> **Robbyx said:**
> I will come back to this if I can not put it into practice. In the meantime I am waiting for a book on zfs which might also help me understand better.


Robbyx that zfs book will turn you into a super hero technically....LOL

---

### Post by MAFoElffen on 2023-10-12
Think of ZFS, just like your past experience with BTRFS and LVM2. Nautilus cannot work directly with LVM VG's or LV's. Nor can it work directly with BTRFS Volumes or Subvolumes... Unitl you mount them into the root filesytem "somewhere" and access it from Nautilus through the filsesystem...

Which is a good segway to start answering one of, what you said was your future plan... Of a adding disks to create a 3-way "mirror". Adding a mirror is common, but why a 3 way mirror? Usually with 3 partitions (notice I didn't say disks) you would do RIADz1 (RAID5), where you could lose a disk... Or if you just added one more mirror to do an extended storage pool, so you have a pool of 2 mirrored vdevs (which would logically be RAID10) or with those 4 partitions, create RAIDz2, where you can afford to lose any 2 disks.  

A mirror, once it loses one disk, that mirror get's degraded. I could get into more technical details about things if traditonal RAID or ZFS, but will just stop there with that explanation.

I'm just trying to figure out what a 3 way mirror would bring to the table.

What value do you think it would give you?

---

