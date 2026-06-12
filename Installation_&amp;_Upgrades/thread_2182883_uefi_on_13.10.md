---
title: "uefi on 13.10"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by ronb19495 on 2013-10-22
I am running 13.10  on my desktop I have just installed a new motherboard its an fatal1ty motherboard my computer has 4 operating systems all on seperate hard drives fedora19,fedora20,linuxmint 15 and ubuntu 13.10 can someone please tell me how to finf if ubuntu is running in uefi mode
regards Ron

---

### Post by fantab on 2013-10-23
You Must give us more info about your computer.. 
So, you had four operating systems on four separate hard drives. Now you've changed just the motherboard, got a new one, right? 
Did the Graphics Card change with the new mobo?
Are you able to boot all your OS with this new mobo?

If you can then post the output of the following:

```
sudo parted -l
sudo fdisk -l
```

If you can't boot into any OS then use a Ubuntu Live DVD/USB and 'Try Ubuntu without installing', open Termianl [Ctrl + Alt + T] and run the above commands.

---

### Post by ronb19495 on 2013-10-23
```
ron@ron-desktop:~$ sudo parted -l
Model: ATA ST3250312AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  525MB  524MB  primary  ext4         boot
 2      525MB   250GB  250GB  primary               lvm


Model: ATA WDC WD10EZRX-00A (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  525MB   524MB   primary  ext4         boot
 2      525MB   1000GB  1000GB  primary               lvm


Model: ATA ST3250318AS (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  216GB  216GB   primary   ext4
 2      216GB   250GB  34.0GB  extended
 5      216GB   250GB  34.0GB  logical   linux-swap(v1)


Model: ATA WDC WD10EARS-003 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  966GB   966GB   primary   ext4            boot
 2      966GB   1000GB  34.0GB  extended
 5      966GB   1000GB  34.0GB  logical   linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora00-root: 53.7GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  53.7GB  53.7GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora00-swap: 16.7GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  16.7GB  16.7GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora00-home: 179GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  179GB  179GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora-root: 53.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  53.7GB  53.7GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora-swap: 16.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  16.7GB  16.7GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora-home: 929GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  929GB  929GB  ext4

``````
ron@ron-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00095c07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1026047      512000   83  Linux
/dev/sda2         1026048   488396799   243685376   8e  Linux LVM

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0008694a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     1026047      512000   83  Linux
/dev/sdb2         1026048  1953523711   976248832   8e  Linux LVM

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005ed3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   421976063   210987008   83  Linux
/dev/sdc2       421978110   488396799    33209345    5  Extended
/dev/sdc5       421978112   488396799    33209344   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004865d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048  1887102975   943550464   83  Linux
/dev/sdd2      1887105022  1953523711    33209345    5  Extended
/dev/sdd5      1887105024  1953523711    33209344   82  Linux swap / Solaris

Disk /dev/mapper/fedora-swap: 16.7 GB, 16718495744 bytes
255 heads, 63 sectors/track, 2032 cylinders, total 32653312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora-swap doesn't contain a valid partition table

Disk /dev/mapper/fedora-home: 929.3 GB, 929269022720 bytes
255 heads, 63 sectors/track, 112977 cylinders, total 1814978560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora-home doesn't contain a valid partition table

Disk /dev/mapper/fedora-root: 53.7 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders, total 104857600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora-root doesn't contain a valid partition table

Disk /dev/mapper/fedora00-swap: 16.7 GB, 16718495744 bytes
255 heads, 63 sectors/track, 2032 cylinders, total 32653312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora00-swap doesn't contain a valid partition table

Disk /dev/mapper/fedora00-home: 179.1 GB, 179126140928 bytes
255 heads, 63 sectors/track, 21777 cylinders, total 349855744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora00-home doesn't contain a valid partition table

Disk /dev/mapper/fedora00-root: 53.7 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders, total 104857600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora00-root doesn't contain a valid partition table
ron@ron-desktop:~$ 

```all the operating systems are booting ok my graphics is on board  intel hd graphics

---

### Post by fantab on 2013-10-23
No, you are NOT booting in UEFI. To boot in UEFI your HDD must have GUID Partition Table [GPT], its a must. GPT is a major upgrade over 'msdos' which is now more than 30 years old. The future is GPT and gradually 'msdos' will become a dodo.

If you look at the output of 'parted -l' you will see that all your partitions have 'msdos' table, with this you can conclude that you are booting in 'legacy BIOS' and Not in UEfI.

---

### Post by ronb19495 on 2013-10-23
so how do i fix this

---

### Post by fantab on 2013-10-23
What do you want to fix? Do you want to boot in UEFI?

---

### Post by oldfred on 2013-10-23
There is no need to change. And not a big advantage unless starting new.

And to easily dual boot you would literately have to erase every drive, convert to gpt and reinstall every system in UEFI mode.
You cannot easily dual boot if one system is UEFI and another is BIOS as you have to go into UEFI menu and boot from that possibly turning on or off UEFI or CSM/BIOS/Legacy boot mode. 
UEFI and BIOS are not really compatible so once you start booting one way you cannot use grub to boot a system that is the other way.

I only have BIOS, but all my new drives are now partitioned with gpt with an efi partition currently unused at the beginning of the drive. UEFI says efi partition should be first, but Windows makes it second or even third, but it still it near beginning of large drives.
But I have to have a bios_grub partition to boot in BIOS mode from gpt partitioned drives. But then I could put drive in a new system and install grub-efi if I wanted to convert in future.

I do recommend gpt partitioning on all newly partitioned drives unless you have or want Windows in BIOS boot mode on the same drive. Windows only boots from gpt partitioned drives with UEFI. Ubuntu and grub2 boot in UEFI or BIOS mode from gpt partitioned drives.

---

### Post by ronb19495 on 2013-10-23
ok thanks one and all for your replies I will leave as is as its all working well as it is wont worry about uefi untill I have a cleanout thanks for the help
regards Ron

---

### Post by ronb19495 on 2013-10-23
ok it got the better of me I tried gptfdisk on linux mint amazing for me it worked heres the output```
@ron-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00095c07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1026047      512000   83  Linux
/dev/sda2         1026048   488396799   243685376   8e  Linux LVM

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0008694a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     1026047      512000   83  Linux
/dev/sdb2         1026048  1953523711   976248832   8e  Linux LVM

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005ed3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   421976063   210987008   83  Linux
/dev/sdc2       421978110   488396799    33209345    5  Extended
/dev/sdc5       421978112   488396799    33209344   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  1953525167   976762583+  ee  GPT

Disk /dev/mapper/fedora-swap: 16.7 GB, 16718495744 bytes
255 heads, 63 sectors/track, 2032 cylinders, total 32653312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora-swap doesn't contain a valid partition table

Disk /dev/mapper/fedora-home: 929.3 GB, 929269022720 bytes
255 heads, 63 sectors/track, 112977 cylinders, total 1814978560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora-home doesn't contain a valid partition table

Disk /dev/mapper/fedora-root: 53.7 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders, total 104857600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora-root doesn't contain a valid partition table

Disk /dev/mapper/fedora00-swap: 16.7 GB, 16718495744 bytes
255 heads, 63 sectors/track, 2032 cylinders, total 32653312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora00-swap doesn't contain a valid partition table

Disk /dev/mapper/fedora00-home: 179.1 GB, 179126140928 bytes
255 heads, 63 sectors/track, 21777 cylinders, total 349855744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora00-home doesn't contain a valid partition table

Disk /dev/mapper/fedora00-root: 53.7 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders, total 104857600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora00-root doesn't contain a valid partition table
ron@ron-desktop:~$ 

```

---

### Post by ronb19495 on 2013-10-24
I have tried uefi install on gpt disk ubuntu 13.10 doesnt like the idea of uefi on my computer for some odd reason either I am not partitioning drives the wright way or something else is wrong can someone point me some good and easy patitioning software for an old man thats brain has become cloudy

---

### Post by fantab on 2013-10-25
So you want to go UEFI way? Alright.

**BACK UP ALL the IMPORTANT DATA**. You WILL lose all the data on those HDDs if you are going to change the partition table to GPT and boot with UEFI.

Does your Mobo support UEFI?
Is UEFI booting ENABLED in UEFI/BIOS?
Does your processor support 64bit?
Have you canged the SATA mode in UEFI/BIOS to 'ACHI/AHCI'?

To Boot in UEFI:
1. Your HDD must have a GUID Partition Table [GPT]. In your case, ALL your OS MUST boot in UEFI, which in turn means that you will have to convert all your HDDs to GPT.
2. With GPT you MUST have your First Parttion as: Size=300MB, Formatted with=FAT32, Flag=Boot. (Do this on all your HDDs, ie, every HDD will have a 300MB first partition).
3. In GPT all partitions are Primary, so you don't need any Extended Partition.
4. You must **use EXT4** as filesystem with UEFI. **LVM** will NOT work. (I am not 100% sure, someone more knowledgeable can confirm this or search for yourself on these forums or www about LVM's compatibility with UEFI).
5. **Only 64bit OS** will boot with UEFI. 32bit OS will NOT install in UEFI.

During Booting Ubuntu/Linux DVD/USB to install you MUST **boot in EFI mode**, (How you boot is how you install). If you boot in EFI mode you will have black screen with menu options, if NOT then you will see regular Ubuntu colors.
Install Grub from an install, say Ubuntu, to its own HDD, ie the HDD on which Ubuntu is installed. Do the same for all OS.

Gparted can do all this, its an excellent disk management tool in Linux. 

***Reminder***: **BACK UP ALL YOUR IMPORTANT DATA**. (All Data WILL be erased when you change the partition table).

Good Luck...

---

### Post by ronb19495 on 2013-10-25
here you go fantab thanks for your help and to oldfred to heres the output [CODEodel: ATA ST3250312AS (scsi)Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size   File system  Name  Flags
 1      1049kB  316MB  315MB  fat32              boot
 2      316MB   250GB  250GB  ext4




Model: ATA WDC WD10EZRX-00A (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  211MB   210MB  fat16        EFI System Partition  boot
 2      211MB   735MB   524MB  ext4
 3      735MB   1000GB  999GB                                     lvm




Model: ATA ST3250318AS (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  316MB   315MB   fat32                 boot
 2      316MB   21.8GB  21.5GB  ext4         primary
 3      21.8GB  250GB   228GB   ext4         primary




Model: ATA WDC WD10EARS-003 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  316MB   315MB   fat32                 boot
 2      316MB   966GB   966GB   ext4
 3      966GB   1000GB  34.0GB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora-home: 929GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system  Flags
 1      0.00B  929GB  929GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora-swap: 16.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  16.7GB  16.7GB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora-root: 53.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags


][/CODE]
it took me a few tries but I got it done
regards Ron

---

### Post by fantab on 2013-10-25
Your /dev/sdb still shows a LVM partition which is probably Fedora /home, but for this it looks good.

EDIT: also 34GB SWAP is bit too much. If you don't 'Hiberante' your machine about 4-8GB of SWAP should be plenty. If you use 'Hiberantion' then the SWAP size should be equal to or greater than the amount of RAM installed.

---

### Post by ronb19495 on 2013-10-25
fantab you are right lvm doesnt work its screwing up my boot menu I have 2 mac osx os on the menu instead of fedora never mind trial and error will reinstall fedora on ext 4 and see if that fixes it ubuntu 13.10 gave me problems also it wouldnt boot but boot-repair fixed that problem ok will keep testing and report back
regards Ron

---

### Post by oldfred on 2013-10-26
If multi-booting it probably is better to have Fedora just in an ext4 partition. Its default is LVM and Ubuntu's desktop does not include the lvm drivers unless you install Ubuntu with lvm. You can install the lvm2 driver and mount your Fedora and then grub2's os-prober will add Fedora to your grub menu.

---

### Post by fantab on 2013-10-26
@oldfred: Does EFI boot work with LVM? Does LVM work with GPT?

---

### Post by oldfred on 2013-10-26
I know LVM works with gpt as Rod Smith the creator of gdisk uses gpt and LVM.
And since he also uses UEFI as he has rEFInd which is multi-boot UEFI.

But I have not seen a UEFI install with LVM where a user has posted BootInfo script to see details. I would expect the efi partition has to be outside the LVM as the UEFI FAT32 driver is probably not aware of anything other than standard partition tables. 

 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

Shows bios_grub, efi & LVM on one drive.

 srs5694's to show 8 sector alignment post post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by fantab on 2013-10-26
Thanks oldfred, I had to confirm this because I rememberd reading somewhere that LVM was not compatible with UEFI... but could remember where,  and wasn't really sure about LVM. I never used LVM.

---

