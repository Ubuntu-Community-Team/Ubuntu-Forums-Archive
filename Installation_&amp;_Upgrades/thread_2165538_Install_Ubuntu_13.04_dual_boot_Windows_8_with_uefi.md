---
title: "Install Ubuntu 13.04 dual boot Windows 8 with uefi"
date: 2013-08-05
forum: Installation &amp; Upgrades
---

### Post by francesco4 on 2013-08-05
Hi. I want install ubuntu 13.04 on my pc with motherboard asus p9x79(uefi). My pc have two hard disk, the first is ssd samsung with 128gb of space, second is western digital with 2tb of space. Some time ago i installed windows 8 on my ssd infact iif i lunch software of partition i read this information:


                 file system     capacity        used       unused           Type                         information 
disk1 (MBR)
/dev/sda
        /dev/sda1                      ntfs                                  100 MB                         35 MB        65 MB         primary                  reserved for the system
       /dev/sda2       ntfs            1,9TB          388GB        1,6TB         primary                    (i stored my data)

disk2 (MBR)
/dev/sdb
/dev/sdb1       ntfs            119GB          96GB         22GB          primary                  (there is windows 8 O.S.) 

My motherboard is uefi. I have partiotioned sda2, i have created 200gb of space ntfs so as to have thi situation:


                 file system     capacity        used       unused           Type                         information 
disk1 (MBR)
/dev/sda
        /dev/sda1                      ntfs                                  100 MB                         35 MB        65 MB         primary                  reserved for the system
       /dev/sda2       ntfs            1,6TB          388GB        1,2TB         primary                    (i stored my data)
/dev/sda3       ntfs            220GB            0            220GB         primary                   (in this partition i want installl ubuntu) 

disk2 (MBR)
/dev/sdb
/dev/sdb1       ntfs            119GB          96GB         22GB          primary                  (there is windows 8 O.S.) 

Then i have unable secureboot from my bios , i am go to bios into section secure boot, there is selection box, default there was windows OS uefi, i have selectioned other O.S., then i have save and reset. 
After with gparted create three partition with sda3. ihave this situation:



                 file system     capacity        used       unused           Type                         information 
disk1 (MBR)
/dev/sda
        /dev/sda1                      ntfs                                  100 MB                         35 MB        65 MB         primary                  reserved for the system
       /dev/sda2       ntfs            1,6TB          388GB        1,2TB         primary                    (i stored my data)
/dev/sda3       ext2           512MB            0            512MB        primary                           (boot)
/dev/sda4       ext4           215GB            0            215GB         logical                           (root)
/dev/sda5      linux-swap     4GB              0             4GB           logical                           (swap)


disk2 (MBR)
/dev/sdb
/dev/sdb1       ntfs            119GB          96GB         22GB          primary                  (there is windows 8 O.S.)

Then i have installed ubuntu manually. I have assigned  pount of mount so:
sda3        /boot         ext2                                             formatted yes
sda4        /              ext4 with journaling                          formatted yes
sda5       /swap         (nothing because is automaticaly)      formatted no

I have install ubuntu, but after reboot don't start boot manager where i can select wich s.o. i want start, but start windwos 8. I have tried with EasyBCD 2.2 i have created grub2  but don' work.
Help me i have read many guides but i can not install ubuntu 13.04.

What i do? Why don't work? 

Thanks all and sorry form my english.

---

### Post by oldfred on 2013-08-05
You can only boot UEFI with drives partitioned with gpt partitioning not MBR(msdos). Windows only boots from gpt with UEFI, Ubuntu will boot from gpt with UEFI or BIOS/CSM/Legacy, and if drive is MBR both Windows & Ubuntu will only boot in BIOS mode.
If dual booting both systems need to be installed in the same boot mode either both UEFI or both BIOS. If two drives then both drives need to be gpt or both MBR although with BIOS mode Windows could be MBR and Ubuntu gpt.

See the link in my signature for dual booting two UEFI systems and lots of info on UEFI. 

Windows has specific partition requirements.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

This is my suggested partitioning for Ubuntu. If two drives have an efi partition on both drives at start of drive, but only one may be used by default.
      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by francesco4 on 2013-08-05
I have created this partition:

disk1 (MBR)
/dev/sda
        /dev/sda1                      ntfs                                   100 MB          primary                   reserved for the system
       /dev/sda2       ntfs            1,6TB          primary                    (i stored my data)
/dev/sda3       ext2           512MB        primary                           (boot)
/dev/sda4       ext4           215GB logical                           (root)
/dev/sda5      linux-swap     4GB logical                           (swap)


disk2 (MBR)
/dev/sdb
/dev/sdb1       ntfs            119GB primary                  (there is windows 8 O.S.)

I have installed ubuntu in sda3 with /boot sda4 with / and sda5 with swap. Afer reboot pc start with windows 8. There isn't boot manager windows 8 where i can choice ubuntu or windows 8. Why? What i can do for my problem?

---

### Post by oldfred on 2013-08-05
You are in BIOS with MBR mode. If you are booting Windows is it booting from sda and has the 100MB Windows boot partition in sda1 to boot the Windows install in sdb1?

Best to see details. 
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

