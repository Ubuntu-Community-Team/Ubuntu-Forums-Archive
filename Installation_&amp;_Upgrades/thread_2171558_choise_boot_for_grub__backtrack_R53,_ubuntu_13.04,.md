---
title: "choise boot for grub : backtrack R53, ubuntu 13.04, freebsd 9.1d"
date: 2013-08-31
forum: Installation &amp; Upgrades
---

### Post by philo_71 on 2013-08-31
goodday,
I have a quad core Q6600 with a 500 GB hard drive, I have to install the OS in the following order, backtrack 5R3, freebsd 9.1, ubuntu 13.04.
I am currently dual boot: BackTrak and ubuntu.
ubuntu since I did a "fdisk-l" I get this result:
----------------------------------------------------------------------------------------------------------------------------------[INDENT]root@dct-zeus:/home/administrateur# fdisk -l
Attention :  identifiant de table de partitions GPT (GUID) détecté sur  « /dev/sda » ! L'utilitaire sfdisk ne prend pas GPT en charge. Utilisez  GNU Parted.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x00000000
Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1               1   976773167   488386583+  ee  GPT
root@dct-zeus:/home/administrateur#


[/INDENT]
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
I do not understand too! it does not develop the sheets!

I see in GPARTED freebsd partition / dev/sda5

I have tried this:
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
sudo  gedit  /etc/grub.d/40_custom
menuentry "FreeBSD 9.1" {
set root='(hd0,5)'
chainloader +1
}
sudo  update-grub

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
But alas this is not conclusive, I put a triple boot windows, ubuntu, freebsd on my laptop while walking very well!


regards
Philippe

---

### Post by oldfred on 2013-08-31
You are showing gpt partitioning. fdisk currently does not work on gpt partitioned drives. You can use parted or install gdisk which is the fdisk for gpt drives.

sudo apt-get install gdisk

       sudo parted /dev/sda unit s print

 sudo gdisk -l /dev/sda

      
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

But Windows only boots from gpt partitioned drives with UEFI. And all systems need to be installed in BIOS boot mode or UEFI boot mode to easily dual boot. Ubuntu will boot from gpt partitioned drives with either UEFI or BIOS, not sure about other systems. 
FreeDos was designed back with BIOS and MBR(msdos) partitioning. You may not be able to dual boot from grub menu if booting with UEFI. But should be able to go into UEFI/BIOS menu, turn on CSM/BIOS mode and directly boot it.

There probably is a French version as the developer is French. 

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by philo_71 on 2013-08-31
hi,
i do sudo gdisk -l /dev/sda:
> 
root@dct-zeus:/home/administrateur# sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): F87B52FE-1183-11E3-8123-BC5FF499F07F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 27303951 sectors (13.0 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1       400478208       550313983   71.4 GiB    EF00  
   2       550313984       940939263   186.3 GiB   0700  
   3       968243200       976773119   4.1 GiB     8200  
   4              34             161   64.0 KiB    EF02  
   5             162       392167457   187.0 GiB   A503  
   6       392167458       400478207   4.0 GiB     A502  
root@dct-zeus:/home/administrateur# 




can i make choise for boot freebsd'os ??

---

### Post by oldfred on 2013-08-31
You are showing a ef00 which is the efi partition used for UEFI boot.
But you also show a ef02 which is bios_grub for BIOS boot with grub2.
So I do not know for sure which way grub is configured to boot. For UEFI you would have grub-efi installed and for BIOS you would have grub-pc installed. 

But you choose how to boot UEFI or BIOS is from UEFI menu. 
And I think FreeDos would only boot from UEFI in BIOS boot mode, and may not work on gpt partitioned drives.

---

### Post by philo_71 on 2013-09-01
hello,
this is a new configuration  , freebsd 9.1, ubuntu 13.04.

with this commands :
> sudo apt-get install gdisk
sudo parted /dev/sda unit s print
sudo gdisk -l /dev/sda

folloing >>


```
root@dct-zeus:/home/administrateur# sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 87291BB7-131A-11E3-9F9D-BC5FF499F07F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 81706861 sectors (39.0 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34             161   64.0 KiB    EF00  
   2            4096       487264255   232.3 GiB   A503  freebsd
   3       966787106       975175713   4.0 GiB     A502  
   4       487264256       878866431   186.7 GiB   EF00 ubuntu /  
   5       878866432       886679551   3.7 GiB     8200  
   6            2048            4095   1024.0 KiB  EF02  
root@dct-zeus:/home/administrateur# 

```






> sudo  gedit  /etc/grub.d/40_custom
Puis ajouter les lignes suivantes :

menuentry "FreeBSD 9.1" {
insmod ufs2
set root='(hd0,2)'
chainloader +1
}

i save and i do :
sudo  update-grub 


i don't anderstand it doesnt work !!

---

### Post by oldfred on 2013-09-01
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

