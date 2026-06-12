---
title: "Ubuntu 10 over Fedora 14"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by sumitk on 2011-01-20
Hi All,

(Sorry for the duplicate post. Please reply here)

I have recently started working on Ubuntu & really liked it :KS**awesomeness!!:KS** But few days back, just out of curiosity I thought of trying the new fedora14:-s. So I tried the live CD but since my dvd rom is not in a good condition, the whole thing was really slow. So I thought of installing it along with my other OS. 

Previously I had Ubuntu10.10 & win xp. So I went ahead, backed up all my data from Ubuntu, and installed fedora14. My partitions were like this:

/dev/sdb2       ----  Extended
   /dev/sdb5    ----  Fat32  (common partition for Ubuntu & Win xp)
   /dev/sdb9    ----  ext4   (Fedora  "  /  "  )
   /dev/sdb10  ----  linux-swap  (Fedora's swap)
   /dev/sdb7    ----  linux-swap  (Ubuntu's swap)
   /dev/sdb)   ----  ext4   (Ubuntu   "  /  "  )

While in the middle of installation, it asked me about the grub configuration. It had option like this:

Other (/dev/sdb1)
Fedora (/dev/sdb9)

I was confused as it didn't recognise my Ubuntu partition which was** /dev/sdb8**. 

So I used the _**Add**_ option visible there and named it Ubuntu, picked /dev/sdb8 from the location drop down menu, and made it the default boot option. So now the list becomes like this:

Other (/dev/sdb1)
Ubuntu (/dev/sdb)
Fedora (/dev/sdb9)
 
I also kept the **Grub install location as the default** which was the name of my laptop hard drive. The installation went as usual but when I rebooted the system, the Grub of Fedora comes up and when I choose Ubuntu my Ubuntu doesn't starts. Instead I am getting a message which goes something like this "Wrong executable selected..." So now I had Win xp and Fedora working on my laptop. 
[B]
_Ques1:_ Is there any way I can configure the grub of Fedora to boot Ubuntu just like win xp is getting booted up.?[/B]

Then I thought I might have overwritten the previous grub. So I did the other way round. I have already installed Fedora14 so I then started installing Ubuntu. It still doesn't recognise my previous partition. So I went ahead with full new installation of Ubuntu on the same location. Now I can see the grub of ubuntu but Fedora is not booting.

_**Ques2: **_**Is there something obvious that I am doing wrong? I think it has something to do with the Grub so could anyone please explain me how I need to configure it.?**


Thanks a lot!!
The forum is gr8 as this is my 1st question ever. I got all my answers here!

---

### Post by coffeecat on 2011-01-20
This is, in my opinion, the biggest irritation in Fedora; that it doesn't set up grub to recognise another Linux distro, only Windows. As you've found, you can add an entry but you have to know how to put in all the code. Which is OK for the advanced user - Fedora's target - but not for the relatively inexperienced.

Fedora uses legacy grub, Ubuntu the newer, more powerful but more complicated grub2. You have two choices. You can reinstall Ubuntu's grub using the Ubuntu live CD and get Ubuntu's grub to give you a triple-booting menu. Or you can manually edit Fedora's menu.lst to get a triple-booting menu. I - or others - can help you with either. To get the information we need, boot either into Fedora or into a live Ubuntu CD, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file within code tags for legibility. You can use the # icon in the message toolbar for this.

---

### Post by sumitk on 2011-01-20
Thanks for the quick reply. Copied are the contents of my RESULTs.txt

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 
    215709168 on boot drive #1 for the stage2 file. A stage2 file is at this 
    location on /dev/sdb. Stage2 looks on partition #9 for 
    /boot/grub/grub.conf.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    83,971,754    83,971,692   7 HPFS/NTFS
/dev/sdb2          83,971,816   312,576,704   228,604,889   f W95 Ext d (LBA)
/dev/sdb5          83,971,818   210,483,629   126,511,812   b W95 FAT32
/dev/sdb6         288,784,503   312,576,704    23,792,202   b W95 FAT32
/dev/sdb7         249,481,216   251,481,215     2,000,000  82 Linux swap / Solaris
/dev/sdb8         251,482,112   288,784,383    37,302,272  83 Linux
/dev/sdb9         210,487,296   247,377,919    36,890,624  83 Linux
/dev/sdb10        247,379,968   249,473,023     2,093,056  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb10       3986bc4c-3fc5-4d67-b3e8-b53849979996   swap                                     
/dev/sdb1        AAB43474B43444DB                       ntfs       Sumit1                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        93B8-D352                              vfat       S_DEFINED)                    
/dev/sdb6        49DC-6973                              vfat       SUMIT3                        
/dev/sdb7        3ee7496f-b016-4a4b-861b-c07f98ec5a58   swap                                     
/dev/sdb8        290fbd47-ec06-4541-bc5d-532266a1725b   ext4                                     
/dev/sdb9        44036103-f2d1-45aa-93d7-fd696064cdff   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sda: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows" Windows 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=290fbd47-ec06-4541-bc5d-532266a1725b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=290fbd47-ec06-4541-bc5d-532266a1725b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=290fbd47-ec06-4541-bc5d-532266a1725b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=290fbd47-ec06-4541-bc5d-532266a1725b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set aab43474b43444db
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb9 during installation
UUID=290fbd47-ec06-4541-bc5d-532266a1725b /               ext4    errors=remount-ro 0       1
/dev/sdb8       none            swap    sw              0       0

=================== sdb8: Location of files loaded by Grub: ===================


 135.4GB: boot/grub/core.img
 141.8GB: boot/grub/grub.cfg
 129.9GB: boot/initrd.img-2.6.35-22-generic
 130.1GB: boot/initrd.img-2.6.35-24-generic
 135.4GB: boot/vmlinuz-2.6.35-22-generic
 135.4GB: boot/vmlinuz-2.6.35-24-generic
 130.1GB: initrd.img
 129.9GB: initrd.img.old
 135.4GB: vmlinuz
 135.4GB: vmlinuz.old

========================== sdb9/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,8)
#          kernel /boot/vmlinuz-version ro root=/dev/sda9
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=1
timeout=5
splashimage=(hd0,8)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.6-45.fc14.i686)
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.35.6-45.fc14.i686 ro root=UUID=44036103-f2d1-45aa-93d7-fd696064cdff rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.35.6-45.fc14.i686.img
title Ubuntu
    rootnoverify (hd0,7)
    chainloader +1
title Windows
    rootnoverify (hd0,0)
    chainloader +1

=============================== sdb9/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Wed Jan 19 21:43:08 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=44036103-f2d1-45aa-93d7-fd696064cdff /                       ext4    defaults        1 1
UUID=3986bc4c-3fc5-4d67-b3e8-b53849979996 swap                    swap    defaults        0 0
UUID=3ee7496f-b016-4a4b-861b-c07f98ec5a58 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sdb9: Location of files loaded by Grub: ===================


 110.4GB: boot/grub/grub.conf
 110.4GB: boot/grub/menu.lst
 110.4GB: boot/grub/stage2
 113.7GB: boot/initramfs-2.6.35.6-45.fc14.i686.img
 110.3GB: boot/vmlinuz-2.6.35.6-45.fc14.i686
=======Devices which don't seem to have a corresponding hard drive==============

sda

---

### Post by theozzlives on 2011-01-20
I tried to install Fedora on an existing Ubuntu box (no Windows) and it played hell with me. You might wanna boot the Ubuntu live CD and try the following:
```
sudo -i
mount /dev/sda? /mnt (The ? is your Ubuntu partition)
grub-install --root-directory=/mnt/ /dev/sda
```

Once you boot Ubuntu do:
```
sudo update-grub
```

It seems logical that all three would be found.

---

### Post by sumitk on 2011-01-20
> **theozzlives said:**
> 
Once you boot Ubuntu do:
```
sudo update-grub
```

Thanks for your reply.!! I had few question as I was reading other threads too...

If I do update-grub - [U][B]

Ques1: [/B][/U]Will it automatically detect the Fedora partition and insert it in the Ubuntu's grub ?

_**Ques2:**_ If later I upgrade Fedora then will the newer kernel be pointed by this same location in the Ubuntu's grub? Or do I need to upgrade it again?

I am little confused as I am still trying these things. Thanks for your patience.

---

### Post by theozzlives on 2011-01-20
> **sumitk said:**
> Thanks for your reply.!! I had few question as I was reading other threads too...

If I do update-grub - [U][B]

Ques1: [/B][/U]Will it automatically detect the Fedora partition and insert it in the Ubuntu's grub ?

Yes it should.

> _**Ques2:**_ If later I upgrade Fedora then will the newer kernel be pointed by this same location in the Ubuntu's grub? Or do I need to upgrade it again?

I never gave Fedora that much of a chance (didn't like it).

---

### Post by sumitk on 2011-01-20
Yeah I also didn't like it. Mostly because I have used Ubuntu for some time now !! Thanks for your help. I am gonna try that now.

---

### Post by coffeecat on 2011-01-20
@sumitk, you forgot to do this:

> **coffeecat said:**
> post the RESULTS.txt file within code tags for legibility. You can use the # icon in the message toolbar for this.

Please take time to learn the various forum facilities. It makes it much easier for people to help you.

To your problem. The commands theozzlives has posted are the way to go, but not as he has posted them - there are complications. You have no sda drive - which is odd. And your Ubuntu partition, which was originally sdb9, is now sdb8 following the installation of Fedora but is referred to as (hd0,msdos9) in Ubuntu's grub.cfg, which is grubspeak for sda9. 

I can't guarantee this will work, but try this. Boot up a live Ubuntu CD and open a terminal. now:

```
sudo mount /dev/sdb8 /mnt
```and...

```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```Now reboot. If you do successfully boot into Ubuntu, open a terminal, and:

```
sudo update-grub
```... which will put Fedora onto the Ubuntu grub menu.

If bootup fails, post back and we'll do something more complicated.

Question: did you use a live CD or live USB drive for the bootscript?

---

### Post by sumitk on 2011-01-20
> **coffeecat said:**
> 
Question: did you use a live CD or live USB drive for the bootscript?

I am sorry I missed that part. Here I am doing it again. For now I am using the Live Ubuntu 10.10 CD.

Thanks!!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 
    215709168 on boot drive #1 for the stage2 file. A stage2 file is at this 
    location on /dev/sdb. Stage2 looks on partition #9 for 
    /boot/grub/grub.conf.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    83,971,754    83,971,692   7 HPFS/NTFS
/dev/sdb2          83,971,816   312,576,704   228,604,889   f W95 Ext d (LBA)
/dev/sdb5          83,971,818   210,483,629   126,511,812   b W95 FAT32
/dev/sdb6         288,784,503   312,576,704    23,792,202   b W95 FAT32
/dev/sdb7         249,481,216   251,481,215     2,000,000  82 Linux swap / Solaris
/dev/sdb8         251,482,112   288,784,383    37,302,272  83 Linux
/dev/sdb9         210,487,296   247,377,919    36,890,624  83 Linux
/dev/sdb10        247,379,968   249,473,023     2,093,056  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb10       3986bc4c-3fc5-4d67-b3e8-b53849979996   swap                                     
/dev/sdb1        AAB43474B43444DB                       ntfs       Sumit1                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        93B8-D352                              vfat       S_DEFINED)                    
/dev/sdb6        49DC-6973                              vfat       SUMIT3                        
/dev/sdb7        3ee7496f-b016-4a4b-861b-c07f98ec5a58   swap                                     
/dev/sdb8        290fbd47-ec06-4541-bc5d-532266a1725b   ext4                                     
/dev/sdb9        44036103-f2d1-45aa-93d7-fd696064cdff   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sda: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows" Windows 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=290fbd47-ec06-4541-bc5d-532266a1725b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=290fbd47-ec06-4541-bc5d-532266a1725b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=290fbd47-ec06-4541-bc5d-532266a1725b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=290fbd47-ec06-4541-bc5d-532266a1725b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 290fbd47-ec06-4541-bc5d-532266a1725b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set aab43474b43444db
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb9 during installation
UUID=290fbd47-ec06-4541-bc5d-532266a1725b /               ext4    errors=remount-ro 0       1
/dev/sdb8       none            swap    sw              0       0

=================== sdb8: Location of files loaded by Grub: ===================


 135.4GB: boot/grub/core.img
 141.8GB: boot/grub/grub.cfg
 129.9GB: boot/initrd.img-2.6.35-22-generic
 130.1GB: boot/initrd.img-2.6.35-24-generic
 135.4GB: boot/vmlinuz-2.6.35-22-generic
 135.4GB: boot/vmlinuz-2.6.35-24-generic
 130.1GB: initrd.img
 129.9GB: initrd.img.old
 135.4GB: vmlinuz
 135.4GB: vmlinuz.old

========================== sdb9/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,8)
#          kernel /boot/vmlinuz-version ro root=/dev/sda9
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=1
timeout=5
splashimage=(hd0,8)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.6-45.fc14.i686)
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.35.6-45.fc14.i686 ro root=UUID=44036103-f2d1-45aa-93d7-fd696064cdff rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.35.6-45.fc14.i686.img
title Ubuntu
    rootnoverify (hd0,7)
    chainloader +1
title Windows
    rootnoverify (hd0,0)
    chainloader +1

=============================== sdb9/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Wed Jan 19 21:43:08 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=44036103-f2d1-45aa-93d7-fd696064cdff /                       ext4    defaults        1 1
UUID=3986bc4c-3fc5-4d67-b3e8-b53849979996 swap                    swap    defaults        0 0
UUID=3ee7496f-b016-4a4b-861b-c07f98ec5a58 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sdb9: Location of files loaded by Grub: ===================


 110.4GB: boot/grub/grub.conf
 110.4GB: boot/grub/menu.lst
 110.4GB: boot/grub/stage2
 113.7GB: boot/initramfs-2.6.35.6-45.fc14.i686.img
 110.3GB: boot/vmlinuz-2.6.35.6-45.fc14.i686
=======Devices which don't seem to have a corresponding hard drive==============

sda 
```

---

### Post by coffeecat on 2011-01-20
Well, that's very curious - no sda when using the CD. :? The first hard drive sometimes changes from sda to sdb when you use a live USB, which is why I asked the question.

Whatever, try the commands I posted with sdb. If that doesn't work, try theozzlives' suggestion with sda - your Ubuntu partition would be sda8. And if neither work, post back and we'll see what we can do. :)

---

### Post by sumitk on 2011-01-20
Yeaah It worked.... I am in my original Ubuntu now. Ah feeling better  now.:D thanks !!

I don't understand one part of your reply though - you said Ubuntu was in sdb9 but after fedora installation it became sdb8 right? But I initially installed Ubuntu in sdb8 only. Then I partitioned the other free sapce and installed fedora on sdb9. Is there some problem?

Let me reboot and see if fedora is booting up correctly - which I am little less bothered now :)

> **coffeecat said:**
> Well, that's very curious - no sda when using the CD. :? The first hard drive sometimes changes from sda to sdb when you use a live USB, which is why I asked the question.


I have the same question since the day I bought my laptop. No sda.? But then I forgot, if it would ever come up.

---

### Post by sumitk on 2011-01-20
Yeaah It worked.... I am in my original Ubuntu now. Ah feeling better  now.:grin: thanks !!

I don't understand one part of your reply though - you said Ubuntu was  in sdb9 but after fedora installation it became sdb8 right? But I  initially installed Ubuntu in sdb8 only. Then I partitioned the other  free sapce and installed fedora on sdb9. Is there some problem?

Let me reboot and see if fedora is booting up correctly - which I am little less bothered now :)

> **coffeecat said:**
> Well, that's very curious - no sda when using the CD. :???: The first hard drive sometimes changes from sda to sdb when you use a live USB, which is why I asked the question.


I have the same question since the day I bought my laptop. No sda.? But then I forgot, if it would ever come up.

---

### Post by coffeecat on 2011-01-20
> **sumitk said:**
> Yeaah It worked.... I am in my original Ubuntu now. Ah feeling better  now.:grin: thanks !!

Excellent. I'm glad it worked.

> **sumitk said:**
>  I don't understand one part of your reply though - you said Ubuntu was  in sdb9 but after fedora installation it became sdb8 right? But I  initially installed Ubuntu in sdb8 only. Then I partitioned the other  free sapce and installed fedora on sdb9. Is there some problem?

This from the Ubuntu /etc/fstab file in your bootscript output:

```
# / was on /dev/sdb9 during installation
UUID=290fbd47-ec06-4541-bc5d-532266a1725b /               ext4    errors=remount-ro 0
```When you installed Ubuntu that partition was numbered sdb9. Don't worry too much about it though. When you create logical partitions (anything numbered 5 upwards) in an extended partition, they sometimes renumber themselves, particularly if you delete one first. You simply need to know this can happen. Such knowledge can avoid hair loss! :)

> **sumitk said:**
> I have the same question since the day I bought my laptop. No sda.? But then I forgot, if it would ever come up.

It could be a quirk of your BIOS. Perhaps you have a card reader that is designated sda. If you have, try putting a card in it and then run 'sudo fdisk -lu' from a terminal. That will tell you if this is so.

By the way, if you're new to Fedora, you might find this link useful:

[http://www.mjmwired.net/resources/](http://www.mjmwired.net/resources/)

It contains a lot of useful stuff - repositories for restricted apps, proprietary video drivers, how to set up sudo, etc.

Good luck!

---

### Post by sumitk on 2011-01-20
> **coffeecat said:**
> Well, that's very curious - no sda when using the CD. :? The first hard drive sometimes changes from sda to sdb when you use a live USB, which is why I asked the question.


I am now having two very weird problems:

1. The grub is taking more time to come up after the computer starts. & my booting time for Ubuntu has increased to noticeable time now. I feel that it didn't used to take this much time. May be my feeling is wrong, i donno but the grub is definitely taking time t load.

More imp
2. I went to fedora and restarted it but this time I kept my USB drive connected while rebooting. Now the grub wont come. It is showing the grub config > prompt. I thought it was due to fedora but when I disconnected my USB the grub loaded fine.

---

### Post by coffeecat on 2011-01-20
In case you missed my post #13, we posted nearly simultaneously.

> **sumitk said:**
> I am now having two very weird problems:

1. The grub is taking more time to come up after the computer starts. & my booting time for Ubuntu has increased to noticeable time now. I feel that it didn't used to take this much time. May be my feeling is wrong, i donno but the grub is definitely taking time t load.

The re-install of grub wouldn't have caused this. I don't know why this should be.

> **sumitk said:**
>  More imp
2. I went to fedora and restarted it but this time I kept my USB drive connected while rebooting. Now the grub wont come. It is showing the grub config > prompt. I thought it was due to fedora but when I disconnected my USB the grub loaded fine.

Two possibilities. Either the USB drive is causing the sda/sdb/sdc designations to change around, confusing things. Or you have the BIOS configured to boot from a USB device first. Either way, don't have a USB drive plugged in when you boot up. That's a good practice anyway - I've been caught out many times by this.

---

### Post by sumitk on 2011-01-20
Thanks a lot coffeecat... really appreciate it man!!

> **coffeecat said:**
> 
It could be a quirk of your BIOS. Perhaps you have a card reader that is designated sda. If you have, try putting a card in it and then run 'sudo fdisk -lu' from a terminal. That will tell you if this is so.

I am gonna try that soon. I think I need to see what happens when I keep the USB intact while booting as now when I connect after booting, it is being recognised as sdc. I also wanna try more on grub.

Anyway thanks a lot for your time and help !! Told ya ... gr8 forum !!:)

---

