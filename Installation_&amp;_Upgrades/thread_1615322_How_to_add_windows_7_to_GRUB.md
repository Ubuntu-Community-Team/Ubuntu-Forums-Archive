---
title: "How to add windows 7 to GRUB"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by janglebyte on 2010-11-06
so here's how it went, first i partitioned my hdd into two partitions  and then i installed windows 7 on the second partition all went fine so i decided to install Linux on the first partition installation went fine but after that GRUB could not boot windows 7.  I would really appreciate some help. ```
Disk /dev/sda: 203.9 GB, 203928109056 bytes 255 heads, 63 sectors/track, 24792 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x05d67c23     Device Boot      Start         End      Blocks   Id  System /dev/sda1               1       12748   102398278+   5  Extended /dev/sda2           12749       18770    48371715    7  HPFS/NTFS /dev/sda5               1       12224    98189217   83  Linux /dev/sda6           12225       12748     4208998+  82  Linux swap / Solaris
```

---

### Post by Quackers on 2010-11-07
Welcome to UF.
It may have worked better if you had installed W7 first then installed Ubuntu.
When you start your pc does a grub menu appear with a choice of operating systems or does an OS just boot up without getting any choice?

---

### Post by garvinrick4 on 2010-11-07
Put in live cd (install cd for ubuntu) choose Try Ubuntu and when it  boots start internet and go to this website and download the Script to  DESKTOP and then run the code below in a terminal. Applications to  Accessories to Terminal:
website to download:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
copy and paste this below into terminal.
 	Code:
 	```
 sudo bash ~/Desktop/boot_info_script*.sh
``` 
Now there will be a file called RESULTS on your desktop:
copy and paste it to this thread. After you paste it here ir you highlight
the whole thing (it is long) and hit the # in upper right of message box you
will put it in a nice box for me to read it in. This whole thing takes about 
a minute to do.

---

### Post by janglebyte on 2010-11-07
thanks for helping me out here are the results. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05d67c23

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   204,796,619   204,796,557   5 Extended
/dev/sda5                 126   196,378,559   196,378,434  83 Linux
/dev/sda6         196,378,623   204,796,619     8,417,997  82 Linux swap / Solaris
/dev/sda2         204,796,620   301,540,049    96,743,430   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        D4A8E3C8A8E3A768                       ntfs                                     
/dev/sda5        9fb6f475-072b-4a6e-b44c-7a7efa527177   ext3                                     
/dev/sda6        89a548d5-4f19-4f1f-85b2-88c247b276e3   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9fb6f475-072b-4a6e-b44c-7a7efa527177 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9fb6f475-072b-4a6e-b44c-7a7efa527177

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

splashimage=9fb6f475-072b-4a6e-b44c-7a7efa527177/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.34
uuid        9fb6f475-072b-4a6e-b44c-7a7efa527177
kernel        /boot/vmlinuz-2.6.34 root=UUID=9fb6f475-072b-4a6e-b44c-7a7efa527177 ro vga=0x317 
initrd        /boot/initrd.img-2.6.34
quiet

title        Ubuntu 8.10, kernel 2.6.34 (recovery mode)
uuid        9fb6f475-072b-4a6e-b44c-7a7efa527177
kernel        /boot/vmlinuz-2.6.34 root=UUID=9fb6f475-072b-4a6e-b44c-7a7efa527177 ro  single
initrd        /boot/initrd.img-2.6.34

title        Ubuntu 8.10, memtest86+
uuid        9fb6f475-072b-4a6e-b44c-7a7efa527177
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9fb6f475-072b-4a6e-b44c-7a7efa527177 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=89a548d5-4f19-4f1f-85b2-88c247b276e3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  57.1GB: boot/grub/menu.lst
  57.1GB: boot/grub/stage2
  57.0GB: boot/initrd.img-2.6.34
  57.1GB: boot/vmlinuz-2.6.34
  57.0GB: initrd.img
  57.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by garvinrick4 on 2010-11-07
I see there are no Primary partitions for Windows to exist in. I see backtrack linux in sda5
and grub legacy installed. If you want to try to boot windows 7 I will try but it really likes to be in a Primary not a logical partition.
Put in live Cd and open a terminal:
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```will say errors but ignore we only need mbr

You should really start over and put 7 in sda1 then make sda2 an extended and that would
make sda5 logical for linux which linux is happy in and Windows is happy in. Just make the partitions they will number themselves. Primary for windows extended then logical for linux.
###I am sorry sda2 is at end of chain and is Primary just not in order. lilo should work, should boot windows.

---

### Post by oldfred on 2010-11-07
Win7 main install is in a primary - sda2. Did you have XP or another windows installed in sda1? Windows combines its boot into the first install that has the boot flag (active partition). You are missing two essential boot files for win7 but can repair the boot in sda2.

First you will need a boot flag on sda2. You can use gparted, manage flags and set boot flag.

You will need windows repair CD and run the full set of windows repairs on sda2.

Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by v1ad on 2010-11-07
have you tried booting into linux and doing 'sudo update-grub' ? or its also could be 'sudo update-grub2'

worked 4 me. if i missed something my bad.

---

