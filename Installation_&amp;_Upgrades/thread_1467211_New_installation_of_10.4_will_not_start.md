---
title: "New installation of 10.4 will not start"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2010-04-30
I have installed 10.4 on a PC running Vista 64-bit with AMD64.  It has 3 x internal hard drives, 1 x1Tb for back uo. 1 x 768Gb partitioned for files. 1 x 300G in two partitions of 150G each for each of the two OS: Vista and Ubuntu.

I used the wubi ti install

The install itself seemed to go well.  However, on reboot, which then does the final install and set up, it refuses to boot.  Generally I get a black screen, but I can get it to sometimes give me info by pressing ENTER after some time in black screen state.  The message it gives is to the effect "Windows was not shut down properly.  Log off, shut it down and try again", and "the drive is in Hybernation so enter the following in command line ' mount -t ntfs-3g -o remove_hiberfile /dev/sda1/ isodevice'"

Mainly there is nowhere to enter this, but I found a way of starting up the boot that does a line by line and when that stops I have tried entering the above command.  I get a message "not found".

Can anyone help me.

---

### Post by edalry1 on 2010-04-30
I have the same problem with two different computers. Both have been running version 9.10 64 bit with out issue. After failed upgrades I down loaded ISO files and tried clean install dual boot using wubi both with windows 7 64. The systems install flows fine in windows, after reboot ubuntu option appears and the continued install of 10.4 is completed. After what seems to be a clean install on last reboot is required ubuntu will not start black screen is all I receive. Never gets to the login screen.

Any help would be awesome.

---

### Post by Jonners59 on 2010-05-03
One step forward and one back...
Fixed the install issue, by disconnecting the spare hard drives and completely re installing Vista and another copy of U 9.10...  That eventually got it going.  I found the 10.4 already installed.  Doesn't sound much but I have installed and installed Ubuntu and Vista so many times over the past 4 days.

Now the next big issue that I found yesterday and has repapered after yet another reinstall.  When I think all is fixed and working, **I complete the setting up of 10.4 which includes an update**.  Then it all goes wrong again:

After a reboot, I find all the installs are listed in Grub - great - and I can select them all, however, Vista will not load, it just reverts back to the Grub.
:mad:
Also, would like to be able to change the boot order....

I also find that 10.4 does not always load up and I have to cold restart, often booting in a level before the most recent to get it to start, but I am not worried about this as I can make it work through the re boot - an issue I think is related to video config.

Any solutions, please?????

---

### Post by cariboo on 2010-05-03
I can't help with the Vista problem as I don't dual boot. but several people have had the same problem, I've seen the solution ins the first 4 or pages of the experience thread. As far as modifying the grub2 menu, have a look at [this]("https://help.ubuntu.com/community/Grub2") document, scroll down to customization.

---

### Post by Jonners59 on 2010-05-04
> **cariboo907 said:**
> I can't help with the Vista problem as I don't dual boot. but several people have had the same problem, I've seen the solution ins the first 4 or pages of the experience thread. As far as modifying the grub2 menu, have a look at [this]("https://help.ubuntu.com/community/Grub2") document, scroll down to customization.



Thanks for this...  GRUB2 config found and very interesting.  Have looked on my machine and I can see that if I get the boot matter working this will work...

Will now look for the "solutions" to booting.  Would be nice if it was in a separate thread so was easy to find.

If this works I may write up experiences and solutions for others to find.


System info:

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057726

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           1        8001    7  HPFS/NTFS
/dev/sdb2               2      121601   976752000    5  Extended
/dev/sdb5               2        6868    55151616    7  HPFS/NTFS
/dev/sdb6            6868      121601   921598976    7  HPFS/NTFS

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8408a51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12871   103386276    7  HPFS/NTFS
/dev/sda2           12872       91201   629185725    f  W95 Ext'd (LBA)
/dev/sda5           12872       25926   104864256    7  HPFS/NTFS
/dev/sda6           25927       38981   104864256    7  HPFS/NTFS
/dev/sda7           38982       52036   104864256    7  HPFS/NTFS
/dev/sda8           52037       65091   104864256    7  HPFS/NTFS
/dev/sda9           65092       78146   104864256    7  HPFS/NTFS
/dev/sda10          78147       91201   104864256    7  HPFS/NTFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe218bae6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19873   159628848+   7  HPFS/NTFS
/dev/sdc2   *       19874       21627    14089005   82  Linux swap / Solaris
/dev/sdc3           21628       26756    41198692+   5  Extended
/dev/sdc4   *       26757       38913    97651102+  83  Linux
/dev/sdc5   *       25541       26756     9767488+  83  Linux
/dev/sdc6           21628       25373    30089682   83  Linux
/dev/sdc7           25374       25540     1341396   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Jonners59 on 2010-05-13
[SIZE=5][B][COLOR=Red]Any Help, Please.  This has been hanging around for a couple of days

[/COLOR][/B][/SIZE]> **Jonners59 said:**
> Thanks for this...  GRUB2 config found and very interesting.  Have looked on my machine and I can see that if I get the boot matter working this will work...

Will now look for the "solutions" to booting.  Would be nice if it was in a separate thread so was easy to find.

If this works I may write up experiences and solutions for others to find.


System info:

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057726

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           1        8001    7  HPFS/NTFS
/dev/sdb2               2      121601   976752000    5  Extended
/dev/sdb5               2        6868    55151616    7  HPFS/NTFS
/dev/sdb6            6868      121601   921598976    7  HPFS/NTFS

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8408a51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12871   103386276    7  HPFS/NTFS
/dev/sda2           12872       91201   629185725    f  W95 Ext'd (LBA)
/dev/sda5           12872       25926   104864256    7  HPFS/NTFS
/dev/sda6           25927       38981   104864256    7  HPFS/NTFS
/dev/sda7           38982       52036   104864256    7  HPFS/NTFS
/dev/sda8           52037       65091   104864256    7  HPFS/NTFS
/dev/sda9           65092       78146   104864256    7  HPFS/NTFS
/dev/sda10          78147       91201   104864256    7  HPFS/NTFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe218bae6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19873   159628848+   7  HPFS/NTFS
/dev/sdc2   *       19874       21627    14089005   82  Linux swap / Solaris
/dev/sdc3           21628       26756    41198692+   5  Extended
/dev/sdc4   *       26757       38913    97651102+  83  Linux
/dev/sdc5   *       25541       26756     9767488+  83  Linux
/dev/sdc6           21628       25373    30089682   83  Linux
/dev/sdc7           25374       25540     1341396   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by oldfred on 2010-05-13
With multiple drives it would be good to see the entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by Jonners59 on 2010-05-14
> **oldfred said:**
> With multiple drives it would be good to see the entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

Is this what you are after.....?

Install of OS is on sdc.  sda and sdb are storgae and backup ONLY.  Odd date!

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary:  ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Lilo is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same  drive in 
    partition #6 for /boot/grub.

sda1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: __________________________________________________   _______________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5  starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6  starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7  starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8  starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9  starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda10  starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: __________________________________________________   _______________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5  starts 
                       at sector 319. But according to the info from  fdisk, 
                       sdb5 starts at sector 16384.
    Operating System:  
    Boot files/dirs:   

sdb6: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb6  starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdc1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /etc/lilo.conf /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr  /wubildr

sdc2: __________________________________________________   _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: __________________________________________________   _______________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________   _______________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sdc6: __________________________________________________   _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sdc4: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr  /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdc4/Wubi: __________________________________________________   _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  __________________________________________________  ___

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8408a51

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   206,772,614   206,772,552   7 HPFS/NTFS
/dev/sda2         206,772,615 1,465,144,064 1,258,371,450   f W95 Ext d  (LBA)
/dev/sda5         206,772,678   416,501,189   209,728,512   7 HPFS/NTFS
/dev/sda6         416,501,253   626,229,764   209,728,512   7 HPFS/NTFS
/dev/sda7         626,229,828   835,958,339   209,728,512   7 HPFS/NTFS
/dev/sda8         835,958,403 1,045,686,914   209,728,512   7 HPFS/NTFS
/dev/sda9       1,045,686,978 1,255,415,489   209,728,512   7 HPFS/NTFS
/dev/sda10      1,255,415,553 1,465,144,064   209,728,512   7 HPFS/NTFS


Drive: sdb ___________________  __________________________________________________  ___

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00057726

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63        16,064        16,002   7 HPFS/NTFS
/dev/sdb2              16,065 1,953,520,064 1,953,504,000   5 Extended
/dev/sdb5              16,384   110,319,615   110,303,232   7 HPFS/NTFS
/dev/sdb6         110,321,664 1,953,519,615 1,843,197,952   7 HPFS/NTFS


Drive: sdc ___________________  __________________________________________________  ___

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe218bae6

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   319,259,744   319,257,697   7 HPFS/NTFS
/dev/sdc2         319,259,745   347,437,754    28,178,010  82 Linux swap  / Solaris
/dev/sdc3         347,437,755   429,835,139    82,397,385   5 Extended
/dev/sdc5         347,437,881   407,617,244    60,179,364  83 Linux
/dev/sdc6         407,617,308   429,835,139    22,217,832  83 Linux
/dev/sdc4         429,835,140   625,137,344   195,302,205   7 HPFS/NTFS


blkid -c /dev/null: __________________________________________________   __________

Device           UUID                                   TYPE       LABEL                          

/dev/loop0       6a314770-5264-4c4f-9496-c497a01ae2e7   ext4                                      
/dev/sda10       B22A9A262A99E81D                       ntfs        CHIARA                        
/dev/sda1        9ABAAE68BAAE411D                       ntfs        BARONI                        
/dev/sda5        64BE1AC0BE1A8AA6                       ntfs        RESOURCES                     
/dev/sda6        0E84A48684A4723F                       ntfs       The  Boys                      
/dev/sda7        BE94ADB294AD6E19                       ntfs        Jonathan                      
/dev/sda8        5830B68E30B6731C                       ntfs        Shared Files                  
/dev/sda9        4E30A23730A225C5                       ntfs        Teaching                      
/dev/sdb1        6313A67F4CCC018F                       ntfs        Bootable space                
/dev/sdb5        429E50419E503021                       ntfs        Backup Configs                
/dev/sdb6        50720F13720EFD8A                       ntfs        Master Backup                 
/dev/sdc1        EC72C80A72C7D78A                       ntfs       Vista  OS                      
/dev/sdc2        8673cd24-c365-443f-9d42-9a60d3ce5559   swap                                      
/dev/sdc4        42F2EF69F2EF5FA1                       ntfs       Linux                          
/dev/sdc5        81dcdc23-0117-42d6-9cff-1ec6c660d3a3   ext3       9.10                           
/dev/sdc6        394d5cf0-5030-4019-aa17-92a043614299   ext4       9.10  temp                     

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

/dev/sdc5        /                        ext3        (rw,errors=remount-ro)


============================= sdc1/etc/lilo.conf:  =============================

paragon_jboot
image=/etc/psrdisk
label="###NdenHden"
initrd=/etc/psr.img
append="paragon_lang=en"
```

---

### Post by darkod on 2010-05-14
I know you are probably pi**ed off by now, but lets go backwards a bit.

You have a hell of a mess. In short, looks like two separate 9.10 installations, and on top of that wubi install inside vista. And on top of that, lilo boot files inside your vista partition, /dev/sdc1.

So lets stop for a moment and figure out what do you want to achieve.
Wubi is used only to try ubuntu and not as long term install. But you can do the similar by running the live mode.
Wubi can give you loads of issues if you try to keep it and use it as long term install. Not to mention that it's inside windows so if you get windows corrupted, wubi is gone too.

If you want to take the full dual boot approach (vista and 10.04 on separate partitions, independent), here is the suggestion:

- lets repair the vista boot process, so you can boot it and remove wubi (it would be in Programs, like a software app)
- if you have no data to extract from both of your 9.10 installations, lets delete their partitions, that will create unallocated space on the hdd
- use that space to install 10.04 into it

Problem solved, hopefully. :)

---

### Post by Jonners59 on 2010-05-14
> **darkod said:**
> I know you are probably pi**ed off by now, but lets go backwards a bit.

You have a hell of a mess. In short, looks like two separate 9.10 installations, and on top of that wubi install inside vista. And on top of that, lilo boot files inside your vista partition, /dev/sdc1.

So lets stop for a moment and figure out what do you want to achieve.
Wubi is used only to try ubuntu and not as long term install. But you can do the similar by running the live mode.
Wubi can give you loads of issues if you try to keep it and use it as long term install. Not to mention that it's inside windows so if you get windows corrupted, wubi is gone too.

If you want to take the full dual boot approach (vista and 10.04 on separate partitions, independent), here is the suggestion:

- lets repair the vista boot process, so you can boot it and remove wubi (it would be in Programs, like a software app)
- if you have no data to extract from both of your 9.10 installations, lets delete their partitions, that will create unallocated space on the hdd
- use that space to install 10.04 into it

Problem solved, hopefully. :)

Thank you Darkod
I want to keep one of the 9.10s as it has allowed me to get in to the 10.4 when all else has failed, so one will be backup....

That said I will - on Sunday PM as it is #2 son's 7th birthday today and mayhem is due this weekend!! - remove Wabi from "Programs" in Vista as suggested.  I did remove it from the C drive before, but if you believe there is still residue there then it may well explain the bogus "UBUNTU" in one of the GRUB menus...  So I'll search for that and remove.

I will delete the spare 9.10.  It was there only temp as it allowed me access after yet another failure.

I will try another 10.4 install after all that.

My concern is that I have been round all this MANY times, and it always fails, even when i get a good install after the update.  But I have been at this for Over 2 weeks now so dong it again won't make that much difference.:popcorn:

Please don't disappear.

---

### Post by darkod on 2010-05-14
sdc4: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    [COLOR=Red]Boot files/dirs:   /ubuntu/winboot/wubildr.mbr  /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk[/COLOR]

Wubi seems to be reported on /dev/sdc4. root.disk and swap.disk are the image files containing the data, in a virtual way they should represent the root and swap partitions. It doesn't look like only traces, but a wubi install.

Also, if you need quick access to failed ubuntu or windows system, you can use live mode anytime, either with the ubuntu cd or usb stick. No need to install on the hdd just so you can access the disk.

In fact, sometimes people have extracted data from a crashed windows installation without ever having ubuntu on the hdd. It works from the live cd directly. One of the big benefits.

Anyway, make a plan what you want to do, and once you get the free time we are all here. :)

---

### Post by Jonners59 on 2010-05-16
> **darkod said:**
> 
Anyway, make a plan what you want to do, and once you get the free time we are all here. :)

Thanks Darkod

---

### Post by Jonners59 on 2010-05-18
> **darkod said:**
> sdc4: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    [COLOR=Red]Boot files/dirs:   /ubuntu/winboot/wubildr.mbr  /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk[/COLOR]

Wubi seems to be reported on /dev/sdc4. root.disk and swap.disk are the image files containing the data, in a virtual way they should represent the root and swap partitions. It doesn't look like only traces, but a wubi install.

Also, if you need quick access to failed ubuntu or windows system, you can use live mode anytime, either with the ubuntu cd or usb stick. No need to install on the hdd just so you can access the disk.

In fact, sometimes people have extracted data from a crashed windows installation without ever having ubuntu on the hdd. It works from the live cd directly. One of the big benefits.

Anyway, make a plan what you want to do, and once you get the free time we are all here. :)

Well, had a bad evening last night until 12:30 again.

I used "Programs and Features" in Vista to remove Ubuntu.  I then did a search for any reference to Wubi or Ubuntu in Vista, deleting ANYTHING I found.  I scrubbed (deleted and reformatted) all bar the Vista partitions.  I then removed the Hard Drives with my docs and backup (of docs, not systems) on. I then reinstalled Ubuntu 9.10, creating a c15Gb SWAP, 5GB Boot (ext4) and c100+Gb 9.10 (ext4)....

I then upgraded via the update Manager to 10.4... I then reinstated the 2 hard drives. So what happened?

1.  I have horrible with boot menus.  I do not know if they are GRUB or something else.

Menu 1 shows a colourful menu, listed, top to bottom: VISTA, UBUNTU and GRUB (see picture: Menu 1).
[INDENT]1a.  If I select Vista in Menu 1 I get Menu 2 (see picture: Menu 2), which lists, from top to bottom: Vista and UBUNTU.[INDENT]1aa.  If I select Vista it loads

1ab.  but If I select UBUNTU it fails (see Picture: UBUNTU in Menur 2), which I assume is failing because I have removed the Wubi and it can not find it.  This occurred before I did all the work this time.
[/INDENT]1b.  If I select UBUNTU in Menu 1, I get an attempt to load Ubuntu that fails (See Picture: UBUNTU in Menu 1), which I get out of by doing Ctrl+Alt+Delete

1c. If I select GRUB, I get a normal GRUB menu (See Picture:  GRUB in Menu 1 = GRUB, last in the row of pictures)
[/INDENT]***[COLOR=Red]I somehow need to remove Menu 1 completely, remove Ubuntu from Menu 2, though this later is not quite so important as it can be avoided.  Can anyone help, please????[/COLOR]***

2.  If I select 10.4, from the GRUB menu as described in 1c above, it boots.

I can hear the drum roll and music, but I get the black screen.  If I the do Ctrl+Alt+ delete twice it shuts down and I get the new Ubuntu 10.4 logo just before it closes.

If I then try to load via Recovery, I open the menu and do fix broken, etc, and then try and open in "Default Resolution (this time only)" and it opens. There is even a "Print Screen" image on the desktop that I tried when I tried loading normally. So I believe the issue here is the Screen resolution.  It can not recognise my monitor, an old IBM 19" CRT monitor, 6332-92N, so I presume I need to change the config somehow.  ***[COLOR=Red]Can anyone help, please???[/COLOR]***

:popcorn:

---

### Post by darkod on 2010-05-18
Because there were fundamental changes to your system, please run the script again and post the current results.txt content. We'll see what can be done.

It doesn't look too complicated, getting rid of bootloaders (or the boot menus) is very simple. But it's better to see the results first before issuing commands.

PS. Also, when running the script leave all internal hdds connected. Lets see how it looks with all of them connected. I get the feeling there is some bootloader on your docs hdd and it remained there and is now being used as primary.

---

### Post by Jonners59 on 2010-05-18
> **darkod said:**
> Because there were fundamental changes to your system, please run the script again and post the current results.txt content. We'll see what can be done.

It doesn't look too complicated, getting rid of bootloaders (or the boot menus) is very simple. But it's better to see the results first before issuing commands.

PS. Also, when running the script leave all internal hdds connected. Lets see how it looks with all of them connected. I get the feeling there is some bootloader on your docs hdd and it remained there and is now being used as primary.

I had no intention of disconnecting them.  No fear of that.

Sorry for taking so long to get back.  I had to reboot from Vista to 10.4, and then I found I could not access any of the HD from the PC I am working from now, so had to reload Vista.  That is something else that will need to be set up.  The ability for PCs and Laptops to access the HDs, and visa versa...  Another day.

OK, test run. The PARAGON is interesting as it appears in one of the faulty options.  I also read somewhere that it is a partition/backup sw...  I had the colourful menu after running Partition Commander and running a boot backup.  I deleted and removed it.  I wonder if this is a remnant?????

[HTML]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Paragon is installed in the MBR of /dev/sda
 => Lilo is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /etc/lilo.conf /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 347714187 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 319. But according to the info from fdisk, 
                       sdc5 starts at sector 16384.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   319,259,744   319,257,697   7 HPFS/NTFS
/dev/sda2         319,260,672   347,435,007    28,174,336  82 Linux swap / Solaris
/dev/sda3    *    347,437,755   363,422,429    15,984,675  83 Linux
/dev/sda4         363,422,430   625,137,344   261,714,915  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   206,772,614   206,772,552   7 HPFS/NTFS
/dev/sdb2         206,772,615 1,465,144,064 1,258,371,450   f W95 Ext d (LBA)
/dev/sdb5         206,772,678   416,501,189   209,728,512   7 HPFS/NTFS
/dev/sdb6         416,501,253   626,229,764   209,728,512   7 HPFS/NTFS
/dev/sdb7         626,229,828   835,958,339   209,728,512   7 HPFS/NTFS
/dev/sdb8         835,958,403 1,045,686,914   209,728,512   7 HPFS/NTFS
/dev/sdb9       1,045,686,978 1,255,415,489   209,728,512   7 HPFS/NTFS
/dev/sdb10      1,255,415,553 1,465,144,064   209,728,512   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065 1,953,520,064 1,953,504,000   5 Extended
/dev/sdc5              16,384   110,319,615   110,303,232   7 HPFS/NTFS
/dev/sdc6         110,321,664 1,953,519,615 1,843,197,952   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        EC72C80A72C7D78A                       ntfs       Vista OS                      
/dev/sda2        5414e1bc-87c6-4c99-83cb-a7d944c625d1   swap                                     
/dev/sda3        cdb1d54a-27ee-4e99-84a4-4b4521412145   ext4                                     
/dev/sda4        febd65f3-6a6d-4b12-8f7d-abff516d083d   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb10       B22A9A262A99E81D                       ntfs       CHIARA                        
/dev/sdb1        9ABAAE68BAAE411D                       ntfs       BARONI                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        64BE1AC0BE1A8AA6                       ntfs       RESOURCES                     
/dev/sdb6        0E84A48684A4723F                       ntfs       The Boys                      
/dev/sdb7        BE94ADB294AD6E19                       ntfs       Jonathan                      
/dev/sdb8        5830B68E30B6731C                       ntfs       Shared Files                  
/dev/sdb9        4E30A23730A225C5                       ntfs       Teaching                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc5        429E50419E503021                       ntfs       Backup Configs                
/dev/sdc6        50720F13720EFD8A                       ntfs       Master Backup                 
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /boot                    ext4       (rw)
/dev/sdb5        /media/RESOURCES         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================= sda1/etc/lilo.conf: =============================

paragon_jboot
image=/etc/psrdisk
label="###NdenHden"
initrd=/etc/psr.img
append="paragon_lang=en"

################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
                
============================= sda3/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set febd65f3-6a6d-4b12-8f7d-abff516d083d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set cdb1d54a-27ee-4e99-84a4-4b4521412145
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cdb1d54a-27ee-4e99-84a4-4b4521412145
    linux    /vmlinuz-2.6.32-22-generic-pae root=UUID=febd65f3-6a6d-4b12-8f7d-abff516d083d ro   quiet splash
    initrd    /initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cdb1d54a-27ee-4e99-84a4-4b4521412145
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /vmlinuz-2.6.32-22-generic-pae root=UUID=febd65f3-6a6d-4b12-8f7d-abff516d083d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cdb1d54a-27ee-4e99-84a4-4b4521412145
    linux    /vmlinuz-2.6.31-21-generic-pae root=UUID=febd65f3-6a6d-4b12-8f7d-abff516d083d ro   quiet splash
    initrd    /initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cdb1d54a-27ee-4e99-84a4-4b4521412145
    echo    'Loading Linux 2.6.31-21-generic-pae ...'
    linux    /vmlinuz-2.6.31-21-generic-pae root=UUID=febd65f3-6a6d-4b12-8f7d-abff516d083d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.31-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cdb1d54a-27ee-4e99-84a4-4b4521412145
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cdb1d54a-27ee-4e99-84a4-4b4521412145
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ec72c80a72c7d78a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda3: Location of files loaded by Grub: ===================


 178.0GB: grub/core.img
 178.0GB: grub/grub.cfg
 178.0GB: initrd.img-2.6.31-21-generic-pae
 178.0GB: initrd.img-2.6.32-22-generic-pae
 178.0GB: vmlinuz-2.6.31-21-generic-pae
 178.0GB: vmlinuz-2.6.32-22-generic-pae

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=febd65f3-6a6d-4b12-8f7d-abff516d083d /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=cdb1d54a-27ee-4e99-84a4-4b4521412145 /boot           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=5414e1bc-87c6-4c99-83cb-a7d944c625d1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 186.2GB: initrd.img
 186.2GB: initrd.img.old
 186.2GB: vmlinuz
 186.2GB: vmlinuz.old
[/HTML]

---

### Post by darkod on 2010-05-18
OK, few things to do:

Number 1:
Set the 320GB disk (/dev/sda) as first hdd boot option in BIOS, if it already isn't.

Number 2:
Boot in ubuntu live mode.

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   319,259,744   319,257,697   7 HPFS/NTFS
/dev/sda2         319,260,672   347,435,007    28,174,336  82 Linux swap / Solaris
/dev/sda3    *    347,437,755   363,422,429    15,984,675  83 Linux
/dev/sda4         363,422,430   625,137,344   261,714,915  83 Linux
```The boot flag is on /dev/sda3. You windows system partition is /dev/sda1. Windows can't boot without the boot flag while linux doesn't need it.

Open Gparted (System-Administration), right-click /dev/sda3 and set the boot flag OFF, then right-click /dev/sda1 and set the bot flag ON. The flags might be in submenu after the right-click, look around.

Number 3:
While still in live mode, reinstall grub2 on the MBR of /dev/sda instead of paragon. You have separate boot partition as /dev/sda3 so you have to mount it too. In terminal execute:

sudo mount /dev/sda4 /mnt
sudo mount /dev/sda3 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda

Restart and you should see the proper grub2 which should be able to boot both ubuntu and windows. If windows still doesn't work, boot ubuntu and from /dev/sda1 remove /etc/lilo.conf, it's not needed there. I think it would work even if it remains there, removing it later is probably a good choice.

---

### Post by Jonners59 on 2010-05-18
OK, I am in there now, via recovery mode - only access I have.  I checked the boot order and that was correct...  I am very uncertain about this so don't go away, please!!!!

I assume I just take note of all the info and go straight to gParted bit.  Did not have this so am downloading as I write

It's very slow.  I set it up in Synaptic to download, wrote to you, and then decided to install on another machine.  That other machine completed the entire task before this started the install, which it is still doing???

OK done the changes - I like gParted!!!!

Now about to reboot

---

### Post by darkod on 2010-05-18
I thought you will use it from the cd, in live mode (Try Ubuntu mode). It should be included in the cd.

Yes, on the hdd installation it's not included by default.

PS. If you don't have an ubuntu cd wait a minute, because you will need it for task 3.

---

### Post by Jonners59 on 2010-05-18
> **darkod said:**
> I thought you will use it from the cd, in live mode (Try Ubuntu mode). It should be included in the cd.

Yes, on the hdd installation it's not included by default.

PS. If you don't have an ubuntu cd wait a minute, because you will need it for task 3.

All done.....  Your a star!!!  :guitar:  Well almost.  Did not need the Live CD (just seen your message as I have just booted in).

I now do not have menu 1, the colourful one.
I boot into the GRUB menu - very nice.

When I select Vista, I get another menu, with the UBUNTU listed that I do not want.  Would be nice to remove, but it works without...  I can load Vista perfectly.

Then re booting again, I can load 10.4 in recovery mode.

So, can I now:

Remove the additional UBUNTU in Menu 2?
How do I get the normal 10.4 to work.  I am sure it is the resolution...?

---

### Post by darkod on 2010-05-18
Good to hear it's working.

But I get slightly confused.

1. What normal ubuntu are you talking about? When the first grub2 loads up, if you select ubuntu in there, that's your hdd ubuntu installation.

2. It seems your vista bootloader has entries for vista and some ubuntu (not sure from where from). If you want to remove this entry, you need to use windows commands. I haven't really used them too much, I rarely need them. If you read around for instructions on bcdedit, that is what you would need to use. Something like:

bcdedit /remove ubuntu

You need to run this from vista, in command prompt with Admin rights (in Accessories right-click command prompt and select Run as Administrator). But the above command is example, you need to find the exact syntax needed.

---

### Post by Jonners59 on 2010-05-18
Cheers for that, I will...

Do you know how to fix the matter of not being able to access 10.4?  I have to use Recovery mode and default resolution to get access, like now.  If I use the normal boot, it seems to load, but I have a blank screen.  I can hear the boot up drums and music, and if I shut down I often get the Ubuntu logo appear briefly.

---

### Post by darkod on 2010-05-18
> **Jonners59 said:**
> Cheers for that, I will...

Do you know how to fix the matter of not being able to access 10.4?  I have to use Recovery mode and default resolution to get access, like now.  If I use the normal boot, it seems to load, but I have a blank screen.  I can hear the boot up drums and music, and if I shut down I often get the Ubuntu logo appear briefly.

OK, I understand now. Give me some time, still haven't had my dinner. :)

---

### Post by oldfred on 2010-05-18
Darko, you must be eating late, I am currently in Fla. and now going out for dinner here.

Just to get you started. Without knowing what video card here are several choices. The nomodeset seems common to many versions.

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

to see what video you have:
lspci | grep VGA

---

### Post by Jonners59 on 2010-05-18
Hello Oldfred
Always popping in to the rescue.

I have had enough for this evening, so will take a look at this tomorrow.  I'll keep you posted.

PS.  I have a string of other threads that have not been answered.  You may be able to assist with.  All referring to my other PC.

---

### Post by oldfred on 2010-05-18
After updating in place for 3 years and having issues or fun figuring out what to fix, I bought a new drive with lots of room and installed Karmic clean. I reorganized as I had just root & swap with a small shared FAT partition for windows stuff.

The clean install of Karmic so so good, I decided to always do clean installs but have programs & settings that I want to keep besides that in /home. So I tried to do everything I could with the terminal and listed history. I then converted that list to a simple bash file (as it grew it may not be as simple but I still am learning bash). I then found my portable that I use for travel with XP was for the nth time not connecting with Samba so I just installed Karmic and ran my scripts. And converted to NFS which has worked well.

I would suggest if you are working with more than one system planning ahead, do clean installs and script as much as possible.

---

### Post by Jonners59 on 2010-05-20
> **oldfred said:**
> Darko, you must be eating late, I am currently in Fla. and now going out for dinner here.

Just to get you started. Without knowing what video card here are several choices. The nomodeset seems common to many versions.

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

SORTED!!!!!!  Thank you

---

### Post by Jonners59 on 2010-07-30
> **oldfred said:**
> 
Just to get you started. Without knowing what video card here are several choices. The nomodeset seems common to many versions.

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
spci | grep VGA

Hi Oldfred
Sorry, it's me again.  I had to rebuild the machine again.  I had lost network and no one seemed to know how to restore it, so I took the plunge.  Anyway the long and short of it, I have the same inability to boot into the normal kernal, I have to load in to recovery mode and the low graphics.

i tried to select "e" on Grub2 Menu as before, but I get the wrong options.  It just has 4 lines of script, and not the one I was expecting to replace "quiet and splash" with "nomodeset.  Where am I going wrong??????

---

