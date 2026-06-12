---
title: "Re-install grub isn't possible"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by TopGear on 2010-01-06
I wanted to replace my grub2 with the grub legacy. But I can't!

I followed this howto:
```

**Uninstalling GRUB 2**

  
**Reverting to GRUB Legacy**

 If a user chooses to return to GRUB legacy (0.97), these steps will remove GRUB 2 and install GRUB.  
The command line produces a cleaner uninstall and reinstallation. While adding and removing the packages can be accomplished with Synaptic, certain steps must be accomplished in a terminal. 

[LIST=1]
[*]Open a terminal: Applications, Accessories, Terminal.
[*]Make backup copies of the main GRUB 2 folders & files. (Optional)
[LIST]
[*]sudo cp /etc/default/grub /etc/default/grub.old
[*]sudo cp -R /etc/grub.d /etc/grub.d.old
[*]sudo cp -R /boot/grub /boot/grub.old
[/LIST]
 
[*]Remove GRUB 2
[LIST]
[*]sudo apt-get purge grub2 grub-pc
[*][IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=important.png[/IMG] The system will be unbootable until another bootloader is installed.
[*]Once the packages are removed, many files will still remain in '/boot/grub'
[/LIST]
 
[*]Install GRUB 0.97
[LIST]
[*]sudo apt-get install grub
[/LIST]
 
[*]With *grub* installed, the user must still create the *menu.lst* and *stage1/stage2* files by running the following two commands.
[LIST=1]
[*]sudo update-grub
[LIST]
[*]Generates *menu.lst*
[LIST]
[*]Tab to "Yes" when prompted.
[/LIST]
 
[/LIST]
 
[*]sudo grub-install /dev/sdX
[LIST]
[*]Choose the correct device (sda, sdb, etc), normally the one on which Ubuntu is installed.
[*]Creates the *stage1* & *stage2* files in */boot/grub* and writes to the MBR.
[/LIST]
 
[/LIST]
 
[*]Reboot
[/LIST]
[IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=important.png[/IMG]If the user receives an "Unrecognized device string Error 11" message on rebooting see the [Resolving an "Unrecognized Device String" (Error 11)]("https://help.ubuntu.com/community/Grub2#Resolving%20an%20%22Unrecognized%20Device%20String%22%20%28Error%2011%29") section for instructions on how to edit the menu and make the system bootable.
```Well, I did that..... Still grub2! I know now that I can't get rid of "grub-common". When I want to remove it, grub legacy has to be deleted to! And when I want to install grub legacy, i've got to install grub-common! Can somebody help me?

---

### Post by presence1960 on 2010-01-06
[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

Try that how to by kansasnoob. I know it works because I used it on a friend's machine.

---

### Post by TopGear on 2010-01-06
[LEFT]THNX! But I've still a few questions left!

> Since /dev/sda is where I'd want grub to be installed, I'd run this command:
sudo grub-install /dev/sda
*Note: If you're at all unsure about where to install grub then ask for help here on the forums! Better to be sure of what you're doing than to play the trial and error game!*
Is this where I want to install the Grub (MBR)?


> [LEFT]Then:
[/LEFT]
find /boot/grub/stage1 [LEFT]That will provide an output like (hd0,2) which you'll need to use in the next step:
[/LEFT]

Does this show where the Ubuntu installation is?
[/LEFT]

---

### Post by kansasnoob on 2010-01-06
If you have a fairly simple installation like just a dual-boot post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

If it's a more complex setup then post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Also I'm just curious why you're reverting to legacy grub?

---

### Post by TopGear on 2010-01-06
Becouse I just don't like that Grub2. I want to wait untill 10.04. Then I would like grub2, but not now.
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 483903 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x0006d00b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Schijf /dev/sdb: 750.2 GB, 750156374016 bytes
255 koppen, 63 sectoren/spoor, 91201 cilinders, totaal 1465149168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x0006a04e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   720,708,029   720,707,967  83 Linux
/dev/sdb2         720,708,030 1,441,399,994   720,691,965   7 HPFS/NTFS
/dev/sdb3       1,441,399,995 1,465,144,064    23,744,070   f W95 Ext d (LBA)
/dev/sdb5       1,441,400,058 1,465,144,064    23,744,007  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="40AC0EEBAC0EDAF4" TYPE="ntfs" 
sdb1: UUID="ccefa12d-ceb5-4051-ae6a-3e1d84da67bc" TYPE="ext4" 
sdb2: UUID="6D0C119E76831EBF" LABEL="Downloads" TYPE="ntfs" 
sdb5: UUID="20a6d6f5-2548-4985-89d6-a9f100a36abe" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/peter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=peter)
/dev/sda1 on /media/40AC0EEBAC0EDAF4 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2 on /media/Downloads type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=peter)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        ccefa12d-ceb5-4051-ae6a-3e1d84da67bc
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        ccefa12d-ceb5-4051-ae6a-3e1d84da67bc
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        ccefa12d-ceb5-4051-ae6a-3e1d84da67bc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        ccefa12d-ceb5-4051-ae6a-3e1d84da67bc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
uuid        ccefa12d-ceb5-4051-ae6a-3e1d84da67bc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set ccefa12d-ceb5-4051-ae6a-3e1d84da67bc
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
set locale_dir=/boot/grub/locale
set lang=nl
insmod gettext 
set timeout=100
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu GNU/Linux, with Linux 2.6.31-16-generic" --class linux {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set ccefa12d-ceb5-4051-ae6a-3e1d84da67bc
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc ro  splash quiet
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu GNU/Linux, with Linux 2.6.31-16-generic (recovery mode)" --class linux {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set ccefa12d-ceb5-4051-ae6a-3e1d84da67bc
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc ro single  splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu GNU/Linux, with Linux 2.6.31-14-generic" --class linux {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set ccefa12d-ceb5-4051-ae6a-3e1d84da67bc
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc ro  splash quiet
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu GNU/Linux, with Linux 2.6.31-14-generic (recovery mode)" --class linux {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set ccefa12d-ceb5-4051-ae6a-3e1d84da67bc
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc ro single  splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 40ac0eebac0edaf4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
. /boot/grub/themes/sora/theme.cfg
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=20a6d6f5-2548-4985-89d6-a9f100a36abe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.olden

```

---

### Post by kansasnoob on 2010-01-06
Just a couple more questions. I see that grub2 was installed to the mbr of both sda and sdb:

> => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=ccefa12d-ceb5-4051-ae6a-3e1d84da67bc)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.

It's been my experience with grub2 that it always wants to install to sda, so did you have to manually install grub2 to sdb to get the machine to boot after installing Ubuntu?

Maybe following a guide something like this:

[http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/](http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/)

The thing is I just can't be 100% sure whether to install grub to sda or sdb. If we get it wrong we'll have to fix it with a Live CD. So your previous knowledge of the machine would be helpful.

It's not all that hard to fix but I'd rather get it right the first time :)

My other question is, you know you'll have to manually edit the grub menu.lst after reverting, that is you'll have to add Win 7 to the menu.lst, probably unhide the menu, change the timeout, etc.

Do you know how to do that or do you need assistance with that? I don't mind helping, but again I'd just like to get it right the first time.

---

### Post by TopGear on 2010-01-06
Yes, I know how to:
```
title        Windows 7
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

I allways install my grub on sdb, that's where ubuntu is installed.

---

### Post by darkod on 2010-01-06
sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  [COLOR=Red]Grub 0.97 is installed in the boot sector of sdb1[/COLOR] and 
                       looks at sector 483903 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

You got into a bit of a mess there. You have grub2 on both MBR of /dev/sda and /dev/sdb, but you also have grub1 on the partition /dev/sdb1. I'm not getting into the decision to replace grub2 with grub1, that's your choice. But by accident or on purpose, you seem to have grub1 installed on a partition and not the MBR. This way you would have to chainload and hop from grub2 on the MBR to grub1 on the sdb1 and boot ubuntu.
When installing any version of grub, always make sure you install on MBR and not partition. For example /dev/sdb and not /dev/sdb1.

---

### Post by TopGear on 2010-01-06
I know that now......

But how can I delete the grub's on the wrong partition?

---

### Post by rmhartman on 2010-01-06
> **TopGear said:**
> Yes, I know how to:
```
title        Windows 7
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

I allways install my grub on sdb, that's where ubuntu is installed.

Unfortunately, in oder to do that you have to go into "advanced" options when the installer is displaying the summary.

The first time I put Ubunto onto a USB drive, the installer wrote the boot loader onto my hard disc and totally messed me up.

I would really, _really_, appreciate it the installer would by default put grub onto the same device it is installing the OS to.  Is this too much to ask?

---

### Post by kansasnoob on 2010-01-06
> **TopGear said:**
> Yes, I know how to:
```
title        Windows 7
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

I allways install my grub on sdb, that's where ubuntu is installed.

So then referring to this:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

You would just:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub-pc grub-common
```

```
sudo apt-get install grub
```

```
sudo update-grub
```

Say yes to making a menu.lst.

```
sudo grub-install /dev/sdb
```

```
sudo grub
```

And since Ubuntu is on sdb1:

```
root (hd1,0)
```

```
setup (hd1)
```

You should see:

> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 

Then:

```
quit
```

That should be it!

---

### Post by kansasnoob on 2010-01-06
> **TopGear said:**
> I know that now......

But how can I delete the grub's on the wrong partition?

I don't think you'll have to worry about it. If you ever did want to restore the Windows MBR you can just use an Ubuntu Live CD:

[http://ubuntuforums.org/showpost.php?p=8538352&postcount=173](http://ubuntuforums.org/showpost.php?p=8538352&postcount=173)

Of course the X in sdX is in your case an a as in sda.

I wouldn't mess with it as long as legacy grub gets you booting.

BTW if you ever use Lilo to replace an mbr like that from an installed working Ubuntu be sure to "sudo apt-get --purge remove lilo" when you're done so you don't at some point hose your grub!

---

### Post by darkod on 2010-01-06
> **kansasnoob said:**
> I don't think you'll have to worry about it. If you ever did want to restore the Windows MBR you can just use an Ubuntu Live CD:

[http://ubuntuforums.org/showpost.php?p=8538352&postcount=173](http://ubuntuforums.org/showpost.php?p=8538352&postcount=173)

Of course the X in sdX is in your case an a as in sda.

I wouldn't mess with it as long as legacy grub gets you booting.

BTW if you ever use Lilo to replace an mbr like that from an installed working Ubuntu be sure to "sudo apt-get --purge remove lilo" when you're done so you don't at some point hose your grub!

I believe the OP was asking how to remove the grub1 from /dev/sdb1 that is there by mistake. I don't know how to do that also, so I can't really help. :)
He has grub1 on the partition /dev/sdb1, in addition to the two grub2 on the MBR of both drives.
Even if he successfully installs grub1 on /dev/sdb, won't the grub1 on /dev/sdb1 get into way?

---

### Post by darkod on 2010-01-06
> **rmhartman said:**
> Unfortunately, in oder to do that you have to go into "advanced" options when the installer is displaying the summary.

The first time I put Ubunto onto a USB drive, the installer wrote the boot loader onto my hard disc and totally messed me up.

I would really, _really_, appreciate it the installer would by default put grub onto the same device it is installing the OS to.  Is this too much to ask?

If you think about it, this behavior has some logic in it. Windows does the same, it installs the bootloader on the drive that is first in the boot order. If you had set the drive where you want to install ubuntu as first in boot order BEFORE beginning the install process, grub should by default go on that drive.
On the other hand, if you have a situation where drive X is first in boot order, and you are installing an OS to drive Y. It needs the bootloader to boot and it can see that drive X is first in boot order so putting the bootloader on that drive makes some sense.
Anyway, with multiple drives it's always wise to check advanced options and make sure the bootloader goes where you want it. Remember, the machine can't always know what you want. :)

---

### Post by rmhartman on 2010-01-06
> **darkod said:**
> If you think about it, this behavior has some logic in it. Windows does the same, it installs the bootloader on the drive that is first in the boot order. If you had set the drive where you want to install ubuntu as first in boot order BEFORE beginning the install process, grub should by default go on that drive.
On the other hand, if you have a situation where drive X is first in boot order, and you are installing an OS to drive Y. It needs the bootloader to boot and it can see that drive X is first in boot order so putting the bootloader on that drive makes some sense.
Anyway, with multiple drives it's always wise to check advanced options and make sure the bootloader goes where you want it. Remember, the machine can't always know what you want. :)

My boot order in the BIOS is "removeable devices" (i.e. USB drives), CD-ROM, then hard disc ... so your explanation still does not hold water.  I am installing on the USB drive.  If grub is put on the hard disc it can a) mess things up for what is already there, and b) may not have the USB drive plugged when it is time to boot to linux.  I can think of little more useless than the hard disc mbr pointing to an OS on a removable device.

Strictly speaking, I needn't have grub at all -- if the only OS on my thumb drive is Ubuntu (although I am hoping to get Puppy linux working on a different partition) because if the thumb drive is in it will boot to the installed OS (Ubunto).

On the other hand ... overwriting the MBR of the hard disc with grup while installing an OS to the USB drive WITHOUT warning the user of what is happening and warning them that it could render their computer unbootable is ... a Bad Thing (tm).

---

### Post by kansasnoob on 2010-01-06
> **darkod said:**
> I believe the OP was asking how to remove the grub1 from /dev/sdb1 that is there by mistake. I don't know how to do that also, so I can't really help. :)
He has grub1 on the partition /dev/sdb1, in addition to the two grub2 on the MBR of both drives.
Even if he successfully installs grub1 on /dev/sdb, won't the grub1 on /dev/sdb1 get into way?

I think when legacy grub runs this check:

> Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded

It will decide to ignore any old clutter, we'll see. I did once have to run through a whole install process to get things straightened out, you just use the Manual (advanced) install option, select the proper partitions, and be absolutely certain **[COLOR="Red"]NOT[/COLOR]** to click on format.

---

### Post by darkod on 2010-01-06
> **rmhartman said:**
> My boot order in the BIOS is "removeable devices" (i.e. USB drives), CD-ROM, then hard disc ... so your explanation still does not hold water.  I am installing on the USB drive.  If grub is put on the hard disc it can a) mess things up for what is already there, and b) may not have the USB drive plugged when it is time to boot to linux.  I can think of little more useless than the hard disc mbr pointing to an OS on a removable device.

Strictly speaking, I needn't have grub at all -- if the only OS on my thumb drive is Ubuntu (although I am hoping to get Puppy linux working on a different partition) because if the thumb drive is in it will boot to the installed OS (Ubunto).

On the other hand ... overwriting the MBR of the hard disc with grup while installing an OS to the USB drive WITHOUT warning the user of what is happening and warning them that it could render their computer unbootable is ... a Bad Thing (tm).

I was talking about boot order of internal hdds. I didn't notice external drive mentioned in your post, maybe I missed it. I'm not 100% sure but I think the internal hdd always gets priority over external for bootloader installation, regardless of the boot device settings (USB, CD, HDD).
Of course, you have the right to be annoyed how ubuntu does things. Personally, I would always check bootloader destination with multiple drives, regardless whether internal/internal, or internal/external combination. Why let the machine make the choice? Likewise, I always create partitions manually to make sure I get what I want.

---

### Post by kansasnoob on 2010-01-06
> Why let the machine make the choice? Likewise, I always create partitions manually to make sure I get what I want.

+ a gazillion!

I hardly even trust myself, I'm surely not going to trust something automated with this mess:

```
Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  22.0GB  22.0GB  primary   ntfs            boot
 3      22.0GB  31.0GB  8933MB  primary   ext3
 2      31.0GB  160GB   129GB   extended
 5      31.0GB  39.5GB  8521MB  logical   ext3
 6      39.5GB  76.4GB  36.9GB  logical   ext3
 7      76.4GB  84.7GB  8365MB  logical   ext3
 8      84.7GB  100GB   15.7GB  logical   ext3
13      100GB   107GB   6835MB  logical   ext3
14      107GB   122GB   15.1GB  logical   ext3
 9      122GB   124GB   1258MB  logical   linux-swap(v1)
10      124GB   141GB   17.0GB  logical   ext3
11      141GB   147GB   6309MB  logical   ext3
12      147GB   160GB   13.1GB  logical   ext3

```

---

### Post by rmhartman on 2010-01-06
> **darkod said:**
> I was talking about boot order of internal hdds. I didn't notice external drive mentioned in your post, maybe I missed it. I'm not 100% sure but I think the internal hdd always gets priority over external for bootloader installation, regardless of the boot device settings (USB, CD, HDD).
Of course, you have the right to be annoyed how ubuntu does things. Personally, I would always check bootloader destination with multiple drives, regardless whether internal/internal, or internal/external combination. Why let the machine make the choice? Likewise, I always create partitions manually to make sure I get what I want.

Unfortunately, in the summary presented just before you install, I don't think it even mentions that it is about to rewrite your mbr unless you go into "advance" and see that install grub is checked, and where.

Perhaps I missed it though.

---

