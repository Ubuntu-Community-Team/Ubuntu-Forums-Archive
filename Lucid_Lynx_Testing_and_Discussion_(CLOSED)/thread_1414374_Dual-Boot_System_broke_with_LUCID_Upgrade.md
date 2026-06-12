---
title: "Dual-Boot System broke with LUCID Upgrade"
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TunaCanTommy on 2010-02-23
I recently did an upgrade from Karmic to Lucid (A2) and now my dual-boot system won't boot into my Windows OS. I have Windows on a second internal hard-drive (dev/sdb), Ubuntu is on the first (dev/sda). I get the GRUB menu but when I select Windows the screen goes to black and freezes with the word "GRUB" at the upper left.

I ran the Boot Info Script . . . 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 366183 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 330959 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #1 for /grub.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 352983 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #1 for /grub. No errors found in 
                       the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 358679 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #1 for /grub.
    Operating System:
    Boot files/dirs:   
```

Can I remove GRUB and reinstall to get it working properly ? ?

---

### Post by wilee-nilee on 2010-02-23
Can you also post sudo fdisk -l from the terminal.

---

### Post by TunaCanTommy on 2010-02-23
Certainly . . . 

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x99ef77d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         124      995998+  83  Linux
/dev/sda2             125         248      996030   82  Linux swap / Solaris
/dev/sda3             249       14593   115226212+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x000237f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1958    15727603+   c  W95 FAT32 (LBA)
/dev/sdb2            1959        9729    62420557+  83  Linux

```

---

### Post by wilee-nilee on 2010-02-24
So there are a couple of people on the forums that know how to fix your problem. I am not sure since I see the Boot in sda and sdb. 

This is a bump so you can get seen.

It may be a simple as making sure whatever drive has the original MBR, sounds like the linux one from your description is 1st in the auto boot order from bios, and taking off the boot flag from the windows with gparted. Just remember what you have done none of these methods are permanent, you can go back to where your at.

---

### Post by TunaCanTommy on 2010-02-24
Thanks for your advice . . . I'll try that.

I just spent most of the day trying to reinstall GRUB 2 from a Karmic live CD, as is in the Ubuntu GRUB 2 documentation.

I succeeded - somewhat.  Now I get the sh.grub > prompt and followed the directions to manually load the kernel. That went OK but as the system boots I get "kernel panic" and the system locks up.

I can get into my Linux system by changing the drive boot order in the system BIOS to boot off my Windows installed drive. GRUB comes up and I can select Linux.  Windows won't boot though.

I'll keep 'putzing' around . . 

Might just have to wait for the beta version of Lucid and do a clean install.

Thanks again for your help.

---

### Post by wilee-nilee on 2010-02-24
I think your on the right track it may be that setting the sdb first and booting linux run sudo update-grub may load the W7 there. Either drive but one or the other is the only one with a boot flag. this is how I would approach it but I have limitations.

So I am assuming you know about the sudo update-grub command to update the grub menu.

---

### Post by meierfra. on 2010-02-24
> ```
sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 352983 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #1 for /grub. No errors found in 
                       the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

```

You overwrote the boot sector of your Windows partiton with Grub. I suggest to use testdisk to restore the boot sector from the backup:

Open a terminal in Ubuntu and type
```
sudo apt-get install testdisk

```
(if apt-get cannot find "testdisk" you have to  enable the universe  repository via "System->Administration->Software Sources)
 
 ```
 sudo testdisk /dev/sdb

```


   
First   screen:  Press enter to  "proceed".
Second   screen:  Choose "intel"
Third  screen:  "advanced",
Fourth   screen:  Select the Windows system partition (although it should be slected already)  and choose "boot"
Fifth  screen:  "BackupBS"
Sixth screen:  type "Y" to confirm
 

then press "q" a few times to quit testdisk, reboot and see whether you can boot into Windows.

---

### Post by TunaCanTommy on 2010-02-24
That did it . . . thanks a bunch. :D

Now I have to sort out my Linux GRUB situation . . . all borked up after this.

Thanks again, and I'll mark this solved.

---

