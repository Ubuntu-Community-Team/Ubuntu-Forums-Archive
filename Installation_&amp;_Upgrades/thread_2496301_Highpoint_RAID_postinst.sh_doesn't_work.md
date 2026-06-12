---
title: "Highpoint RAID postinst.sh doesn't work"
date: 2024-03-22
forum: Installation &amp; Upgrades
---

### Post by jessica445566 on 2024-03-22
I have a highpoint 7505, created a RAID0, I am working from the instructions here:

[https://download.highpoint-tech.com/www/HighPoint-Download/Document/Guide/SSD7000/RAID%20Management%20Guide/Linux_Ubuntu_On_HighPoint_NVMe_RAID_Controller_Installation_Guide_V1.03_23_11_22.pdf](https://download.highpoint-tech.com/www/HighPoint-Download/Document/Guide/SSD7000/RAID%20Management%20Guide/Linux_Ubuntu_On_HighPoint_NVMe_RAID_Controller_Installation_Guide_V1.03_23_11_22.pdf)

After lots of tinkering, downloading the old sub-version of ubuntu (22.04.2) in order to have a version 5 kernel, etc, I managed to get ubuntu installed on the RAID0 drive.  All of the highpoint instructions have worked up to this point, and It is now sitting in the post-install version of Ubuntu (prior to restarting), which is when I'm supposed to run the postinst.sh script in order to load the driver into the kernel so that when it restarts, it sees it and is able to run off he new RAID.  The postinst.sh script fails, and looking at the script, it appears that it is looking for files to be present in the /target directory, but that directory is empty.  I don't know what it's trying to do, or what the files are that it thinks are supposed to be there.

As a workaround, I also tried installing the regular open source driver from highpoint, but that didn't work either due to incorrect kernel version.

I'm pretty sure if I let Ubuntu restart, it's going to be unable to boot without the postinst.sh script successfully installing the driver.  Any ideas?

---

### Post by MAFoElffen on 2024-03-23
Looking at the spec sheet for that controller. Says for Linux, only requires Kernel 3.10 or later.

Reading the PDF. Will get back to you after that.

I have an idea, before reading that... That it probably installs the driver module to the Live Environment to recognize the card during the install, then afterwards, you need to mount /target, and chroot into it to install that same driver module into the kernel. I have to do that occasionally for some things.

---

### Post by MAFoElffen on 2024-03-23
Oh man... PITA.

So...
1.) The system does no tsee anything on that card until the driver is loaded.

 2.) There is no DKMS process for that module to rebuild when a kernel  is updated. Which means, that for every update, you need to be very  aware of if there are any kernel updates, and when a kerenl update does  happen, before you reboot, to manually rebuild the modules for the new  kernel.

a.) Backup work-around, is if you do have to reboot, and you didnt build  the new modules yet, then use the advanced options menu to boot from  the next previous kernel, so that you can boot and build rebuild the  modules...

So this is not a native hard-rad card. More like BIOS "fake raid".

From the manual, it does not say if the system can see the NVMe devices  if you do jbod. And that if you did, if you still needed the driver to  see what is on the card, or if the driver is just to see the raid array  on the card.

Hmmm. That is something you might want to check. There might be a  better, and safer way to end up with the same end-point, that would be a  lot less work in the long-run. By doing jbod and software RAID. Or use  LVM or ZFS Volume Managers to increase your storage pool as needed..

It  also says in the initial boot of the installer LiveUSB, that you before  the boot, to disconnect all other NVMe drives, then on the boot,  blacklist the NVMe module, So none of those drives are going to come up  during the process. Not sure if the postinstall scripts add anything to  the boot line, that is similar.

---

### Post by jessica445566 on 2024-03-23
Thanks for looking into it. The more I mess with it, the more I'm thinking it's not a good idea. This is kinda just a project to tinker with, but yeah agreed that it's really dangerous going forward if it's going to break every time there's a kernel update. I'm leaning toward giving up on it. 

One question, conceptually though. If it needs a driver to read the card and that driver (along with the rest of the operating system) is on that very same card, how does it work at all?

---

### Post by MAFoElffen on 2024-03-23
I'm thinking it will see the drives if you do jbod... Without having to use the driver. The driver would be for doing fake-raid on the card...

*** But I would contact the vendor to see exactly what the driver does and how it works with that card. I follow the path that if I understand how something works, then I can exploit all the possibilities of what it might be able to do... Does that make sense to you?

If you do jbod, then you could do Linux mdadm, ZFS or LVM2.

What is your goal? If just a RAID0, that is a bit dangerous at the get go. That is not just with the 'drive' itself, but with filesystem or write errors. This is why I moved away from hard-RAID in favor of mdadm, then later from mdadm to LVM, then ZFS. If you do RAID0 and one drive fails, 'everything' goes. What size drives are you wanting to use, and what path are you wanting to follow? 

I was never a fan of fake-RAID. There are a lot of problems where the vendor has to be on the ball with any new kernel changes (constantly).

If you just want to make your storage area bigger, there are smarter ways to do that. It seems like that card creates arrays on the raw disks, before adding partitions... That is also a bit risky, unless it is true hard-RAID, like LSI. Better to do jbod with partitions, then do what you want, whatever that might be.

What I would do is jbod to see the drives. Create Partitions for the OS to live and boot from. Create partitions for your home and data. Create them as a size you think you need. Those could be RAID or not. But use a Volume Manager such as LVM2 or ZFS, so that you can add to it later easily. I always keep some unreserved 'storage', in case things come up, so I can assign it to where I need it as the system grows.

To add to it, you just create another partition and add it to your LV or Pool. <-- That is like doing RAID0, but safer. That, and with LVM or ZFS, you can do it with a Live Filesystem. With mdadm, you have to make changes offline.

My preference is with ZFS. Both LVM and ZFS have a "ramp up" to learn. I believe learning ZFS would be a valuable investment for you. It is very robust and flexible.

I have my home and data storage pools on RAIDZ2 and RAIDZ3. It takes 4 partitions to create a RAIDZ2 array. Build a striped array that can afford to lose 2 members and still run... While being able to work on it while live. With RAIDz3, you can loose 3 members. Being striped over multiple disks makes it very fast performance wise. The filesystem is copy-on-write, which means it confirms the write, before going on. Doing a scrub, it like doing fsck, to check ad repair the filesystem of any errors. It give lots of warnings before a failure. It is also very forgiving.

It's drivers rebuild over a kernel update...

LVM is easier to learn, and also has an mdadm implementation, which is easier to use... Bout bout LVM and ZFS allow adding partitions as pieces of the pie, to create RAID0 storage pools easily and on the fly... Using a live filesystem = running while making changes.

Both my server and workstation, each have PCIe 4 x M.2 NVMe cards with onboard bifurcation chips (as yours does). Mine is a different brand. They all work together. They do not conflict with any of the the motherboard attached storage devices. They do not need to be removed or disconnected during an install on mine.

---

### Post by MAFoElffen on 2024-03-23
Here is how that looks on my server:
```

mafoelffen@Mikes-B460M:~$ lspci -knnn | grep -A3 -E 'Non-Volatile memory controller'
03:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983 [144d:a808]
    Subsystem: Samsung Electronics Co Ltd SSD 970 EVO Plus 1TB [144d:a801]
    Kernel driver in use: nvme
    Kernel modules: nvme
04:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983 [144d:a808]
    Subsystem: Samsung Electronics Co Ltd SSD 970 EVO Plus 1TB [144d:a801]
    Kernel driver in use: nvme
    Kernel modules: nvme
05:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983 [144d:a808]
    Subsystem: Samsung Electronics Co Ltd SSD 970 EVO Plus 1TB [144d:a801]
    Kernel driver in use: nvme
    Kernel modules: nvme
06:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983 [144d:a808]
    Subsystem: Samsung Electronics Co Ltd SSD 970 EVO Plus 1TB [144d:a801]
    Kernel driver in use: nvme
    Kernel modules: nvme
0b:00.0 Non-Volatile memory controller [0108]: Sandisk Corp WD Blue SN570 NVMe SSD [15b7:501a]
    Subsystem: Sandisk Corp WD Blue SN570 NVMe SSD [15b7:501a]
    Kernel driver in use: nvme
    Kernel modules: nvme
--
0e:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983 [144d:a808]
    Subsystem: Samsung Electronics Co Ltd SSD 970 EVO Plus 1TB [144d:a801]
    Kernel driver in use: nvme
    Kernel modules: nvme
0f:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983 [144d:a808]
    Subsystem: Samsung Electronics Co Ltd SSD 970 EVO Plus 1TB [144d:a801]
    Kernel driver in use: nvme
    Kernel modules: nvme
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
nvme4n1              931.5G                       WD Blue SN570 1TB
&#9500;&#9472;nvme4n1p1            512M vfat       /boot/efi  
&#9500;&#9472;nvme4n1p2              2G swap       [SWAP]     
&#9500;&#9472;nvme4n1p3 bpool        2G zfs_member            
&#9492;&#9472;nvme4n1p4 rpool      927G zfs_member            
nvme1n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme1n1p1 kpool      1.8T zfs_member            
nvme6n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme6n1p1 datapool  1000G zfs_member            
nvme3n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme3n1p1 kpool      1.8T zfs_member            
nvme0n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme0n1p1 kpool      1.8T zfs_member            
nvme2n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme2n1p1 kpool      1.8T zfs_member            
nvme5n1     datapool   1.8T zfs_member            Samsung SSD 970 EVO 2TB
&#9500;&#9472;nvme5n1p1            1.3T zfs_member            
&#9492;&#9472;nvme5n1p2 datapool    10G zfs_member            
mafoelffen@Mikes-B460M:~$ sudo zpool status -v {datapool,kpool}
  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 00:21:04 with 0 errors on Sun Mar 10 00:45:05 2024
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
  scan: scrub repaired 0B in 00:12:35 with 0 errors on Sun Mar 10 00:36:37 2024
config:

    NAME                                 STATE     READ WRITE CKSUM
    kpool                                ONLINE       0     0     0
      raidz2-0                           ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1  ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1  ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1  ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1  ONLINE       0     0     0

errors: No known data errors

```
kpool is the RAIDZ2 array using 4 NVMe drives, each with just one partition, all added as members to a RAIDZ2 array. In the lspci results, you can see how it uses the generic nvme module, that is standard with all kernels... and the the onboard bifurcation chip splits the lanes of the PCIe bus for the M.2 drives.

---

### Post by MAFoElffen on 2024-03-23
Oh... Hints on sizes on pool sizes on that system to get your mind going on possibilities for a plan for yours:
```

mafoelffen@Mikes-B460M:~$ sudo zpool list -v
NAME                                                    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool                                                  1.88G   306M  1.58G        -         -     1%    15%  1.00x    ONLINE  -
  0196ab45-3ee2-894e-b725-39560409109f                 1.88G   306M  1.58G        -         -     1%  15.9%      -    ONLINE
datapool                                               9.09T  2.27T  6.83T        -         -     5%    24%  1.00x    ONLINE  -
  raidz2-0                                             9.09T  2.27T  6.83T        -         -     5%  24.9%      -    ONLINE
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1      -      -      -        -         -      -      -      -    ONLINE
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1      -      -      -        -         -      -      -      -    ONLINE
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1      -      -      -        -         -      -      -      -    ONLINE
    ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1      -      -      -        -         -      -      -      -    ONLINE
    ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1      -      -      -        -         -      -      -      -    ONLINE
logs                                                       -      -      -        -         -      -      -      -  -
  nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   9.50G  1.50M  9.50G        -         -     0%  0.01%      -    ONLINE
cache                                                      -      -      -        -         -      -      -      -  -
  nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   1.25T  91.2G  1.16T        -         -     0%  7.12%      -    ONLINE
kpool                                                  7.27T  3.40T  3.87T        -         -     0%    46%  1.00x    ONLINE  -
  raidz2-0                                             7.27T  3.40T  3.87T        -         -     0%  46.7%      -    ONLINE
    nvme-eui.0025385a2140bd61-part1                        -      -      -        -         -      -      -      -    ONLINE
    nvme-eui.0025385a21418769-part1                        -      -      -        -         -      -      -      -    ONLINE
    nvme-eui.0025385a2141f4fc-part1                        -      -      -        -         -      -      -      -    ONLINE
    nvme-eui.0025385b21407ef0-part1                        -      -      -        -         -      -      -      -    ONLINE
rpool                                                   920G  19.4G   901G        -         -     1%     2%  1.00x    ONLINE  -
  ae13efaa-d1cf-ec40-86a6-2883f0e07102                  920G  19.4G   901G        -         -     1%  2.10%      -    ONLINE
mafoelffen@Mikes-B460M:~$ sudo zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              305M  1.45G       96K  /boot
bpool/BOOT                                         303M  1.45G       96K  none
bpool/BOOT/ubuntu_2cwpns                           303M  1.45G      303M  /boot
datapool                                          1.21T  3.51T      307K  /data
datapool/DATA                                     1.21T  3.51T      307K  none
datapool/DATA/ubuntu_2cwpns                       1.21T  3.51T     10.0G  /data
datapool/DATA/ubuntu_2cwpns/ISO                    489G  3.51T      489G  /data/ISO
datapool/DATA/ubuntu_2cwpns/KVM-VM                 739G  3.51T      739G  /data/KVM-VM
kpool                                             1.64T  1.76T      279K  /KVM_Pool
kpool/KVM                                         1.64T  1.76T      279K  none
kpool/KVM/ubuntu_2cwpns                           1.64T  1.76T     1.64T  /KVM_Pool
rpool                                             19.4G   872G       96K  /
rpool/ROOT                                        15.4G   872G       96K  none
rpool/ROOT/ubuntu_2cwpns                          15.4G   872G     6.74G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   872G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       236K   872G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 140K   872G      140K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      8.64G   872G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   872G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  8.26G   872G     7.54G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   872G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    196K   872G      196K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt               686M   872G      686M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             50.1M   872G     50.1M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   389M   872G      389M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   872G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.54M   872G     1.54M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   872G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   872G       96K  /var/www
rpool/USERDATA                                    3.96G   872G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  3.96G   872G     3.96G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        3.04M   872G     3.04M  /root

```
Just let your imagination run a bit for a plan that makes sense. The possibilities are endless to do that smartly.

---

