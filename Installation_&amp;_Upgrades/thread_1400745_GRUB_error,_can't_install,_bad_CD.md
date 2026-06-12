---
title: "GRUB error, can't install, bad CD?"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by Melyans on 2010-02-07
Hi people, i saw many threads with the same problem, but I've been reading and it seems like for each case there's a diferent solution and i couldnt find any that has exactly my problem, so i open this cz i'm really a noob on this and dont want to keep playing arround and keep making things worst. I'll try and do this as short as i can. Please help me :sad:

I dual-boot WIndows XP and Ubuntu 9.10 a week ago, with a partition for each and an extra one for files (NTFS). I was really happy cz installation was rather easy and it was working well, i just wanted the third partition (Labeled "THINGS") to automount itself on start. Someone told me to modify the fstab file wich i did and then the partition couldnt be mounted and all the modifications i tried on the fstab (following other people's advices) didnt work, so since i hadnt really done anything on ubuntu so far i erased the entire ext4 and swap partitions (from live CD) and installed it again. 

It was all well again but i still wanted the get the mounting thing right, this time i tried with mout manager wich aparently on the first time i opened it it made the mountings without asking (?) in this part i'm not sure whether it added to the fstab file the first partition (the one with the xp on it) wich i didnt want it to. So i checked the options and indeed the first partition was to be mounted on start i disabled that, also i configurated so everybody could mount the "THINGS" partition. So i thought that was ok, when i opened nautilus i noticed that the free space on the THINGS partition was really small, so i opened Gparted and saw that the free space on it was left aside on its right, when i tried to modify that, Gparted said that to do it i had to unmount it so i said "Ok, unmount it" i guessed it could hurt cz i had mounted and unmount it before, right? and it did, and it was a waste of time cz thats when i discovered u cant expand a partition on that direccion or at least i coudnt do it (by this time i was starting to get really upset) i closed gparted, and tried to open THINGS but and error message came up saying it couldnt be mounted, unfortunatly i cant show it cz many things happened and i lost the file where i had saved it

So i freeked out thinking i had damaged the THINGS partition wich had 80 Gb of movies and music, wich obviously i can get again but it still sucks to loose it, i luckily backed up all the important things before installing ubuntu the first time. So i thought that if i could see it from windows then i would be calm enough to look for the solution, so i restarted and choose windows on the GRUB menu but before it started blue screen comes up (:rolleyes:) and it says "chkdsk is about to start u have 5 seconds to cancell it"

WHAT!! (4 seconds) WHY (3 seconds) I (2 seconds) DONT (1 second) KNOW ................ and it started :confused:
so i said maybe this is good, maybe it will fix whathever i did before [-o<  (I swear in other aspects of life i'm not that much of an idiot :S) So windows finally started and all the files where there, "THANK GOODNESS" i thought (again the idiot thing)...

And then when i restarted:

```
GRUB loading
error: unknown filesystem
GRUB rescue>
```:cry: This is when i totally lost it...:cry:
After picking up fights with half the family i tried to start live CD session and it did! and all the files were and are still there so i figured i'll erase this partition if its the one making all this problem... i used the free space that was left aside to make a new partition "LITTLE THINGS" and slowly moved the files... really slowly cz i had to modify the space, then mount, then move the files, then restart cz i didnt want gparted mount or unmount anything, and then do that all over again... i was finally left again with 2  NTFS partitions and free space between them to re install UBUNTU, but before that i thought that since i had totally erased ubuntu, the GRUB should be gone and i'd be able to start on windows at least, WRONG, i tried and the GRUB rescue still comes up, i also may add that during this process sometimes it would not start the live CD even if it was booted to do so and the CD was on the tray, it would go straight to the GRUB rescue and i qould restart it a couple of times untill the live CD actually worked.

I tried again to install UBUNTU but it starts installing and after a while it gives an error wich i will post later cz i'd have to try the instalation again to get it, it said something like maybe the CD or another device is bad

I did the boot_info_script that darkod posted on a couple of threads and this is what comes up

```
 ============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x824cc067

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    53,785,619    53,785,557   7 HPFS/NTFS
/dev/sda2          53,785,620    96,743,429    42,957,810   5 Extended
/dev/sda5          53,785,683    94,863,824    41,078,142  83 Linux
/dev/sda6          94,863,888    96,743,429     1,879,542  82 Linux swap / Solaris
/dev/sda3          96,743,430   312,576,704   215,833,275   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7CAC539DAC53512E                       ntfs       Meli                          
/dev/sda3        6A3143F10F9BECF6                       ntfs       cositas                       
/dev/sda5        8ab2446f-3083-4cbc-9115-5b4dfac72f64   ext4                                     
/dev/sda6        1a750c95-9fa8-45a3-accc-79992772beac   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda5        /target                  ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=8ab2446f-3083-4cbc-9115-5b4dfac72f64 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1a750c95-9fa8-45a3-accc-79992772beac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```Ps: i'm a spanish user
sda 2, 5 and 6 where created during the failed instalation, wich i'll have to erase to try and install again to show u the error it shows, should i do that?

sda3 is the "Little THINGS " (in spanish, "Cositas") partition but i hav never installed there any OS, nor vista nor W7... i do not even have the tools to install them, i have no idea why it says that

Btw, everything i have tried i did following tutorials and advice posts, cz i dont know much and i know i dont know, but i was told Ubuntu wouldn be hard on me, i just had to get used to it

Thanks for reading! i know it came up long, i hope u can help me, i wasnt lucky on spanish forums...

---

### Post by darkod on 2010-02-07
You are trying too much at the same time. Slow down, don't do so many things or you can really mess it up.
So far it seems you haven't lost any data which is great. First it would be best to restore windows bootloader on the MBR, so at least you can boot XP directly. Boot again into 9.10 live desktop and in terminal do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore any warnings. That will install windows bootloader to the MBR of your hdd, /dev/sda.

Reboot and XP should boot directly. Check you data partition (little things) if everything is there. Also make a backup if you can, just in case.

After that, when you decide to install ubuntu again, first boot into live desktop, open Gparted and delete /dev/sda5, /dev/sda6 and /dev/sda2, all the partitions created by previous ubuntu install. Note that for /dev/sda6 you will probably have to do right-click Swapoff to unmount it before you can delete it.
This will leave unallocated space on your hdd. Then just boot again with ubuntu cd, Install Ubuntu options, and in step 4 tell it to Use Largest Available Free space. That will install it into the unallocated space.

IMPORTANT NOTE: If you still want to automount ntfs partition after you have reinstalled ubuntu, forget about editing fstab. You can do it that way, but it's risky and it already failed for you. These days there are ready tools you can use. Open terminal and install ntfs-config:

sudo apt-get install ntfs-config

It will be in System-Administration. With the ntfs partition UNMOUNTED, open the program and it will detect it, and ask you if you want to mount every time at start, and with which permissions. It works great. I recommend you do it that way, instead of messing with fstab.

---

### Post by Melyans on 2010-02-07
THANK YOU!! thank u so much for answering that fast and solving my problem!!

If i could i would fly to wherever u are and kiss u, i swear!!!
=D> =D> =D>

Should i retry Ubuntu now? I do want Ubuntu, i do like it a lot more than windows, and i want to give it another chance but at this point i'm scared next time my pc will explode =S, what do u think about Wubi?? a friend told me its better

Ps: if someone goes through the same when i first tried sudo apt-get install lilo it told me it had to erase gdm-guest-session but it couldnt do it (firefox was open)
so i copied the intruction on paper, re open the live cd session and retried it without opening anything but the terminal and it work perfectly :D

Edit: i almost forget, when windows started it did the chkdsk again on the little things partition =S i'm scared to turn the computer off now =S could that bring me more problems?

---

### Post by darkod on 2010-02-07
Doing a chkdsk shouldn't be a problem. In fact, windows is so stubborn about chkdsk that it can be a problem if you don't let it do it when it wants it. Just reboot and see how it goes, no problem.

I would recommend full install of ubuntu, not wubi. Your ubuntu was working fine, as you said. It was probably something got messed up when you tried modifying fstab, maybe even the instructions were unclear or for older version of ubuntu.

Use the ntfs-config tool, it works great.

Use XP for a while if you want, backup your data, and you can always delete the older ubuntu partitions and install it again as I said before.

---

### Post by Melyans on 2010-02-07
Thank u very much again! =D 

i'll try again... i hope i come back here to help and not be helped XD

---

