---
title: "Full RAID0 Encryption"
date: 2013-09-13
forum: Installation &amp; Upgrades
---

### Post by ww21 on 2013-09-13
Hello,
I have 2x 128GB SSD [/dev/sda and /dev/sdb] what I want to do is:

1. merge them into RAID0 for 256GB space + double I/O

```
128gb /dev/sda                 128gb /dev/sdb
----------------------         -----------------------
                     |         |
                     V         V
                    256gb /dev/md0
```


2. then, divide it 256 = 1 + 255 [GB]

```
              256 gb /dev/md0
[ - | - - - - - - - - - - - - - - - - - - - - - - - ]
  |                                  |
  V                                  V
1gb /dev/md0p1             255gb /dev/md0p2      
```


3. then, make full disk encryption on 255gb part
```

               256gb /dev/md0
[ - | # # # # # # # # # # # # # # # # # ]
                           |
                           V
               255gb /dev/md0p2
                           |
                           V
           255gb EXTENDED PARTITION
                           |
                           V
               255gb /dev/md0p5_crypt
```


4. then, install Ubuntu this way, that /boot is on 1gb part, and / is on encrypted 255gb

```
               256gb /dev/md0
[ - | # # # # # # # # # # # # # # # # # ]
  |                              |
  V                              V
1gb /dev/md0p1        255gb /dev/md0p2 -> EXTENDED -> /dev/md0p5_crypt
          |                                                      |
          V                                                      V
1gb /boot ext4           255gb / ext4 <- PASSWORD <- 255gb / crypt-luks
```

So yea, a bit complicated ;]
Now some Q/A to make things faster:

Q: Why I am not using swap?
A: I have 8gb RAM, using about 1gb all the time

Q: What have I already tried
A: Debian installed successfully BUT using fakeraid [and I want real software raid].
    Xubuntu installed successfuly BUT using fakeraid + was major problem with installing GRUB.
     I had to rescue, and with some miracle I have installed GRUB2 in  /dev/sda [same configuration but with raid insteed of fakeraid is not  working]

Q: What exacly am I trying to install?
A: Any version of Ubuntu 13.04 amd64 [mabye with xfce DE so let's call it Xubuntu]

Q: How am I trying to do it right now?
A:  I am booting Xubuntu live usb [from unetbootin if it matters] then  update and install cryptsetup and mdadm and dmraid and lvm2.
      Then execute ```
sudo mdadm --create /dev/md0 --chunk=4 --level=0  --raid-devices=2 /dev/sdb /dev/sdc
```[COLOR=#ff0000] THIS IS LIVE USB SO /dev/sda IS USB! [/COLOR]
what makes me /dev/md0.
     Then, I am trying normal install, /dev/md0p2 ==[luks-crypt]==> /dev/md0p5_crypt ==[password]==> ext4 /.
     The installation is successful, BUT it fails to install grub.
     Where? Everywhere! /dev/sda, /dev/sdb, /dev/md0, /dev/md0p1, /dev/mdp5, /dev/md0p5_crypt everything fails.
     Shows just simple error that can't install and that's it.

Q: What is the laptop spec?
A: It's VPCZ21E5C:
    i7-2620m, 2/4
    8gb ram 1333mhz
    2x samsung 128gb ssd
    no idea what motherboard, but it has fakeraid in bios

Q: what about fdisk -l?
A: 
```
Disk /dev/sda: 4009 MB, 4009754624 bytes
126 heads, 22 sectors/track, 2825 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088545

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     7831551     3914752    b  W95 FAT32

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00012aa1

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6ff9

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/md0: 256.1 GB, 256071335936 bytes
2 heads, 4 sectors/track, 62517416 cylinders, total 500139328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 8192 bytes
Disk identifier: 0x000753a1

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1              64     2050047     1024992   83  Linux
/dev/md0p2         2050062   500139247   249044593    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/md0p5         2050064   500139247   249044592   83  Linux

Disk /dev/mapper/md0p5_crypt: 255.0 GB, 255019565056 bytes
255 heads, 63 sectors/track, 31004 cylinders, total 498085088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 8192 bytes
Disk identifier: 0x00000000
```

[COLOR=#ff0000]IT SHOWS STATE FROM LIVE USB SO /dev/sda IS USB, AND AFTER INSTALL WITH FAILED GRUB.[/COLOR]

Q: What shows lvm> [any command]
A: It shows, that there are no any groups, or just prints basic disk info, that was previously in fdisk -l.

---------------------------------------------------------------------------------------------------------------------------------------------------------

All right, now what do I need/want?
Well, first, I would like to have ANY debian/ubuntu/mint installed with true software RAID0...
...and if it will be successful, then I would like to learn how and why it wasn't working...
...then I would like to learn how to install with ALL debians/ubuntus/mints with this configuration...
...so mabye I will have enough informations to create a tutorial, so everyone can have secure and fast ubuntu! :D

---

### Post by Kirboosy on 2013-09-13
I would recommend setting the RAID from the BIOS. The Hybrid fake RAID of the BIOS in my opinion is a bit more stable than software RAID. I have a Hybrid RAID on my desktop at home in RAID 0 and I have Ubuntu 13.04 running no problems on it. I did have to use [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") in order to have my GRUB install successfully but that was a minor issue. Just reboot the computer after install back into LiveCD mode and make all the Boot Repair changes.

That being said. The Ubuntu installer since version 12.10 has support for full disk encryption.It should all be fairly straight forward and simple to use.

Hope that helps!
~Caboose

---

### Post by xxx2 on 2013-09-17
ww21 here.
Thank You for reply, but it is not what I need.
I want SOFTWARE RAID0.
There are few reasons why, but it's not topic about it - my first post is already too long ;[

---

### Post by Kirboosy on 2013-09-18
Well try this then. The official documentation takes you through it step by step

[Software RAID Community Documentation ]("https://help.ubuntu.com/community/Installation/SoftwareRAID#Configuring_the_RAID")

---

