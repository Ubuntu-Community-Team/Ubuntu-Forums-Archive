---
title: "Ubuntu Server 20.04 Installation Failed with &quot;End Kernel Panic: not synching&quot;"
date: 2023-07-31
forum: Installation &amp; Upgrades
---

### Post by jinglenose on 2023-07-31
[SIZE=4][FONT=arial]Hi,  Ubuntu Server 20.04 does not install on my new PC.
It boots into the grub menu and when I choose install Ubuntu it comes out with a large log and ending in the following message:

"end kernel panic - not synching: attempt to kill the idle task"

I have built a new PC using the following kit:
[/FONT][/SIZE][TABLE]
[TR]
[TD="align: left"][SIZE=4][FONT=arial][AMD Ryzen 9 5950X Processor]("https://www.amazon.co.uk/AMD-Ryzen-5950X-Processor-Cache/dp/B0815Y8J9N/ref=sr_1_1?keywords=AMD+Ryzen+9+5950X+Processor+%2816C%2F32T%2C+72MB+Cache%2C+Up+to+4.9+GHz+Max+Boost&s=computers&sr=1-1")
[/FONT][/SIZE][TABLE]
[TR]
[TD="align: left"][SIZE=4][FONT=arial][MSI MAG X570S TOMAHAWK MAX WIFI]("https://www.amazon.co.uk/MSI-TOMAHAWK-Motherboard-Channel-Bluetooth/dp/B09BYZ9J93/ref=sr_1_4?keywords=MSI+MAG+X570S+TORPEDO+MAX+wifi&s=computers&sr=1-4")
[/FONT][/SIZE]
[TABLE]
[TR]
[TD="align: left"][SIZE=4][FONT=arial]128 GB [Crucial Pro RAM]("https://www.amazon.co.uk/Crucial-2x32GB-3200MT-Desktop-CP2K32G4DFRA32A/dp/B0C29W4G29/ref=sr_1_1_sspa?keywords=64GB+DDR4+RAM&s=computers&sr=1-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1") DDR4 
[/FONT][/SIZE][TABLE]
[TR]
[TD="align: left"][SIZE=4][FONT=arial][Noctura-NH-D15]("https://www.amazon.co.uk/Noctua-NH-D15-Premium-Cooler-NF-A15/dp/B00L7UZMAK/ref=sr_1_11?keywords=Noctua+NH-D15S+Chromax&s=computers&sr=1-11") heat sink.
[/FONT][/SIZE][TABLE]
[TR]
[TD="align: left"][SIZE=4][FONT=arial][Generic AMD chipset]("https://www.amazon.co.uk/Dilwe-Computer-Graphics-Express-Desktop-default/dp/B095319YG5/ref=d_dp-upsell-widget_sccl_4_2/262-1075965-5221415?content-id=amzn1.sym.6a8bf132-c500-4b85-9b7c-a82353db78fa&pd_rd_i=B08RNV7D22&th=1") graphics card in PCIe slot 2.
Crucial Gen 4 PCIe M.2 2TB Hard drive.

I am looking to use a PCIe Adaptor with 16 lanes to the CPU adding four 1TB drives in a RAID 10 array,  To do this I have been using ASUS Hyper M.2 X16 PCIe 4.0 X4 Expansion Card Supports 4 NVMe M.2

I entered the bios and set up RAID 10 OK after some messing about but the computer would not install Ubuntu from my USB.

I have removed the PCIe Adapter and tried to install Ubuntu on the M.2 drive but the program dumps out errors.

I have tried using USB2 for the USB stick with no luck.

Bit of a dead loss as to what's causing it.  Other people seem to have used this motherboard and I can't see that the RAM or SSD are an issue.  The graphics card is obviously working enough to get a display.

I'm at a dead loss to be honest, hope someone can help.

I'm not sure how I can get a better dump.

Any ideas?



[/FONT][/SIZE][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[SIZE=4][FONT=arial]
[/FONT][/SIZE][/TD]
[/TR]
[/TABLE]
[SIZE=4][FONT=arial]
[/FONT][/SIZE]

---

### Post by guiverc on 2023-07-31
You've opted to use the 2020-April release of Ubuntu, the Server system (*thus opting to use the most stable kernel stack possible; ie. the oldest*) on a new machine?

The CPU you hadn't been released when 20.04 released, and it takes time for software to be tested & thus appear in products like Ubuntu; thus I'd be trying a newer release, even ISO that uses a new *kernel stack* (*alas that may not be server*).

I'm assuming you [validated the ISO before writing to media]("https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0"); and then validated the write of ISO to media using another box if necessary. You can't expect invalid media to give anything but [problems you experience]("https://askubuntu.com/questions/993407/is-verifying-isos-downloaded-from-the-official-website-worthwhile/993409#993409"), and don't mention performing these checks; concentrating on newish hardware & an old release of Ubuntu.
[I]
Note:  I don't know your hardware[/I]

---

### Post by MAFoElffen on 2023-08-01
I know the hardware, and the Releases. ...And Server Edition. I've been on the Ubuntu Server Team since 2012...

If you somehow used 20.04(.0), then it would it not have booted. It was created before the CPU was released, AND prior to when the microcode of the CPU was released to kernel.org. The support for it in the kernel started late 5.8... (/remember this release number/)

Which Live installer ISO Release did you try? For example, 20.04.6? And why not install LTS Server Edition 22.04? (The current LTS?) 20.04 is EOL in 4/25. 22.04 is EOL 4/27. 

Next is the ISO. Desktop Edition has both kernel track in the ISO (GA & HWE) Having the newer HWE kernel series gives it a step up to be able to boot and run on newer hardware. Server ISo only has the GA Kerrnel series. For Focal Fossa, 20.04, when it released, the GA series of kernel was 5.4. HWE when it was released was 5.8... Which much later, a decision was made, accelerate that HWE kernel series choice to 5.15. (Biggest factor was hardware considerations.)

Put the release numbers above together... Now ca you see that the Server Edition ISO will not boot, but the Desktop Edition of 20.04 will?

You have 2 choices. Install an minimal system from the 20.04 Desktop ISO. Then convert that back to Ubuntu Server (only takes one command), or install Ubuntu Server LTS 22.04.

*** Next... Does that PCIe NVME quad card work with your motherboard? Does that motherboard have a PLX bifuration chip on it with the MSI "PCIe Configuration" menu option? I thought the MSI boards that have that onboard were the Unify, x670e Carbon, x670e ACE, x670e Godlike and the TRX40-A PRO... I know the chipsets that support PCIe Bifurcation: Intel Platform X299, C422, C621, Z390, Z370, Z490, Z590, Z690, X99; AMD Platform TRX40, X399, X570, X470, B550, B450, Z590, etc. And just because the chipset supports it doesn't mean that the BIOS supports it. That is usally in their higher end boards.

Some mobo manufacturers, if you do ot use the top x16 slot for that, then you might only get 2 of the 4 drives come up on those cards. I use a Quad Card with the birfurcation chip on the card I have.

*** Next is, once you get it booting, you may find that Linux will not see your drives at all. None of them that you have setup behind the BIOS RAID. That is ot an HBA RAID controller. You say in MSI's instructions for BIOS RAID, that the options related to Microsoft Windows type right? They are using API's to, and drivers within Windows to do that... Their drivers downloads, do not include Linux Drivers to do the same...

If you really think you need to do RAID, then I would recommend using mdadm, LVM2 RAID, or ZFS RAIDz. RAID is not a replacement for backups. But there are reasons for RAID. One is uptime, meaning staying running. Hardware and software mdadm, What I found out long ago which disaster management in a crisis (for servers), is that you should create with hot-spares. Then is worse-off, expect and plan to destroy your old arrays, to create new to restore to. For better adaptability, portability, and flexibility... I converted everything I had to LVM2 RAID, then later on to ZFS RAIDz.

I test daily builds. I run LTS'es as daily drivers. You are planning to run LTS, but from a previous release, before your hardware came out. 22.04 has been out for over a year and is well-proven in production. I run new hardware, so I run the HWE stack on my servers. I would try 22.04 and see if it boots and runs. Then relook at your plan, to verify and see what will work with the hardware you have.

This is one of my servers, with a PCIe x M.2 Bifurifaction card:
```

mafoelffen@Mikes-ThinkPad-T520:~$ ssh mafoelffen@10.0.0.3
Welcome to Ubuntu 22.04.2 LTS (GNU/Linux 5.19.0-50-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

Expanded Security Maintenance for Applications is not enabled.

79 updates can be applied immediately.
66 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status

Last login: Sun Jul 30 06:18:49 2023 from 10.0.0.170
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
nvme1n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme1n1p1 kpool      1.8T zfs_member            
nvme0n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme0n1p1 kpool      1.8T zfs_member            
nvme4n1              931.5G                       WD Blue SN570 1TB
&#9500;&#9472;nvme4n1p1            512M vfat       /boot/efi  
&#9500;&#9472;nvme4n1p2              2G swap       [SWAP]     
&#9500;&#9472;nvme4n1p3 bpool        2G zfs_member            
&#9492;&#9472;nvme4n1p4 rpool      927G zfs_member            
nvme3n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme3n1p1 kpool      1.8T zfs_member            
nvme2n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme2n1p1 kpool      1.8T zfs_member            
nvme6n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme6n1p1 datapool  1000G zfs_member            
nvme5n1     datapool   1.8T zfs_member            Samsung SSD 970 EVO 2TB
&#9500;&#9472;nvme5n1p1            1.3T zfs_member            
&#9492;&#9472;nvme5n1p2 datapool    10G zfs_member            
mafoelffen@Mikes-B460M:~$ zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              293M  1.46G       96K  /boot
bpool/BOOT                                         291M  1.46G       96K  none
bpool/BOOT/ubuntu_2cwpns                           291M  1.46G      291M  /boot
datapool                                           931G  3.81T      307K  /data
datapool/DATA                                      931G  3.81T      307K  none
datapool/DATA/ubuntu_2cwpns                        931G  3.81T     10.0G  /data
datapool/DATA/ubuntu_2cwpns/ISO                    403G  3.81T      403G  /data/ISO
datapool/DATA/ubuntu_2cwpns/KVM-VM                 518G  3.81T      518G  /data/KVM-VM
kpool                                             1.56T  1.85T      279K  /KVM_Pool
kpool/KVM                                         1.56T  1.85T      279K  none
kpool/KVM/ubuntu_2cwpns                           1.56T  1.85T     1.56T  /KVM_Pool
rpool                                             15.9G   876G       96K  /
rpool/ROOT                                        14.0G   876G       96K  none
rpool/ROOT/ubuntu_2cwpns                          14.0G   876G     7.07G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   876G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   876G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   876G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      6.91G   876G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   876G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  6.66G   876G     6.51G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   876G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    180K   876G      180K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt               113M   876G      113M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             46.0M   876G     46.0M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   248M   876G      248M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   876G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.49M   876G     1.49M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   876G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   876G       96K  /var/www
rpool/USERDATA                                    1.93G   876G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  1.93G   876G     1.93G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        2.66M   876G     2.66M  /root
mafoelffen@Mikes-B460M:~$ sudo zpool status -v datapool
  pool: datapool
 state: ONLINE
status: One or more devices has experienced an unrecoverable error.  An
    attempt was made to correct the error.  Applications are unaffected.
action: Determine if the device needs to be replaced, and clear the errors
    using 'zpool clear' or replace the device with 'zpool replace'.
   see: https://openzfs.github.io/openzfs-docs/msg/ZFS-8000-9P
  scan: scrub repaired 0B in 00:16:11 with 0 errors on Sun Jul 30 06:36:28 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     4     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors
mafoelffen@Mikes-B460M:~$ sudo zpool status -v kpool
  pool: kpool
 state: ONLINE
  scan: scrub repaired 0B in 00:06:08 with 0 errors on Sun Jul 30 06:45:27 2023
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
I'm in the middle of upgrading my workstation, which is on an MSI MPG Z790 Edge WiFi DDR5... Which I also have a bifurcation card ordered for. which I also have installed as ZFS-On-Root. I migrate the old system to the new with the Ubuntu Server 22.04.2 Live Installer. The old for that one was on LVM2 RAID.

---

### Post by MAFoElffen on 2023-08-01
Part 2:

I have two reasons for using RAID: Reliability and speed performance increase. My through-put benchmarks on my server (above) is in the multi-GiB/s... I can run VM Guests that 'pop', better than most people can run on normal physical hardware.

With hardware RAID and Linux software RAID, there are no warnings before the array goes into degraded or failed. You get warnings from LVM2 RAID and ZFS RAIDz. They are also more flexible, and you can make changes (in structure, size, etc) and do maintenance on a live filesystem. With ZFS, even more. With both, I can export and migrate the data members to other places or machines. Both, I can take snapshots. Both are production ready. ZFS has a steeper learning curve of the two. Check into both of these volume managers to see what might fit your needs.

Here is my workstation, still in the rebuilding stage:
```

root@msi-ubuntu:~# lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME        LABEL             SIZE FSTYPE     MOUNTPOINT             MODEL
sda                           3.6T                                   WDC WD40EZAZ-00S
&#9500;&#9472;sda1                         16M                                   
&#9500;&#9472;sda2      Win_G             3.4T ntfs       /home/mafoelffen/WIN_G 
&#9492;&#9472;sda3      Home_LTS        295.4G ext4                              
sdb                         465.8G                                   Samsung SSD 870
&#9500;&#9472;sdb1      System Reserved    50M ntfs                              
&#9500;&#9472;sdb2                      365.2G ntfs                              
&#9500;&#9472;sdb3                          1K                                   
&#9492;&#9472;sdb4                        508M ntfs                              
sdc                           3.6T                                   WDC WD40EZRZ-22G
&#9500;&#9472;sdc1                        128M                                   
&#9492;&#9472;sdc2      WIN_F             3.6T ntfs                              
sdd                           3.6T                                   WDC WD40EZAZ-00S
&#9500;&#9472;sdd1                         16M                                   
&#9492;&#9472;sdd2      20210604          3.6T ntfs                              
sde                           4.5T                                   ST5000DM000-1FK1
&#9500;&#9472;sde1                        128M                                   
&#9492;&#9472;sde2      WIN_H             4.5T ntfs       /Media_H               
sdf         varpool           7.3T zfs_member                                        
&#9492;&#9472;sdf1      mpool             1.5T zfs_member                        
nvme2n1                       1.8T                                   Samsung SSD 990 PRO 2TB
&#9500;&#9472;nvme2n1p1 kpool             1.8T zfs_member                        
&#9492;&#9472;nvme2n1p9                     8M                                   
nvme0n1                       1.8T                                   Samsung SSD 990 PRO 2TB
&#9500;&#9472;nvme0n1p1 EFI               750M vfat       /boot/efi              
&#9500;&#9472;nvme0n1p2 bpool               3G zfs_member                        
&#9500;&#9472;nvme0n1p3 rpool             750G zfs_member                        
&#9500;&#9472;nvme0n1p4                   250G swap       [SWAP]                 
&#9500;&#9472;nvme0n1p5 hpool             359G zfs_member                        
&#9492;&#9472;nvme0n1p6 kpool             465G zfs_member                        
nvme3n1                     465.8G                                   PCIe SSD
&#9492;&#9472;nvme3n1p1                 465.8G zfs_member                        
nvme1n1                     465.8G                                   PCIe SSD
&#9492;&#9472;nvme1n1p1 dpool             465G zfs_member                        
root@msi-ubuntu:~# zfs list
NAME                                             USED  AVAIL     REFER  MOUNTPOINT
bpool                                            518M  2.12G      192K  /boot
bpool/BOOT                                       517M  2.12G      192K  none
bpool/BOOT/ubuntu_2204                           517M  2.12G      517M  /boot
dpool                                           1.38M   450G       96K  /dpool
dpool/DATA                                       192K   450G       96K  none
dpool/DATA/ubuntu_2204                            96K   450G       96K  /dpool
hpool                                            472M   346G      192K  /home
hpool/USERDATA                                   464M   346G      192K  none
hpool/USERDATA/ubuntu_2204                       464M   346G      464M  /home
kpool                                            399G   500G       96K  /kpool
kpool/QEMU-KVM                                   399G   500G       96K  none
kpool/QEMU-KVM/ubuntu_2204                       399G   500G      104K  /kpool
kpool/QEMU-KVM/ubuntu_2204/ISO                   399G   500G      399G  /kpool/ISO
kpool/QEMU-KVM/ubuntu_2204/KVM-VM                 96K   500G       96K  /kpool/KVM-VM
kpool/QEMU-KVM/ubuntu_2204/images                112K   500G      112K  /var/lib/libvirt/images
kpool/QEMU-KVM/ubuntu_2204/libvirt               576K   500G      576K  /etc/libvirt/
mpool                                           2.24G  1.41T       96K  /mpool
mpool/BACKUPS                                   2.24G  1.41T       96K  none
mpool/BACKUPS/ubuntu_2204                       2.24G  1.41T     2.24G  /mpool/backups
mpool/MEDIA                                      192K  1.41T       96K  none
mpool/MEDIA/ubuntu_2204                           96K  1.41T       96K  /mpool/media
rpool                                           16.8G   708G      192K  /
rpool/ROOT                                      16.7G   708G      192K  none
rpool/ROOT/ubuntu_2204                          16.7G   708G     7.29G  /
rpool/ROOT/ubuntu_2204/srv                       192K   708G      192K  /srv
rpool/ROOT/ubuntu_2204/usr                       488K   708G      192K  /usr
rpool/ROOT/ubuntu_2204/usr/local                 296K   708G      296K  /usr/local
rpool/ROOT/ubuntu_2204/var                      9.44G   708G      192K  /var
rpool/ROOT/ubuntu_2204/var/cache                 432M   708G      432M  /var/cache
rpool/ROOT/ubuntu_2204/var/games                 192K   708G      192K  /var/games
rpool/ROOT/ubuntu_2204/var/lib                  7.99G   708G     7.84G  /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService   240K   708G      240K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager    280K   708G      280K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt              80.3M   708G     80.3M  /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/docker            192K   708G      192K  /var/lib/docker
rpool/ROOT/ubuntu_2204/var/lib/dpkg             77.8M   708G     77.8M  /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs               192K   708G      192K  /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                  1.01G   708G     1.01G  /var/log
rpool/ROOT/ubuntu_2204/var/mail                  192K   708G      192K  /var/mail
rpool/ROOT/ubuntu_2204/var/snap                  976K   708G      976K  /var/snap
rpool/ROOT/ubuntu_2204/var/spool                 240K   708G      240K  /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                  12.3M   708G     12.3M  /var/tmp
rpool/ROOT/ubuntu_2204/var/www                   192K   708G      192K  /var/www
rpool/USERDATA                                  4.05M   708G      192K  none
rpool/USERDATA/root_2204                        3.87M   708G     3.87M  /root
root@msi-ubuntu:~# zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  2.75G   518M  2.24G        -         -     1%    18%  1.00x    ONLINE  -
dpool   464G  1.38M   464G        -         -     0%     0%  1.00x    ONLINE  -
hpool   358G   472M   358G        -         -     0%     0%  1.00x    ONLINE  -
kpool   928G   399G   529G        -     1.36T     1%    43%  1.00x    ONLINE  -
mpool  1.46T  2.24G  1.46T        -         -     0%     0%  1.00x    ONLINE  -
rpool   748G  16.8G   731G        -         -     0%     2%  1.00x    ONLINE  -

```

---

