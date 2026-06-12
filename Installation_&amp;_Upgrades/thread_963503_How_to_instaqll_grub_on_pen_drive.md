---
title: "How to instaqll grub on pen drive"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by codpawn on 2008-10-30
How to install GRUB on the pen drive
Hi
Iam a total noob to the linux cuz ive just switched from windooze

i heard somewhere that i can install grub to pen drive

i wanna do that cuz i wanna prevent my pc used by my roommates

how can i install grub on a pen drive and boot from it

iam using ubuntu 8.04 with the windooze fuxp dual boot

iam total noob to linux so plz tell me step by step
and i want to be my pc booted when only i connect the pen drive


waiting for ur replys

---

### Post by caljohnsmith on 2008-10-30
So do you want to make it so you can't boot your PC at all unless you boot from the pen drive? With your pen drive connected, how about first posting:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by codpawn on 2008-10-30
I tried that and i got result as following 

```
codpawn@root-wick:~$ sudo fdisk -lu
[sudo] password for codpawn: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x005495b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62910539    31455238+   7  HPFS/NTFS
/dev/sda2        66910725   976768064   454928670    f  W95 Ext'd (LBA)
/dev/sda3        62910540    66910724     2000092+  82  Linux swap / Solaris
/dev/sda5       167766858   377479304   104856223+   7  HPFS/NTFS
/dev/sda6       377479368   976768064   299644348+   7  HPFS/NTFS
/dev/sda7        66910851    86911649    10000399+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2051 MB, 2051013632 bytes
33 heads, 63 sectors/track, 1926 cylinders, total 4005886 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb9ca3dda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     4005885     2002927    6  FAT16
codpawn@root-wick:~$ 

```

---

### Post by caljohnsmith on 2008-10-30
OK, do the following:
```
sudo grub
grub> device (hd0) /dev/sdb
grub> device (hd1) /dev/sda
grub> root (hd1,6)
grub> setup (hd0)
grub> quit
```
Reboot, and you should be able to boot from your pen drive and get the Grub menu screen, but selecting any of the OSes most likely won't work. So select the first Ubuntu entry in the Grub menu, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd1,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. See first if you can get this far, and we can work from here.

---

### Post by codpawn on 2008-10-30
> **caljohnsmith said:**
> OK, do the following:
```
sudo grub
grub> device (hd0) /dev/sdb
grub> device (hd1) /dev/sda
grub> root (hd1,6)
grub> setup (hd0)
grub> quit
```
Reboot, and you should be able to boot from your pen drive and get the Grub menu screen, but selecting any of the OSes most likely won't work. So select the first Ubuntu entry in the Grub menu, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd1,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. See first if you can get this far, and we can work from here.


Do I need to do that every time I boot?
and what if I need to boot into XP?

Regards

---

### Post by caljohnsmith on 2008-10-30
You won't have to do that menu modifying every time you reboot, only once just to get into Ubuntu; then you can modify your menu.lst so that the change is permanent. Also, make sure your BIOS is set to boot your pen drive (USB drive) before your HDD. Let me know how it goes.

---

### Post by codpawn on 2008-10-30
After connecting the pen drive I done what you said and got following 

```
grub> device (hd1) /dev/sda

grub> root (hd1,6)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,6)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

```

and then rebooted my PC and selected to boot from the USB device 
But the following msg was there
```
Please select the proper boot device.
```

and again when i booted from the hard drive 
the Grub loaded normally.

And yes the pen drive's file system is fat16

---

### Post by caljohnsmith on 2008-10-30
Some BIOSes will refuse to boot a drive unless one of the partitions is marked as bootable, which is probably why you got that error. So, to mark the sdb1 partition as bootable, try the following:
```
sudo fdisk /dev/sdb
```
Press "a", then "1", then "w", and fdisk should quit. Next do:
```
sudo fdisk -l
```
And it should show sdb1 with an asterisk * meaning it marked as bootable. If it does, go ahead and reboot and try again.

---

### Post by codpawn on 2008-10-30
1- I marked sdb1 as bootable.
2- I rebooted my PC booted from the pen drive.
3- And my BIOS was showing as:
   ```
Verifying DMI pool data
         _
``` 
    And the cursor was blinking.
4- I booted back to Ubuntu and Checked the pen drive it was empty 

and i think  that is the problem so again Iam posting result of 
```
sudo fdisk -lu 
```
```
codpawn@root-wick:~$ sudo fdisk -lu
[sudo] password for codpawn: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x005495b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62910539    31455238+   7  HPFS/NTFS
/dev/sda2        66910725   976768064   454928670    f  W95 Ext'd (LBA)
/dev/sda3        62910540    66910724     2000092+  82  Linux swap / Solaris
/dev/sda5       167766858   377479304   104856223+   7  HPFS/NTFS
/dev/sda6       377479368   976768064   299644348+   7  HPFS/NTFS
/dev/sda7        66910851    86911649    10000399+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2051 MB, 2051013632 bytes
33 heads, 63 sectors/track, 1926 cylinders, total 4005886 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb9ca3dda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     4005885     2002927    b  W95 FAT32
codpawn@root-wick:~$ 

```

---

### Post by caljohnsmith on 2008-10-30
You're pen drive will appear empty since we installed Grub to the MBR (Master Boot Record) of the pen drive, and pointed it back to your sda drive for Grub's boot files; thus there are no extra boot files or modifications to your sdb drive other than changing its MBR, so that's OK. :)

The "Verifying DMI pool data" error you are getting sounds like a BIOS issue with booting your pen drive, because in the least you should get a Grub error if the drive is booting at all. Have you ever booted from a USB drive from that computer before? You probably will have to tweak your BIOS settings to get it to boot. Just look for anything in your BIOS related to your drives (especially anything about DMI and USB), change the parameters one at a time, and see if you can boot the USB drive. I would recommend writing down the BIOS settings you change so you can always revert back to the original settings if necessary. Good luck and let me know how it goes.

---

### Post by codpawn on 2008-10-30
I've tried everithing same problem 

board freezes at Verifing DMI pool data 

and BTW Iam using XFX630i

---

### Post by caljohnsmith on 2008-10-30
Are you at least giving your BIOS a minute or two to update its DMI data when it gives you that message "verifying DMI pool data"? Do you have a BIOS setting for enabling/disabling internal and external CPU cache? Do you have any other BIOS settings related to LBA, CHS, RAID, AHCI vs. IDE, ACPI, etc? Those are all the BIOS settings you could change to see if it helps.

---

### Post by meierfra. on 2008-10-30
> grub> device (hd1) /dev/sda

grub> root (hd1,6)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,6)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.


Did you also do "device (hd0) /dev/sdb"  ?

---

### Post by codpawn on 2008-10-31
> **caljohnsmith said:**
> Are you at least giving your BIOS a minute or two to update its DMI data when it gives you that message "verifying DMI pool data"? Do you have a BIOS setting for enabling/disabling internal and external CPU cache? Do you have any other BIOS settings related to LBA, CHS, RAID, AHCI vs. IDE, ACPI, etc? Those are all the BIOS settings you could change to see if it helps.

Ive tried changing each and every setting in my BIOS.
And I was waiting near about 5to6 minutes at the "verifying dmi pool data" step.:confused:

---

### Post by codpawn on 2008-10-31
> **meierfra. said:**
> Did you also do "device (hd0) /dev/sdb"  ?

No I didn't done that.

---

### Post by caljohnsmith on 2008-10-31
How about going through the steps in post #4 again, and this time be careful to include all the commands. After that, try and boot your USB stick again and let me know what happens.

---

### Post by codpawn on 2008-10-31
Ive Repeted the 4th step again and the problem was same.

And afterwords something gone wrong, Now Iam getting the GRUB error 17 while booting 

right now iam on live 8.10 and tried fixing that by following tutorial
```
http://ubuntuforums.org/showthread.php?t=767189
```

but iam getting  
Error 15:File not found 

so again
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x005495b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            4166       60801   454928670    f  W95 Ext'd (LBA)
/dev/sda3            3917        4165     2000092+  82  Linux swap / Solaris
/dev/sda5           10444       23497   104856223+   7  HPFS/NTFS
/dev/sda6            4166        5410    10000399+  83  Linux
/dev/sda7           23498       60801   299644348+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 2051 MB, 2051013632 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d23c23a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         249     2000061    b  W95 FAT32

```

Iam messed up.
And sorry for asking it again :(

---

### Post by meierfra. on 2008-10-31
> GRUB error 17 while booting 

Do you get Grub error 17 after selected Ubuntu at the Grub menu?  Or do you get the  error before the Grub menu appears?

---

### Post by codpawn on 2008-10-31
> **meierfra. said:**
> Do you get Grub error 17 after selected Ubuntu at the Grub menu?  Or do you get the  error before the Grub menu appears?

It was before Grub  menu appearing
But now Ive Fixed my Xp's Mbr and booted into XP

Can I do a fresh install of Ubuntu 8.10 or repair the Grub??

---

### Post by codpawn on 2008-10-31
Finally I fixed the both boot loaders and back in Ubuntu :)

---

