---
title: "Grub lost on upgrade ?"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by ronnie.s on 2014-10-06
Hello. I have been using Ubuntu 10.04 since 2010 on my laptop. I had installed Ubuntu 10.04 alongside Windows 7 and this was working perfectly. Since the last few months my laptop internal hard drive is giving me a lot of problems these days and so I decided to install Ubuntu 14.04 on my 1 TB external hard drive and use it from there. I proceeded to do this as follows 

1. I was already using my external hard drive and so I made space for the new operating system. I made partitions so that in all there are 4 partiions. The last two partitions contain my data and I intended to use the first two partitions for / and /home.

2. I installed Ubuntu 14.04 from a USB flash drive and selected install.

3. I selected "Something else", and I also chose my external hard drive as the place where the boot loader should be installed.

4. I installed Ubuntu 14.04. 

5. Upon restarting the machine with my external hard drive plugged in, it detected Ubuntu 14.04 and booted. However, after I did sudo apt-get update and sudo apt-get upgrade and restarted, it refuses to detect the OS on my external hard drive. It bypasses my external hard drive and goes into my internal hard drive, and then only detects the old 10.04 and windows.

I'm adding some extra information which might be useful.

There are now 4 partitions on my external hard drive in the following order 

sdb1* sdb4 sdb2 sdb3 (the star indicating boot)

Just to give all information, I am attaching the output of ```
sudo fdisk -lu
```

```
ronnie@ronnie-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8457ecea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      273104      136521   de  Dell Utility
/dev/sda2   *      274432    20021247     9873408    7  HPFS/NTFS
/dev/sda3        20021248   143986687    61982720    7  HPFS/NTFS
/dev/sda4       143986699   625137344   240575323    5  Extended
/dev/sda5       143988736   190884329    23447797   83  Linux
/dev/sda6       190884393   619273619   214194613+  83  Linux
/dev/sda7       619273683   625137344     2931831   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca33c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    91602629    45801283+  83  Linux
/dev/sdb2       206322795   632639699   213158452+  83  Linux
/dev/sdb3       632639700  1953520064   660440182+  83  Linux
/dev/sdb4        91602630   206322794    57360082+  83  Linux

Partition table entries are not in disk order
ronnie@ronnie-laptop:~$ 

```

and screenshots of gparted 

[ATTACH=CONFIG]256987[/ATTACH][ATTACH=CONFIG]256988[/ATTACH]

Any help would be really appreciated. Thanks.

---

### Post by ronnie.s on 2014-10-06
Hello. I have been using Ubuntu 10.04 since 2010 on my laptop. I had  installed Ubuntu 10.04 alongside Windows 7 and this was working  perfectly. Since the last few months my laptop internal hard drive is  giving me a lot of problems these days and so I decided to install  Ubuntu 14.04 on my 1 TB external hard drive and use it from there. I  proceeded to do this as follows 

1. I was already using my external hard drive and so I made space for  the new operating system. I made partitions so that in all there are 4  partiions. The last two partitions contain my data and I intended to use  the first two partitions for / and /home.

2. I installed Ubuntu 14.04 from a USB flash drive and selected install.

3. I selected "Something else", and I also chose my external hard drive as the place where the boot loader should be installed.

4. I installed Ubuntu 14.04. 

5. Upon restarting the machine with my external hard drive plugged in,  it detected Ubuntu 14.04 and booted. However, after I did sudo apt-get  update and sudo apt-get upgrade and restarted, it refuses to detect the  OS on my external hard drive. It bypasses my external hard drive and  goes into my internal hard drive, and then only detects the old 10.04  and windows.

I'm adding some extra information which might be useful.

There are now 4 partitions on my external hard drive in the following order 

sdb1* sdb4 sdb2 sdb3 (the star indicating boot)

Just to give all information, I am attaching the output of ```
sudo fdisk -lu
```
```
ronnie@ronnie-laptop:~$ sudo fdisk -lu
sudo: timestamp too far in the future: Oct  7 00:36:56 2014
[sudo] password for ronnie: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8457ecea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      273104      136521   de  Dell Utility
/dev/sda2   *      274432    20021247     9873408    7  HPFS/NTFS
/dev/sda3        20021248   143986687    61982720    7  HPFS/NTFS
/dev/sda4       143986699   625137344   240575323    5  Extended
/dev/sda5       143988736   190884329    23447797   83  Linux
/dev/sda6       190884393   619273619   214194613+  83  Linux
/dev/sda7       619273683   625137344     2931831   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca33c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    91602629    45801283+  83  Linux
/dev/sdb2       206322795   632639699   213158452+  83  Linux
/dev/sdb3       632639700  1953520064   660440182+  83  Linux
/dev/sdb4        91602630   206322794    57360082+  83  Linux

Partition table entries are not in disk order
ronnie@ronnie-laptop:~$ 

```

and screenshots of gparted 
[ATTACH=CONFIG]256989[/ATTACH][ATTACH=CONFIG]256990[/ATTACH]

Any help would be appreciated. Thanks.

---

### Post by grahammechanical on 2014-10-06
It is my guess that the internal hard drive has the boot priority and the only Grub being loaded is the Grub of Ubuntu 10.04 which does not know about Ubuntu 14.04. As far as I can see you have two options.

a) use the BIOS/UEFI to choose to load from the external hard disk.

b) load into Ubuntu 10.04 and run

```
sudo update-grub
```

That will update the Grub configuration file of the 10.04 Grub boot loader. The printout will show if Ubuntu 14.04 on the external hard drive is being detected.

Regards.

---

### Post by grahammechanical on 2014-10-06
Why have are you dual posting? You have the same post in the New to Ubuntu section and a duplicate in the Installation and Upgrades section. That is not good manners.

[http://ubuntuforums.org/showthread.php?t=2247192](http://ubuntuforums.org/showthread.php?t=2247192)

---

### Post by oldfred on 2014-10-06
From Live installer run the summary report from Boot-Repair and post the link. 
If you tell it that sdb is external it should just re-install grub to sdb. And it can do a full uninstall/reinstall of all of grub if required. Best not to run auto fix, as that likes to just install one grub to all drives.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by coffeecat on 2014-10-06
Threads merged. Please do not post duplicates in different parts of the forum. This causes confusion and duplication of effort from those helping.

---

### Post by ronnie.s on 2014-10-07
I am sorry for dual posting. I tried looking for a way to transfer the post to "Installations and hardware" but when I could not, I just posted it there again. 

After booting in to 10.04 I plugged in my external hard drive and gave the command "sudo update-grub". It detected the 14.04 in my external hard drive. Now when I switch on my computer with my external hard drive plugged in, one of the following two things happens 

1. It loads a grub 1.98 menu (this is from my 10.04) which contains as an option ubuntu 3..... , however, when I choose this option I get an error that the device is not found, followed by an error that (hd1,1) missing or something to that effect. I go to the grub menu and type "ls" and see that it detects only hd0 (hd0,1) (hd0,2) ... (hd0,7) and does not detect hd1, which is my external hard drive. I press ctrl+alt+del and start again, this time i go to the boot menu. It turns out that sometimes the boot menu has an option +USB but at other times it does not have such an option. The first option is removable drives, the second option is +USB (whenever this is there), the third is +HDD ( I guess this refers to my internal hard drive).

2. On the few occasions that I went to the boot menu and found that +USB option is there, I choose it and then I get a grub 2.02 menu which has 14.04, 10.4 and windows. 

Sometimes when I chose the option to boot from removable drive, I get the message "Media not found, check cable" followed by "Operating system not found", followed by "Press any key to continue". I noticed that sometimes upon going to the boot menu after these messages shows up +USB and then choosing that I am able to boot into my external hard drive.

Could it be the case that there is some problem with my machine that it does not always correctly detect my external hard drive? Thanks.

I ran Boot-Repair and here is the result 
```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 13170079 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for .
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       273,104       273,042  de Dell Utility
/dev/sda2    *        274,432    20,021,247    19,746,816   7 NTFS / exFAT / HPFS
/dev/sda3          20,021,248   143,986,687   123,965,440   7 NTFS / exFAT / HPFS
/dev/sda4         143,986,699   625,137,344   481,150,646   5 Extended
/dev/sda5         143,988,736   190,884,329    46,895,594  83 Linux
/dev/sda6         190,884,393   619,273,619   428,389,227  83 Linux
/dev/sda7         619,273,683   625,137,344     5,863,662  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    91,602,629    91,602,567  83 Linux
/dev/sdb2         206,322,795   632,639,699   426,316,905  83 Linux
/dev/sdb3         632,639,700 1,953,520,064 1,320,880,365  83 Linux
/dev/sdb4          91,602,630   206,322,794   114,720,165  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        B643-1278                              vfat       
/dev/sda2        52B44479B4446219                       ntfs       RECOVERY
/dev/sda3        2C2A46692A462FDE                       ntfs       OS
/dev/sda5        8bd64e6b-73e6-482c-9ce4-d830c96cc66b   ext4       
/dev/sda6        f86f588f-4496-4057-ae76-c5d85d375471   ext4       
/dev/sda7        cf1e34da-8fb9-471d-bb2b-46947cf749ff   swap       
/dev/sdb1        08464d7c-e5b6-46a7-98d5-81e0b5bda01a   ext4       
/dev/sdb2        3f824394-263b-44ff-a7c7-de1120ebde17   ext4       Work
/dev/sdb3        54dad381-2d43-456e-b8f4-8725dcb6653b   ext4       Ronnie
/dev/sdb4        449cc952-54ed-43da-a051-d9bfdf4cf121   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb2        /media/ronnie/Work       ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb3        /media/ronnie/Ronnie     ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb4        /home                    ext4       (rw)




```

---

### Post by yancek on 2014-10-07
I would start by checking that the cable for the USB is securely plugged in as suggested in your messages.  You seem to have all the correct files where they should be and the menuentry for 14.04 looks correct.

---

### Post by ronnie.s on 2014-10-07
Every time I plug in the USB, the green light goes on perfectly. Moreover, in 10.04, there has never been a problem with the external hard drive. That is the reason I find it a bit hard to believe that there could be something wrong with the cables or the external hard drive. Perhaps from now on everything will work smoothly. 

Would you recommend I try repair using boot-repair? Thanks.

Ok I completely screwed everything by doing a recommended repair. Now on switching on my laptop directly goes into windows. If I plug in my external hard drive and then switch on the laptop, then every once in a blue moon it gives me the option of booting from a usb storage and then I can choose 14.04 in my external hard drive or I can choose 10.04 in my internal hard drive (my external hard drive carries this information that there is a 10.04 on sda5). What should I do? 

The external hard drive which is a Seagate is detected on other machines and I can boot from it without any problems. Any help would be of tremendous use.

I managed to boot into 14.04 and then once again ran boot-repair. This has completely messed up everything, though this time I have this link which was given to me once boot-repair completed 

[http://paste.ubuntu.com/8516862](http://paste.ubuntu.com/8516862)

Now the status of my computer is that without the external hard drive plugged in if I switch it on, then I get the following errors
PXE-E61 Media test failure check cable
Another similar error 
Operating system not found 
On pressing any key .... 
Windows ..... ntoskrnl.exe not found

After repeating ctrl+alt+del and F12 a few times, I always eventually get a +USB option in my boot menu. From this I can boot into Windows or Ubunto 14.04 or Ubuntu 10.04. Can someone please help me. Thanks.

---

