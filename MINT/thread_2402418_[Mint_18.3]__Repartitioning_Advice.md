---
title: "[Mint 18.3]  Repartitioning Advice"
date: 2018-09-29
forum: MINT
---

### Post by tinker123 on 2018-09-29
Hello,

I am running Linux Mint 18.3 on my computer.

I would like to resize the existing partitions to create a partition for Windows 10.   

I'm thinking of giving Windows 10, 20 gigabytes in its partition.  I don't plan on using that much or installing much there.  
I'm installing it to make it easier to VPN ( with a USB CAC reader ) into my computer at work.

I have tried the VM route, but I can't get Windows 10 in a VM to autodetect drivers it needs to, according to the VPN & CAC guide I have from work.

So, I would like to set up a partition for Windows 10, so I can do a native install & dual boot.

Its been many years since I've done this, I have forgotten everything I know in this regard.

I Gparted and it looks like /dev/sd5 is where all the room is.

When I brought up Gparted it said that drive was active and I saw no options for resizing.   I'm guessing I will also need to reformat the new partition on nfsts.

How would I move forward?

I posted some information about my system below:



```


Mint18.3SlyviaCinnamonBIOSDelKey$ lsblk
NAME                MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb                   8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1                8:17   0 931.5G  0 part /media/steve/FreeAgent GoFlex Drive
sr0                  11:0    1   4.4G  0 rom  /media/steve/CCCOMA_X64FRE_EN-US_DV9
sda                   8:0    0 232.9G  0 disk 
&#9500;&#9472;sda5                8:5    0 232.4G  0 part 
&#9474; &#9500;&#9472;mint--vg-swap_1 253:1    0    16G  0 lvm  [SWAP]
&#9474; &#9492;&#9472;mint--vg-root   253:0    0 216.4G  0 lvm  /
&#9492;&#9472;sda1                8:1    0   487M  0 part /boot
Mint18.3SlyviaCinnamonBIOSDelKey$ 
```



```
Mint18.3SlyviaCinnamonBIOSDelKey$ df -hT
Filesystem                Type      Size  Used Avail Use% Mounted on
udev                      devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs                     tmpfs     1.6G  9.5M  1.6G   1% /run
/dev/mapper/mint--vg-root ext4      213G   74G  129G  37% /
tmpfs                     tmpfs     7.9G   55M  7.8G   1% /dev/shm
tmpfs                     tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                     tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1                 ext2      472M   68M  380M  16% /boot
cgmfs                     tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs                     tmpfs     1.6G   36K  1.6G   1% /run/user/1000
/dev/sr0                  udf       4.4G  4.4G     0 100% /media/steve/CCCOMA_X64FRE_EN-US_DV9
/dev/sdb1                 fuseblk   932G  205G  728G  22% /media/steve/FreeAgent GoFlex Drive
Mint18.3SlyviaCinnamonBIOSDelKey$ 
```


```
Mint18.3SlyviaCinnamonBIOSDelKey$ lvs
  LV     VG      Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   mint-vg -wi-ao---- 216.43g                                                    
  swap_1 mint-vg -wi-ao----  15.93g                                                    
Mint18.3SlyviaCinnamonBIOSDelKey$ 

```


```
Mint18.3SlyviaCinnamonBIOSDelKey$ vgs
  VG      #PV #LV #SN Attr   VSize   VFree 
  mint-vg   1   2   0 wz--n- 232.41g 44.00m
Mint18.3SlyviaCinnamonBIOSDelKey$ 
```


```
Mint18.3SlyviaCinnamonBIOSDelKey$ pvs
  PV         VG      Fmt  Attr PSize   PFree 
  /dev/sda5  mint-vg lvm2 a--  232.41g 44.00m
Mint18.3SlyviaCinnamonBIOSDelKey$
```

 ```

Mint18.3SlyviaCinnamonBIOSDelKey$  inxi -Fdpz
System:    Host: Godzilla Kernel: 4.10.0-38-generic x86_64 (64 bit) Desktop: Cinnamon 3.6.7
           Distro: Linux Mint 18.3 Sylvia
Machine:   Mobo: ASUSTeK model: PRIME Z370-P v: Rev X.0x
           Bios: American Megatrends v: 0606 date: 12/12/2017
CPU:       Hexa core Intel Core i7-8700K (-HT-MCP-) cache: 12288 KB 
           clock speeds: max: 4700 MHz 1: 4488 MHz 2: 899 MHz 3: 899 MHz 4: 899 MHz 5: 1705 MHz
           6: 4018 MHz 7: 1500 MHz 8: 4375 MHz 9: 929 MHz 10: 1578 MHz 11: 911 MHz 12: 899 MHz
Graphics:  Card: NVIDIA Device 1c81
           Display Server: X.org 1.18.4 drivers: (unloaded: fbdev,vesa) FAILED: nouveau
           tty size: 104x27 Advanced Data: N/A for root
Audio:     Card-1 Intel Device a2f0 driver: snd_hda_intel Sound: ALSA v: k4.10.0-38-generic
           Card-2 NVIDIA Device 0fb9 driver: snd_hda_intel
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp4s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1250.3GB (25.1% used) ID-1: /dev/sda model: Samsung_SSD_860 size: 250.1GB
           ID-2: USB /dev/sdb model: FreeAgent_GoFlex size: 1000.2GB
           Optical: /dev/sr0 model: HL-DT-ST DVDRAM GH24NSC0 dev-links: cdrom,cdrw,dvd,dvdrw
           Features: speed: 94x multisession: yes audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r,dvd-ram
Partition: ID-1: / size: 213G used: 74G (37%) fs: ext4 dev: /dev/dm-0
           ID-2: /boot size: 472M used: 68M (16%) fs: ext2 dev: /dev/sda1
           ID-3: /media/steve/CCCOMA_X64FRE_EN-US_DV9 size: 4.4G used: 4.4G (100%) fs: udf dev: /dev/sr0
           ID-4: /media/steve/FreeAgent GoFlex Drive size: 932G used: 205G (22%) fs: fuseblk dev: /dev/sdb1
           ID-5: swap-1 size: 17.10GB used: 0.00GB (0%) fs: swap dev: /dev/dm-1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 292 Uptime: 29 min Memory: 2267.0/15975.0MB Client: Shell (bash) inxi: 2.2.35 
Mint18.3SlyviaCinnamonBIOSDelKey$ 

```

---

### Post by yancek on 2018-09-29
You have an LVM install so the methods/software needed are different than standard partitioning.  Take a look at the link below and/or do an online search for "resize lvm partitions linux".

[https://www.rootusers.com/lvm-resize-how-to-increase-an-lvm-partition/](https://www.rootusers.com/lvm-resize-how-to-increase-an-lvm-partition/)

---

