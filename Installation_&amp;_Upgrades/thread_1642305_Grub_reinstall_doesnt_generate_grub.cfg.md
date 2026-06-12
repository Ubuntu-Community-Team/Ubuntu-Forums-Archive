---
title: "Grub reinstall doesnt generate grub.cfg"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by siddhartpai on 2010-12-10
I have ubuntu 10.10 running on my HP dv5 pavilion laptop
So today i tried to reinstall grub on my pc ..
i removed grub-pc and grub-common using synaptic
then booted up with a live cd of ubuntu 10.04
i then mounted sda11 to mnt
using 
sudo mount /dev/sda11 /mnt
sda11 being my ubuntu directory containing the /boot
then i installed grub to it
using 
sudo grub-install --root-directory=/mnt /dev/sda
it reported as installation finished.No error reported
then i unmounted /mnt 
and checked for /boot/grub/grub.cfg
seems like the file is missing
so are the files in /etc/grub.d/
so please help me to reinstall my grub back

---

### Post by siddhartpai on 2010-12-10
```
                  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #11 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             208,894   488,394,751   488,185,858   5 Extended
/dev/sda5          28,209,152   128,206,847    99,997,696   7 HPFS/NTFS
/dev/sda6         128,208,896   228,206,591    99,997,696   7 HPFS/NTFS
/dev/sda7         228,208,640   268,206,079    39,997,440   7 HPFS/NTFS
/dev/sda8         268,208,128   368,205,823    99,997,696   7 HPFS/NTFS
/dev/sda9         368,207,872   488,394,751   120,186,880   7 HPFS/NTFS
/dev/sda10         26,193,920    28,194,815     2,000,896  82 Linux swap / Solaris
/dev/sda11            208,896    24,240,127    24,031,232  83 Linux
/dev/sda12         24,242,176    26,185,727     1,943,552  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       87e12758-e604-4232-990d-58f3590d0a61   swap                                     
/dev/sda11       948dea34-8d15-43fd-9694-4914384351c9   ext4                                     
/dev/sda1        2A223A74223A44DB                       ntfs       System Reserved               
/dev/sda12       db534f61-cb92-4c19-99c1-d3a60b47b7f4   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0E5A1C565A1C3D41                       ntfs       Soft Stuff                    
/dev/sda6        F4CC5D0CCC5CCB0E                       ntfs       Chill                         
/dev/sda7        8C5E2DC65E2DA9C2                       ntfs       WinDoze                       
/dev/sda8        2CE637D7E6379FCE                       ntfs       Miscellaneous                 
/dev/sda9        1E02C26C02C2490B                       ntfs       Music                         
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda8        /media/Miscellaneous     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda11       /media/948dea34-8d15-43fd-9694-4914384351c9 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda11       /mnt                     ext4       (rw)


=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda11      /               ext4    errors=remount-ro 0       1
/dev/sda10      none            swap    sw              0       0

=================== sda11: Location of files loaded by Grub: ===================


   6.8GB: boot/grub/core.img
   3.6GB: boot/initrd.img-2.6.35-22-generic
   4.4GB: boot/initrd.img-2.6.35-23-generic
   6.8GB: boot/vmlinuz-2.6.35-22-generic
   6.9GB: boot/vmlinuz-2.6.35-23-generic
   4.4GB: initrd.img
   3.6GB: initrd.img.old
   6.9GB: vmlinuz
   6.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by Rubi1200 on 2010-12-10
Hi and welcome to the forums :)

As you suspected, you are definitely missing files.

The best way to deal with this is to purge and reinstall GRUB from the LiveCD.

The following fantastic guide by drs305 uses the chroot method to accomplish this task:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You must use the chroot method, mount sda11, and install GRUB to the MBR.

Good luck and let us know what happens.

---

### Post by siddhartpai on 2010-12-10
I solved it myself by using the chroot procedure..
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Thanks Everybody
To Admin Please Close the Topic

---

### Post by Quackers on 2010-12-10
siddhartpai, it's you that can mark the thread as solved using the thread tools near the top of the page :-)

---

### Post by Herman on 2010-12-10
:D Hmmm, interesting thread!

So you learned that when GRUB is installed, (as part of the operating system), it consists not only of the obvious files in /boot/grub that everyone knows about, but is also made up of important files in /etc, /usr/bin, usr/lib and usr/share. 
If you want to see the complete list you can open Synaptic Package Manager and search for 'grub-pc', then look in the 'installed files' tab there. 
When you completely remove GRUB with Synaptic Package Manager, it removes all of the GRUB files from the whole operating system, so you lose all the commands associated with GRUB like grub-install and grub-mkconfig too.

The grub-install command you used from the Live CD creates the /boot/grub directory and fills it up with GRUB files, all except for the grub.cfg.
A different command is needed to create the /boot/grub/grub.cfg file, either grub-mkconfig or update-grub (which is just another name for grub-mkconfig, but easier for new users to remember).
The grub-install command doesn't install all the other GRUB files in the operating system such as in /etc and /usr though, you need to use apt-get or synaptic to install the entire grub-pc package, so that's why you needed to chroot.

I imagine explaining this will seem like 'overkill' for some of us, but the extra explanation might be of some benefit to new users who may be wondering what's going on here.   :)

---

### Post by Quackers on 2010-12-10
I have to admit to be somewhat confused by this.
I would have put the lack of /boot/grub/grub.cfg down to an installation error (not knowing any better :-) ). Otherwise how would the chroot method be any different? It still installs grub to the mbr of the drive and the grub files to sda11 (in this case) by mounting that partition first.
Am I missing a link here?

---

### Post by Herman on 2010-12-10
Okay, I'll explain what I think happened.

First, the OP used Synaptic Package Manager to remove the grub-pc package,
> I have ubuntu 10.10 running on my HP dv5 pavilion laptop
So today i tried to reinstall grub on my pc ..
i removed grub-pc and grub-common using synapticNow, if you tak a look in your own Synaptic Package manager and search 'grub-pc', then right-click on the grub-pc line and click 'properties', and go to the 'installed files' tab you can see all the files in the grub-pc package and where they are placed in the file system.

Now, if you go take a look at some of those files, you be able to see which ones the OP says were removed, and the list includes scripts and programs associated with GRUB, such as /usr/sbin/grub-install, /usr/sbin/grub-reboot, /usr/sbin/grub-set-default, /usr/sbin/grub-setup, /usr/sbin/update-grub, /usr/bin/grub-mkimage and so on.

Okay, so at this point it's no use trying to run grub-install or any other command from within the operating system because all of those programs have been removed, they're gone.

Re-installing GRUB with Synaptic Package Manager or apt-get would have fixed it though, because that would have put all those programs that are part of the grub-pc package back where they belong again.

Instead, the OP chose to reboot, and re-install grub from a Live CD. 
That only installs the files in /boot/grub, plus installs GRUB to MBR. 
It doesn't re-install any of the GRUB files from the grub-pc package that live deeper inside the operating system.
> then booted up with a live cd of ubuntu 10.04
i then mounted sda11 to mnt
using 
sudo mount /dev/sda11 /mnt
sda11 being my ubuntu directory containing the /boot
then i installed grub to it
using 
sudo grub-install --root-directory=/mnt /dev/sda
it reported as installation finished.No error reported
then i unmounted /mnt 
and checked for /boot/grub/grub.cfg
seems like the file is missing
so are the files in /etc/grub.d/
so please help me to reinstall my grub back The grub-install command never did make a grub.cfg file either, we need to use grub-mkconfig separately for that.
(As a little irrelevant info on the side, most people say they use 'update-grub', but that only runs a script that runs 'grub-mkconfig', so they're still using grub-mkconfig but they don't know it.)

So correctly, Rubi1200 advised:
> The best way to deal with this is to purge and reinstall GRUB from the LiveCD. ... and if you read fantastic guide by drs305 about using the chroot method to accomplish this task: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099), you will see in step 3 where it explains how to purge grub packages and in step 4 where drs305 demonstrates re-installing grub with an apt-get command.
So in other words all the scripts and programs normally associated with GRUB that live elsewhere in the operating system are now replaced, not just the grub files in /boot/grub.

The files in /boot/grub are all that are required to boot the operating system, providing you have a grub.cfg unless you can use GRUB's command line. To run update-grub or grub-mkconfig we need all those other programs that come with the grub-pc package.

Sabbe?  :)

---

### Post by Quackers on 2010-12-10
Thank you for your detailed response Herman :-)

I am somewhat familiar with drs305's excellent guide(s) :-)
In fact the purge/re-install grub is my most used link ;)

---

### Post by drs305 on 2010-12-10
Herman's analysis is, as usual, spot on.

Since this thread is going into some detail on this, I'll add the reason to purge/install rather than just a "--reinstall". For whatever reason, if a user intentionally or unintentionally deletes or renames a file, the system remembers that action. On a reinstall, APT will restore missing packages *if they were not removed or renamed (by root)*. So if Grub 2 is failing because the user removed/renamed a file, a simple reinstall will not normally replace the manually-removed file and the package will remain broken.

If the entire package is removed (purged), all the files are installed and the package should be returned to working order. Since in many cases we may not know the reason the files are missing or corrupted, purging first offers the highest likelihood the action will succeed.

---

### Post by Herman on 2010-12-10
:p Cool! Thanks for taking the time to explain that, drs305, now it was *my* turn to learn something, thank you for sharing. 

and thank you too, Quackers, for your excellent question. :)

---

### Post by Quackers on 2010-12-10
I have this hunger to know things :-) Particularly about grub2.

---

