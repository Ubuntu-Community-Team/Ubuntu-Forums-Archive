---
title: "INstalled but major problems , please help quick"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by saadghauri on 2005-10-13
Hi,
 Well i installed ubuntu but then bad stuff happened , as follows :

1) Grub installation failed so i installed lilo on mbr , now my windows 2000 cant be booted (it still exists on my hd)

2) i cant access any partition aside from the one i installed ubuntu on , ubuntu can read fat32 partitions right ? mu other two partitions are fat32 but ubuntu doesn't even show them

3)  I can't change the screen resolution from 640*480 to anything else :(

Please help me

---

### Post by adwait on 2005-10-13
1) Add the windows entry to the LILO config file, don't really know how......google it
2)You need to mount the partitions before you can access them. Use the command
```
df
``` 
This will show you all the partitions on the system. In order to mount a partitions, use the command
```
 sudo mount /dev/hdX /mnt/location -t <filesystem type> 
```
Look at the man pages for more details. 
If you want to mount the drives on booting, you can do that by adding them to the fstab file. To do this, open the fstab file using
```
sudo gedit /etc/fstab 
```
Now add the line
```
/dev/hdX <TAB>  </mount/location>  <TAB> <fs type>
3) To fix the resolution, try running
[code]sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by saadghauri on 2005-10-13
uwhen i use the df command it says this :

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda5              7692876   1393952   5908148  20% /
tmpfs                   127644         0    127644   0% /dev/shm
/dev                   7692876   1393952   5908148  20% /.dev
none                      5120      2840      2280  56% /dev
/dev/hdb                630994    630994         0 100% /media/cdrom0

PLease tell me what to do next

---

### Post by adwait on 2005-10-13
Uuh sorry, that lists the mounted partitions. I meant use
```
sudo fdisk -l 
```

---

### Post by saadghauri on 2005-10-13
it shows this :
 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         973     7815591    7  HPFS/NTFS
/dev/hda2             974        4865    31262490    f  W95 Ext'd (LBA)
/dev/hda5             974        1946     7815591    7  HPFS/NTFS
/dev/hda6            1947        2919     7815591    b  W95 FAT32
/dev/hda7            2920        4865    15631213+   b  W95 FAT32
what do i do now ?? thanks for replying

---

### Post by adwait on 2005-10-13
Well, your three windows drives are /dev/hda7/6/1. To mount these, first create empty directories in the mnt directory using 
```
sudo mkdir /mnt/a
```

Now add the line as follows to fstab
```
/dev/hda1 <TAB> /mnt/a <TAB> auto
```

That will mount that partition at mnt/a. now u can view the contents by browsing throught /mnt/a. Similarly do this for /dev/hda6 and /dev/hda7 changing /mnt/a to /mnt/b and /mnt/c (Or whatever you want to name it)

---

### Post by saadghauri on 2005-10-13
bash: /dev/hda6: Permission denied
 ITS GIVING THIS ERROR :(

---

### Post by saadghauri on 2005-10-13
[QUOTE=adwait]Well, your three windows drives are /dev/hda7/6/1. To mount these, first create empty directories in the mnt directory using 
```
sudo mkdir /mnt/a
```

Now add the line as follows to fstab
```
/dev/hda1 <TAB> /mnt/a <TAB> auto
```

That will mount that partition at mnt/a. now u can view the contents by browsing throught /mnt/a. Similarly do this for /dev/hda6 and /dev/hda7 changing /mnt/a to /mnt/b and /mnt/c (Or whatever you want to name it)[/QUOTE]

WHats the fstab ?? sorry i am new

---

### Post by adwait on 2005-10-13
fstab stands for file system table. It is a file which holds information about all the partitions and where they are to be mounted.

---

### Post by adwait on 2005-10-13
[QUOTE=saadghauri]bash: /dev/hda6: Permission denied
 ITS GIVING THIS ERROR :([/QUOTE]
When does it give this error?

---

### Post by saadghauri on 2005-10-13
sorry i was doing something wrong when i was getting that error ..
However fstab is read only and i can't edit it .. what do i do ?

---

### Post by Feirax on 2005-10-13
[QUOTE=saadghauri]sorry i was doing something wrong when i was getting that error ..
However fstab is read only and i can't edit it .. what do i do ?[/QUOTE]

sudo gedit fstab.conf should do it.

---

### Post by adwait on 2005-10-13
```
 sudo gedit /etc/fstab 
```

---

### Post by saadghauri on 2005-10-13
[QUOTE=Feirax]sudo gedit fstab.conf should do it.[/QUOTE]

That command opens up a blank file .. not the fstab file in /etc :(

---

### Post by saadghauri on 2005-10-13
i edited the fstab .. how do i access the files now ? when i go to :open location" it shows empty on all three ....

---

### Post by saadghauri on 2005-10-13
fixed that .. thanks a LOT u guys ...

---

