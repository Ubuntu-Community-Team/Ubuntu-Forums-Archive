---
title: "i cant boot in windows xp."
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by alx_gom on 2010-08-10
i have two HD. 
in one i have windows xp, i just installed ubuntu in the other, but now i cant boot in windows.

---

### Post by alx_gom on 2010-08-10
also, i cant install sofware from ubuntu software center.
it says " Previous installation hasn't been completed.  the installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software"

---

### Post by oldfred on 2010-08-10
Did you try
sudo update-grub
That will usually find windows.

To update system from command line - may need sudo in front of each line as I copied this from a chroot version that does not need sudo:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by alx_gom on 2010-08-11
thanks. that solve the ubuntu software problem.
but i still cant use windows.
is there any way i can see if the HD with windows still has it?
in disk utility it apears as bootable, partition type: HPFS/NTFS (0x07), type NTFS, device: /dev/sdb1.

---

### Post by cavalier911 on 2010-08-11
Open nautilus file manager,the drive will be in the left column.You have to click on the drive to mount,the files will be on the right. Is there a boot menu with ubuntu and winxp listed ? Or no menu and you boot into ubuntu ?

---

### Post by alx_gom on 2010-08-11
the boot info script was really helpfull, i still have the xp.
but i dont know how to boot it.
i dont see any boot menu in the file browser

---

### Post by alx_gom on 2010-08-11
if it of any use. these are the results ive got.
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    75,239,423    75,237,376  83 Linux
/dev/sda2          75,241,470    78,163,967     2,922,498   5 Extended
/dev/sda5          75,241,472    78,163,967     2,922,496  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5da985e6-6608-47a7-869e-482cb82360b4   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        44964e36-6dcc-48d3-9dff-6abadc6a3cf8   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F8209B4D209B11AC                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/F8209B4D209B11AC  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

---

### Post by cavalier911 on 2010-08-11
Open terminal:
```
sudo update-grub
```Reboot,if it detected winxp on /dev/sdb the grub menu will appear.
If no menu appears once your in ubuntu you'll make a custom entry.
```
gksudo gedit /etc/grub.d/40_custom
```Add this entry below everything else on the file.
```
menuentry "Microsoft Windows XP" {
    insmod chain
    set root=(hd1)
    devicemap -s hd0 hd1
    chainloader +1
}

```Save the file,verify that it's executable,rerun sudo update-grub to add entry to grub menu,reboot.
Boot menu should appear with winxp boot option. Hold down Shift key after power on to force menu to appear if it doesn't.

---

### Post by oldfred on 2010-08-11
You seem to be missing the boot files. Did you have another copy of windows installed? Windows moves the boot files to one copy to allow booting and if you then delete that copy the second is missing its boot files.

Should be this:
Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
You have this:
Boot files/dirs:   

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

[http://ubuntuforums.org/showthread.php?p=5726832](http://ubuntuforums.org/showthread.php?p=5726832)

Or you can run windowss repairs from the XP install disk. You may also have to update boot.ini

---

### Post by cavalier911 on 2010-08-11
If you install Windows 7 or Vista after WindowsXP even on another drive it wipes out critical boot files on Windows XP ? So when you remove Vista/Win7 you have to restore these bootloader files for Windows XP . I guess this might explain why grub2 did not detect WindowsXP and autoconfigure a menu entry.What happens if you have Win7/Vista installed and then add WinXP to  multiboot and then remove Vista/Win7. I guess since WinXP was last installed it's boot loader is untouched and functional? 

Ignore my previous post about creating the custom menu for now. Follow oldfred's info for restoring winxp's bootloader files, after that run sudo update-grub and maybe grub will autoconfigure the menu for winxp.

---

### Post by alx_gom on 2010-08-11
it's fixed. thanks to all. i followed what oldfred said.

---

