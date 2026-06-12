---
title: "[SOLVED] sata hard disks (i am corn-fused)"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Homunculi on 2007-05-06
installing a fresh install
i guess i am a little confused about this ... 
i have always had ide eide hard disks in my machines 

well now i have 2 sata drives and i got the 2nd one on a deal 
but here is the situation i had the one 250gb sata drive in and windoze installed on it 
with a 250gb ide drive that had linux installed on it 

now i got a sata 320gb 16mb cache for $67 bucks brand new 

here is the problem grub is loaded on the 1 sata drive (the 250 with windoze )
i installed the new 320gb one and attached my 2nd dvd burner on the ide chain 
now grub will come up but will not boot linux 
boots windoze ok ... but i cannot get it to see the sata drives to update it's config 
and i have ran the install 2 times now thinking it would reinstall grub on the 1st sata drive and all will be ok .... not ! :(

---

### Post by Big Ed on 2007-05-06
320 GB Sata for $67 is a good deal!

I think your drive numbers have changed.  So now one of the Grub menu items is pointing to the wrong drive.  Have a look at this:
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/HOWTO_GRUB_BOOTLOADER_AND_TROUBLE_SHOOTER](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/HOWTO_GRUB_BOOTLOADER_AND_TROUBLE_SHOOTER)

Scroll down to TROUBLESHOOTING GRUB AT BOOT MENU near the bottom.  It explains (better than I could) how to find what drive/partition your boot kernel is on.

Note that Grub doesn't care about ide/sata, it just numbers them hd0, hd1, hd2, etc.

HTH,
Ed

---

### Post by Homunculi on 2007-05-06
ran a install to set grub on sda1 and get windows booting back and (hoped that ubuntu would boot) 
no go 

i get error 17 or something like that .... 
reading you help page i will need a little time to read and reread this out .. 
i was just hopeing to get both dvd burners back and could not resist the extra space ... 

if anyone has the quik trik .... please let me know 


 :guitar: 

rock on

---

### Post by confused57 on 2007-05-06
Boot the live cd, open a terminal, & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by Homunculi on 2007-05-07
here is the fdisk -l information ... 
on sata 2 is the info to the /usr partition 
so that drive 2 look like 
swap 
/ (root) 
/usr
/home
and so on (additional storage partitions)



Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       30401   182755440    f  W95 Ext'd (LBA)
/dev/sda5            7650       19122    92156841    7  HPFS/NTFS
/dev/sda6           19123       30401    90598536    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         122      979933+  82  Linux swap / Solaris
/dev/sdb2             123        4985    39062047+  83  Linux
/dev/sdb3            4986       17143    97659135   83  Linux

---

### Post by confused57 on 2007-05-07
Can you mount your root partition on your 320 Gb drive?:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Read the above link, but it would be something like this:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdb2 /media/ubuntu
```

then you examine the contents of your menu.lst, if it mounts OK:
```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

I noticed your boot flag wasn't on(*) in your root partition, don't know if that would make a difference or not.

I don't know if there might be something in your bios that you need to turn on for a larger hard drive(LBA?).

---

### Post by Homunculi on 2007-05-07
ok i got it ... (gedit does not work in kubuntu ) 

do not know what i did but everything started working 
everything in the menu.lst looked normal 
all i did was ran a reinstall and i got out some old notes 

this is what i did when making the partitions (then everything worked ) 
i made partitions as follows :

swap 
/boot
/ (root)
/user
/home
vfat ... and on 

do not know what happened ... 
but i am happy !! 
:guitar: 
rock on ppl .... 

and thank you for all the help :)

---

### Post by confused57 on 2007-05-07
Great, glad YOU got it working.  You're correct Kubuntu (kde) uses kwrite, instead of gedit.

---

### Post by Homunculi on 2007-05-17
ok this is the deal ... the disk was a great deal i went and got another :)

i tried just installing from the live cd  and set all my partitions with the live cd 
/swap 
/root
/boot 
and so on 

waited for the install to complete and no problems found 

then i went it with my utility disk and defined the partitions (raw) set an active root partition 

ran the install and set the mount points .... after the install was complete grub could not find boot .... 

and i redid step one again ... it boots ...  
well after this i just slaved the new disk into my big tower as a slave 

and the only thing i can think of is the partition manager loved it when it defined the partitions ... and hated when i used a second party software 

i do not know if this will help every one but i hope it helps some :) 
again thank every one for the help when i need it :)

:guitar:
rock on

---

