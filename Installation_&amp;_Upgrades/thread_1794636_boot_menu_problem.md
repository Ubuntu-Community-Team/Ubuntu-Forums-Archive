---
title: "boot menu problem"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by lodhaakshay on 2011-07-01
In my PC i have 2 harddisk one is 80gb nd other is 500gb.In 80gb, 50gb is for windows and remaining i am using for ubuntu.The problem is after installing ubuntu i do not get the boot menu option for selection of different operating system.I tried all the method but in vain.I know the problem here is with boot menu but i am not getting the solution.

---

### Post by pawhtiobo on 2011-07-01
Hi,

Whats the behavior of the boot of the machine, does it boot directly to Ubuntu? Does it not boot at all?

See ya...

---

### Post by drs305 on 2011-07-01
lodhaakshay,

Welcome to the Ubuntu forums. Try holding down the SHIFT key during boot and see if the menu is displayed. If the menu shows up, is Windows on the menu? 

The default action of Grub is to boot directly into Ubuntu if it doesn't know about other OS's. To get Grub2 to recognize Windows, boot into Ubuntu and then run:
```
sudo update-grub
```
Watch the terminal returns - if it finds Windows as the command runs there should be a Windows entry and the menu should display the next time you boot.

---

### Post by lodhaakshay on 2011-07-01
the problems is not able to be get solved as ubuntu first get installed very well.But after installation it asked for reboot required and then it never boot into ubuntu at all.By default windows xp get booted.So i cannot even get into ubuntu to solve the problem suggested by you.So plz give some way so that i can get rid of this problem.

          And thanx to all of you for your reply given before.

---

### Post by georgelab on 2011-07-01
Use a Ubuntu live CD to recover grub.

---

### Post by YesWeCan on 2011-07-01
[FONT=Nimbus Sans L, sans-serif]We'd better have a look at what is where. Would you download and run this and post RESULTS.txt here? BootInfoScript: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)[/FONT]

---

### Post by lodhaakshay on 2011-07-01
this are the content of result.txt
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 74dd8a70-5da9-45a2-817f-73addda37ce0 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb1 has 
                       307199999 sectors, but according to the info from 
                       fdisk, it has 976768001 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 NTFS / exFAT / HPFS
/dev/sda2         102,398,310   147,910,454    45,512,145  83 Linux
/dev/sda3         147,910,455   156,296,384     8,385,930  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   976,768,064   976,768,002  42 SFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        10389B56389B39A4                       ntfs       
/dev/sda2        66954053-cdc0-489e-be55-af9b13c46861   ext4       
/dev/sda3        58448170-d841-4116-8eb5-ecb9bf7f5a4f   swap       
/dev/sdb1        6AF499DBF499AA39                       ntfs       Entertainment
/dev/sdb2        0C0CA7470CA72B22                       ntfs       Software
/dev/sdb3        4A48B1AE48B19961                       ntfs       Akshay

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb3        /media/Akshay            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb2       /               ext4    errors=remount-ro 0       1
/dev/sdb3       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  55.459738731 = 59.549441024   boot/initrd.img-2.6.32-21-generic              1
  55.698370934 = 59.805670400   boot/vmlinuz-2.6.32-21-generic                 1
  55.459738731 = 59.549441024   initrd.img                                     1
  55.698370934 = 59.805670400   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

thanx for the advise.Hoping now that the problem get's the solution.

---

### Post by lodhaakshay on 2011-07-02
waiting for the reply...........

---

### Post by drs305 on 2011-07-02
It looks like at one time you tried to install Wubi but you now have an Ubuntu installation on sda2. Grub isn't installed, so you can install Grub2 via an Ubuntu LiveCD. You will lose the Windows bootloader if you do this but Windows should be a menu option in the Grub menu if you want to do this.

To install Grub2, you will have to 'chroot' into your Ubuntu partition. If you need explanations of these commands, please refer to the 'Chroot' link in my signature line. It provides additional guidance.

Boot the LiveCD, then:
```
sudo mkdir /mnt/temp
sudo mount /dev/sda2 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo chroot /mnt/temp

```
You should now be at a 'root' prompt. 'sudo' is no longer required.
```

apt-get update
apt-get install --reinstall grub-common grub-pc
```
At the first prompt, TAB to OK. When asked for the installation location, choose "sda" with the SPACEBAR, then TAB to OK. Do not select (*) any partition, only sda.
When back at the prompt,
```
exit
```
This exits the chroot. Now unmount and reboot:
```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
sudo umount /mnt/temp

```
Reboot.

If you still have problems, please rerun the boot info script and post the new RESULTS.txt.

---

### Post by lodhaakshay on 2011-07-02
hi,
 i tried today to install ubuntu again..nd i dont know how but now itz working..
but while booting it display the error as "error:Forcing to 32mgart size(because of ASIC bug?)"..wats d problem?
 And one more thing it is not recognizing m harddisk..so everytime i am working in ubuntu i have to go to system->administration->disk utility and mount the volume..Is der any permanent solution..

And thank you all the expertise for your post..

---

### Post by drs305 on 2011-07-02
Are you using a Radeon ATI video card?

If so:
I found a few kernel bugs which produce this error message. In those cases, adding a kernel parameter at boot seemed to help.

Hold down the SHIFT key during boot. At the grub menu, press 'e' to edit the first menuentry.

Go to the 'linux' line, cursor to the end and add **radeon.modeset=0** to the end of the line, then press CTRL-x to boot. If it now boots, let us know and we can tell you how to make it permanent.

---

