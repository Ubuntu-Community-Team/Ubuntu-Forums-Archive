---
title: "Booting problem after updgrading"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by Wissem R on 2010-11-27
I have a ubuntu 9.10 karmic koala,I just did an upgrade but after the upgrade was done I restarted and the system wouldn't boot up !
I get this message when booting in recovery mode :
**fsck from util-linux-ng 2.16**
From googling the problem,I found a lot of users reporting this as a bug (tried a lot of solutions but nothing so far).

My ubuntu's partition: /dev/sda6

---

### Post by Rubi1200 on 2010-11-27
Hi and welcome to the forums :)

Use a LiveCD to boot the computer and choose to try Ubuntu.

Click on the boot info script link at the bottom of my post (instructions included).

Copy/paste the results back here to the forums.

It will show us what is where and make troubleshooting and offering solutions easier.

Thanks.

---

### Post by Wissem R on 2010-11-27
Thanks for the quick reply :D

Here is the output of RESULTS.txt

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1f7b1f7a

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   205,487,414   205,487,352   f W95 Ext d (LBA)
/dev/sda5         174,578,418   205,487,414    30,908,997   7 HPFS/NTFS
/dev/sda6                 189   167,381,234   167,381,046  83 Linux
/dev/sda7         167,381,298   174,578,354     7,197,057  82 Linux swap / Solaris
/dev/sda2    *    205,503,480   418,766,354   213,262,875   7 HPFS/NTFS
/dev/sda3         418,766,355   441,289,484    22,523,130   7 HPFS/NTFS
/dev/sda4         441,289,485   488,392,064    47,102,580   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        F20024A8002475AF                       ntfs       Files                         
/dev/sda3        56309031309019D7                       ntfs       Films                         
/dev/sda4        E0DC5301DC52D200                       ntfs       Hck                           
/dev/sda5        D88C02738C024D06                       ntfs                                     
/dev/sda6        8ee745ba-7d3a-403c-9557-74a8e56270a0   ext4                                     
/dev/sda7        a29ad160-bb08-4ecf-b2bc-a84db55bb161   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect 


```

---

### Post by Rubi1200 on 2010-11-27
Was your system booting normally prior to the upgrade? In other words, were you able to boot into both Windows and Ubuntu?

The reason I ask is because you have an unusual partition setup.

If Ubuntu was on sda6, there is definitely a problem right now:[FONT=monospace]
[/FONT]> Mounting failed:[FONT=monospace]
[/FONT]mount: unknown filesystem type 'ext4'

I suggest you try fixing the file-system from the LiveCD first. If that doesn't work, we will try and figure something else out.

Run the following commands:

```
sudo e2fsck -C0 -p -f -v /dev/sda6
```

If there are errors, run this:

```
sudo e2fsck -f -y -v /dev/sda6
```

---

### Post by Wissem R on 2010-11-27
> **Rubi1200 said:**
> Was your system booting normally prior to the upgrade? In other words, were you able to boot into both Windows and Ubuntu?
Yes it was perfect .

> **Rubi1200 said:**
> The reason I ask is because you have an unusual partition setup. 
I know lol it was clean at first but I re partioned everything to make ubuntu disk space a little bigger(I'm using it as my primary OS ;) )




> **Rubi1200 said:**
>  I suggest you try fixing the file-system from the LiveCD first. If that doesn't work, we will try and figure something else out. 

Still not working...When I try to mount the ubuntu partition I get this error:

**The volume uses the ext4 file system which is not supported by your system.**

allthough using Gparted it shows that the partitions uses ext3 !

---

### Post by Rubi1200 on 2010-11-27
Wissem R,
do not try and mount the file-system! The commands need to be run on an unmounted system.

Use GParted to unmount all partitions, including swap and then try running the commands in the terminal. 

As I said, this must be done from the LiveCD.

EDIT: if the commands work, you should be able to reboot, taking the CD out, and be back in business.

---

### Post by Wissem R on 2010-11-27
It didn't work when i restart it and did boot from my hard drive instead of the cd live and im pretty sure that all partition are unmouted :(

---

### Post by dino99 on 2010-11-27
to boot on cd you need first to set the bios to boot on cd of course, otherwise it continue to boot on hdd (logical indeed)

question: are you still using karmic or more recent ? If grub2 is used, is grub1 (legacy) and menu.lst removed ? (because they are not good friends)

/dev/sda6 might be bootable (actually its sda2 which is ntfs)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Rubi1200 on 2010-11-27
As dino99 said, you need to go into BIOS and change the boot order so that the CD is set in first place. On most computers, F2, F8, or F12 will get you into BIOS.

Once the boot order is set so that the CD is first, then try again.

Simply get to the desktop on the LiveCD, go to the terminal and run the commands I posted.

If this still does not work, we can try something else.

---

### Post by Wissem R on 2010-11-27
I was using Mandriva for about 6 months ,ubuntu for 4 until now ,so I know how to configure BIOS to boot the cd :tongue:

> **Rubi1200 said:**
> 
Simply get to the desktop on the LiveCD, go to the terminal and run the commands I posted.

If this still does not work, we can try something else.

I'm afraid it dosen't.Is there another thing we can check ? Please I 'm not returning to Windows again !!

---

### Post by Rubi1200 on 2010-11-28
I am beginning to wonder if part of the problem has to do with the fact that Windows is in an extended partition?

Perhaps try recovering the Windows bootloader and then we can work from there.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Wissem R on 2010-11-28
Still nothing so far :(

Can I upgrade the system again ? Maybe it will be fixed ?
I ll just run:
> chroot /media/ubuntu /bin/bash
apt-get update;apt-get upgrade
But I couldn't mount the Linux's partition ...
**mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab**

$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0

---

### Post by Wissem R on 2010-11-28
I ll just switch to debian ;)
Thanks a lot for your time and the help thought .

---

### Post by Rubi1200 on 2010-11-28
Have you been using an Ubuntu CD to do the things we asked or another one?

Which version CD are you using to do this?

Perhaps a fresh install to sda6 would be the best option?

Either way, I hope you stick with Linux.

---

### Post by Wissem R on 2010-11-28
Yes of course I was using Ubuntu 9.10 Live CD.Sorry but I didn't understand what you want to say by a fresh install to sda6 ?

I should take a look to  my Hard drive and re partition the hole thing.It 's in a big mess right now :(

---

### Post by Rubi1200 on 2010-11-28
There seem to be so many issues going on that you may need to reinstall.

However, before doing that, let's try something else (but I don't know if it will work).

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

If you can chroot into the system, run some commands and do some "housecleaning"
```
apt-get autoclean
apt-get clean
apt-get update
apt-get upgrade
apt-get -f install
dpkg --configure -a
```
When you are finished, exit and unmount:
```
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt
```

---

### Post by Wissem R on 2010-11-28
I get this error as usual :'(

**mount: unknown filesystem type 'ext4'**

---

### Post by Rubi1200 on 2010-11-29
The only other possibility I can think of which might help is to use Testdisk to try and either recover the partition or rescue your data. Other than that, you may have little choice but to reinstall Ubuntu.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Wissem R on 2010-11-29
For rescuing my data I found a good tutorial on how to do it with virtual box :D
BTW I really apreciate your   help,just one last thing what is the best partitioning you can think of for my Hard Drive(A partition For Linux and another little one for WindoZe)

---

### Post by Rubi1200 on 2010-11-30
No problem, you are more than welcome :)

As far as partitioning is concerned, I think it really depends on your needs.

If you only plan on using Windows now and again, a smaller partition (must be primary) of about 50GB would most likely be enough.

That would leave you with 200GB for Ubuntu.

---

