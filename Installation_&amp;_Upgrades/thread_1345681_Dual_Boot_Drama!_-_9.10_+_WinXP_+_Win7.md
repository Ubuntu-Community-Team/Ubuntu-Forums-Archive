---
title: "Dual Boot Drama! - 9.10 + WinXP + Win7"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by woofire on 2009-12-04
I just received a new HP laptop at work and thankfully it came with XP (not vista) installed and just needed some cleaning.  (Saves a Vol. Lic.)  I then like normal decided I would dual boot and install the latest ubuntu, so 9.10 is what I went with.  Everything worked great!

Until I find out we have an MSDN copy of Win 7 and figured why not add that too!  After doing so I lost my ability to boot to 9.10 and only had options to boot for Win XP and Win 7.

I tried to fix it by following [this tut]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

That seemed to work at first then I realized I added grub to sda instead of sda2 where my 9.10 partition is...  As a result I now can boot to 9.10 and XP but not Win 7...

I've searched around and learned a little about BCEDIT for Win7 but I'm not sure how to use it or if it will even fix the issue...  If I could solve this through my 9.10 install id prefer it!  :-)

---

### Post by darkod on 2009-12-04
You were supposed to install grub2 to /dev/sda, not to a partition (/dev/sda2). The only thing that link is for the older version, grub1, for ubuntu 9.04 or before.

I am not sure what is the best approach in this type of situation because the standard install process would be xp-win7-ubuntu. That's not because of ubuntu, but because windows has decided to combine the boot process for more than one version of windows.

From within ubuntu, download the script in my signature, move it to desktop for example and execute it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. Copy the content of that file here and put CODE tags around it (with the content selected hit the # button in the toolbar above). That makes it easier to read.

I think you should be able to boot both xp and win7 directly from grub2. If that fails, there are other options.

---

### Post by presence1960 on 2009-12-04
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

**sorry darkod, I did not see you already asked to run the boot info script.**

---

### Post by woofire on 2009-12-04
Here you go, thanks in advance for even trying to help!

Out of curiosity, I noticed it says 9.4 kernel at the end...  Is that from the original install and the upgrade or from repairing grub with a 9.4 live CD?


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95aa95aa

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   195,318,269   195,318,207   7 HPFS/NTFS
/dev/sda2         195,318,270   390,636,539   195,318,270  83 Linux
/dev/sda3         390,636,540   394,540,334     3,903,795   5 Extended
/dev/sda5         390,636,603   394,540,334     3,903,732  82 Linux swap / Solaris
/dev/sda4         394,541,056   599,341,055   204,800,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0C76C8CF2E0D6BAD" TYPE="ntfs" 
/dev/sda2: UUID="1ec3bcaf-2362-40f2-a3c3-37f01cc264e2" TYPE="ext3" 
/dev/sda4: UUID="4486B85F86B85362" TYPE="ntfs" 
/dev/sda5: UUID="ef539fda-4c9d-4ff8-b5e3-16e12c64acd8" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/drudwn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=drudwn)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sda2/boot/grub/menu.lst: ===========================

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
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=1ec3bcaf-2362-40f2-a3c3-37f01cc264e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1ec3bcaf-2362-40f2-a3c3-37f01cc264e2

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
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        1ec3bcaf-2362-40f2-a3c3-37f01cc264e2
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=1ec3bcaf-2362-40f2-a3c3-37f01cc264e2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        1ec3bcaf-2362-40f2-a3c3-37f01cc264e2
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=1ec3bcaf-2362-40f2-a3c3-37f01cc264e2 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        1ec3bcaf-2362-40f2-a3c3-37f01cc264e2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1ec3bcaf-2362-40f2-a3c3-37f01cc264e2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        1ec3bcaf-2362-40f2-a3c3-37f01cc264e2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1ec3bcaf-2362-40f2-a3c3-37f01cc264e2 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        1ec3bcaf-2362-40f2-a3c3-37f01cc264e2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=1ec3bcaf-2362-40f2-a3c3-37f01cc264e2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ef539fda-4c9d-4ff8-b5e3-16e12c64acd8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 163.2GB: boot/grub/menu.lst
 163.2GB: boot/grub/stage2
 163.2GB: boot/initrd.img-2.6.28-11-generic
 163.2GB: boot/initrd.img-2.6.28-16-generic
 163.3GB: boot/vmlinuz-2.6.28-11-generic
 163.3GB: boot/vmlinuz-2.6.28-16-generic
 163.2GB: initrd.img
 163.2GB: initrd.img.old
 163.3GB: vmlinuz
 163.3GB: vmlinuz.old

```

---

### Post by darkod on 2009-12-04
OK. In terminal run:
sudo gedit /boot/grub/menu.lst

It should open your menu.lst file (that's .Lst, not .1st)

After the Windows XP entry add the following for 7

title        Microsoft Windows 7
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader /bootmgr

Save and close the file. Reboot and check if the entry works.

---

### Post by woofire on 2009-12-04
Now that entry shows up in grub however when i select to boot to it I get;

Error 17: Cannot mount selected partition

Press any key to continue...

---

### Post by presence1960 on 2009-12-04
You do not have 9.10 installed, see this:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95aa95aa

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   195,318,269   195,318,207   7 HPFS/NTFS
/dev/sda2         195,318,270   390,636,539   195,318,270  83 Linux
/dev/sda3         390,636,540   394,540,334     3,903,795   5 Extended
/dev/sda5         390,636,603   394,540,334     3,903,732  82 Linux swap / Solaris
/dev/sda4         394,541,056   599,341,055   204,800,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0C76C8CF2E0D6BAD" TYPE="ntfs" 
/dev/sda2: UUID="1ec3bcaf-2362-40f2-a3c3-37f01cc264e2" TYPE="ext3" 
/dev/sda4: UUID="4486B85F86B85362" TYPE="ntfs" 
/dev/sda5: UUID="ef539fda-4c9d-4ff8-b5e3-16e12c64acd8" TYPE="swap" 
```

sda1 is XP
sda4 is windows 7
sda2 is 9.04

When you choose XP from the grub menu you should get the windows bootloader which offers you the choice of XP or  Windows 7. You should get a choice because your Win 7 bootloader has been merged with XP's:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr [COLOR="Red"]/Boot/BCD[/COLOR] /ntldr /ntdetect.com
``` Note the red- they are from Win 7

 If not boot into 9.04 and run in terminal ```
gksu gedit /boot/grub/menu.lst
``` That is a lowecase L in .lst

scroll down to your XP entry and skip a line & add this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title           Microsoft Windows 7
rootnoverify    (hd0,3)
chainloader     +1
```

Click Save on top toolbar, close file. reboot & try Win 7 from GRUB menu

---

### Post by presence1960 on 2009-12-04
BTW GRUB 2 is not installed and GRUB 0.97 is on the MBR and looks to your 9.04 partition to menu.lst.

This why I always ask for the script to be run when people ask for help. Whether or not on purpose the setup described by most people is usually different than what is actually on the machine.

---

