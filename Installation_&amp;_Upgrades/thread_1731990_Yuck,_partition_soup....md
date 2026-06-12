---
title: "Yuck, partition soup..."
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by doubi on 2011-04-17
Hi all,

I'd like some advice on how to change my boot partition, the advantages / disadvantages of having a separate, small boot partition at the start of my drive, and on what risks I might have in removing a couple of partitions I have.
 
When I first got into Linux I was trying a bunch of different OS's, making partitions for them all over the place. After a horrible experience accidentally deleting most of my home dir the other day, I've decided the time has come to get my house in order backup-wise. Now also seems like a good time to get my partitions / boot stuff sorted out.

I've ended up with an NTFS partition with Windows XP, several ext3/4 ones with various Linices (some in an extended / logical partition), a small 512MB ext2 partition, which I think was meant to be a separate boot partition but hasn't been for a while, and bizarrely, two swap partitions.

Here's the most relevant output from the delightful [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) :

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 29141134 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     1,028,159     1,028,097  83 Linux
/dev/sda2           1,028,221   197,101,484   196,073,264   5 Extended
/dev/sda5           1,028,223    11,036,654    10,008,432  82 Linux swap / Solaris
/dev/sda6         179,735,283   195,013,034    15,277,752  83 Linux
/dev/sda7         195,013,098   197,101,484     2,088,387  82 Linux swap / Solaris
/dev/sda8          11,036,672   179,735,219   168,698,548  83 Linux
/dev/sda3         197,101,568   239,046,655    41,945,088  83 Linux
/dev/sda4    *    239,047,200   312,576,704    73,529,505   7 HPFS/NTFS

```One thing I really don't understand is that the Windows partition seems to be the boot partition. I can only imagine that it "redirects" to grub on another partition somehow, but I can't see anything in boot.ini that does this? :

```

================================ sda4/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```So my questions are:

[LIST=1]
[*]Is it safe to remove one of my two swap partitions, and if so should I enlarge the other one?
[*]Should I boot from a small boot partition to avoid this Windows-to-grub weirdness?
[*]What tools should I use for either of the above?
[/LIST]
My instant reason for wanting to do any of this is I simply wanted to change my grub boot order, and suddenly realised I didn't know on which of 5 or so partitions menu.lst was! I can see where it is now thanks to bootinfoscript, but this isn't a convenient state of affairs. Many thanks for your thoughts / advice.

---

### Post by Hedgehog1 on 2011-04-17
Might I request you post the entire script output, please?  This way we can tell which swap partition is being used, and if the '/boot' partition is really no longer used.

***The Hedge***

:KS

p.s. If you want to see a really crazy partition layout, ask Dutch70 to post his. :D

---

### Post by Dutch70 on 2011-04-17
Hahaa, you should see my boot info script ;)

1. Yes it's safe to remove one of your swap partitions. The one you keep should be equal to the size of your RAM, or a slightly larger for overflow if you want. [[COLOR="Red"]SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

2. I don't see any windows to grub weirdness on you computer. You have windows installed to sda4, which is a primary partition, so you're good. That's where the boot flag should be. I don't think Ubuntu even pays any attention to the boot flag.

If you want to change your partitioning scheme, *(or swap)* take a screenshot of gparted & attach it with the paper clip in the toolbar of your next post. I get a better idea with a visual of your hdd than from fdisk -l.

---

### Post by oldfred on 2011-04-17
Herman posted some good info on separate system partitions. You only need a separate /boot on a desktop if you have an older system that can only boot from the first 137GB. But even then you can have an entire system partition in the first 137GB.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

You /boot has menu.lst from grub legacy. But you have grub2 in the MBR and are booting sda6. I would expect the grub menu in sda6 then gives you the choice to boot your other installs.

---

### Post by doubi on 2011-04-18
Hi all,

Thanks for the feedback.

Here's the entire bootinfoscript output:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 29141134 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     1,028,159     1,028,097  83 Linux
/dev/sda2           1,028,221   197,101,484   196,073,264   5 Extended
/dev/sda5           1,028,223    11,036,654    10,008,432  82 Linux swap / Solaris
/dev/sda6         179,735,283   195,013,034    15,277,752  83 Linux
/dev/sda7         195,013,098   197,101,484     2,088,387  82 Linux swap / Solaris
/dev/sda8          11,036,672   179,735,219   168,698,548  83 Linux
/dev/sda3         197,101,568   239,046,655    41,945,088  83 Linux
/dev/sda4    *    239,047,200   312,576,704    73,529,505   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c5ba0046-157b-4ca9-a57a-506b6d0325ad   ext2                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        1618da5d-3469-4836-b824-ffb7d6ae5fbd   ext4                                     
/dev/sda4        F87022D170229702                       ntfs       xp                            
/dev/sda5        b0f0e160-6031-4daa-83e6-1cd8e42fa460   swap                                     
/dev/sda6        23be90ed-b6b6-4625-be7b-c59c1a11600a   ext4                                     
/dev/sda7        9c93e080-e6a3-4154-9163-a93002955b0e   swap                                     
/dev/sda8        301c903c-485f-409f-8ff8-b792cf0ec7c3   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /media/doub2             ext4       (rw)
/dev/sda4        /media/xp                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title        Microsoft Windows XP Home Edition
root        (hd0,3)
savedefault
makeactive
chainloader    +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title        Other operating systems:
# root

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
# kopt=root=UUID=44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26

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

title        Ubuntu Studio 8.10, kernel 2.6.27-7-generic
uuid        44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu Studio 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu Studio 8.10, memtest86+
uuid        44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Ubuntu 9.04
root        (hd0,5)
kernel        (hd0,0)/mint/vmlinuz-2.6.27-11-generic root=/dev/sda6 ro quiet splash
initrd        (hd0,0)/mint/initrd.img-2.6.27-11-generic
quiet

title        Ububtu Studio New, kernel 2.6.27-7-generic
root        (hd0,6)
kernel        (hd0,0)/studNew/vmlinuz-2.6.27-7-generic root=/dev/sda7 ro quiet splash
initrd        (hd0,0)/studNew/initrd.img-2.6.27-7-generic
quiet


============================= sda1/grub/menu.lst: =============================

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title        Microsoft Windows XP Home Edition
root        (hd0,3)
savedefault
makeactive
chainloader    +1

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title        Other operating systems:
# root

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
# kopt=root=UUID=44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26

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

title        Ubuntu Studio 8.10, kernel 2.6.27-7-generic
uuid        44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu Studio 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu Studio 8.10, memtest86+
uuid        44a3ba8b-8ce7-4cd0-8b05-6dfc91ec2b26
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Ubuntu 9.04
root        (hd0,5)
kernel        (hd0,0)/mint/vmlinuz-2.6.27-11-generic root=/dev/sda6 ro quiet splash
initrd        (hd0,0)/mint/initrd.img-2.6.27-11-generic
quiet

title        Ububtu Studio New, kernel 2.6.27-7-generic
root        (hd0,6)
kernel        (hd0,0)/studNew/vmlinuz-2.6.27-7-generic root=/dev/sda7 ro quiet splash
initrd        (hd0,0)/studNew/initrd.img-2.6.27-7-generic
quiet


=================== sda1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/menu.lst
    .2GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.27-7-generic
    .0GB: boot/vmlinuz-2.6.27-7-generic
    .2GB: grub/menu.lst
    .2GB: grub/stage2
    .0GB: initrd.img-2.6.27-7-generic
    .0GB: vmlinuz-2.6.27-7-generic

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.04 LTS (10.04) (on /dev/sda3)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1618da5d-3469-4836-b824-ffb7d6ae5fbd
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda3
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set f87022d170229702
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro quiet splash
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b0f0e160-6031-4daa-83e6-1cd8e42fa460 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=9c93e080-e6a3-4154-9163-a93002955b0e none            swap    sw              0       0
/dev/sda4       /media/xp       ntfs    defaults        0       2
/dev/sda8    /media/doubuntu1    ext4    defaults    0    2


=================== sda6: Location of files loaded by Grub: ===================


  92.4GB: boot/grub/core.img
  92.4GB: boot/grub/grub.cfg
  95.8GB: boot/initrd.img-2.6.32-21-generic
  95.9GB: boot/initrd.img-2.6.32-22-generic
  96.1GB: boot/initrd.img-2.6.32-23-generic
  99.0GB: boot/initrd.img-2.6.32-30-generic
  95.7GB: boot/vmlinuz-2.6.32-21-generic
  92.3GB: boot/vmlinuz-2.6.32-22-generic
  95.5GB: boot/vmlinuz-2.6.32-23-generic
  97.6GB: boot/vmlinuz-2.6.32-30-generic
  99.0GB: initrd.img
  96.1GB: initrd.img.old
  97.6GB: vmlinuz
  95.5GB: vmlinuz.old

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 301c903c-485f-409f-8ff8-b792cf0ec7c3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda3)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1c2fb8ce-a721-40d8-acc1-78beb25562c1
    linux /boot/vmlinuz-2.6.27-7-generic root=UUID=1c2fb8ce-a721-40d8-acc1-78beb25562c1 ro quiet splash
    initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda3)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1c2fb8ce-a721-40d8-acc1-78beb25562c1
    linux /boot/vmlinuz-2.6.27-7-generic root=UUID=1c2fb8ce-a721-40d8-acc1-78beb25562c1 ro single
    initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda3)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1c2fb8ce-a721-40d8-acc1-78beb25562c1
    linux /boot/memtest86+.bin 
}
menuentry "Microsoft Windows XP Professional (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set f87022d170229702
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 23be90ed-b6b6-4625-be7b-c59c1a11600a
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=23be90ed-b6b6-4625-be7b-c59c1a11600a ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=301c903c-485f-409f-8ff8-b792cf0ec7c3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b0f0e160-6031-4daa-83e6-1cd8e42fa460 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=9c93e080-e6a3-4154-9163-a93002955b0e none            swap    sw              0       0
/dev/sda4    /media/xp    ntfs    defaults    0    2
/dev/sda6    /media/doub2    ext4    defaults    0    2

=================== sda8: Location of files loaded by Grub: ===================


  12.5GB: boot/grub/core.img
  18.2GB: boot/grub/grub.cfg
  12.6GB: boot/initrd.img-2.6.32-21-generic
  12.6GB: boot/initrd.img-2.6.32-23-generic
  14.0GB: boot/initrd.img-2.6.32-24-generic
  25.4GB: boot/initrd.img-2.6.32-25-generic
  30.1GB: boot/initrd.img-2.6.32-26-generic
  13.1GB: boot/initrd.img-2.6.32-27-generic
  18.4GB: boot/initrd.img-2.6.32-28-generic
   9.2GB: boot/initrd.img-2.6.32-29-generic
  49.3GB: boot/initrd.img-2.6.32-30-generic
   5.7GB: boot/vmlinuz-2.6.32-21-generic
  12.6GB: boot/vmlinuz-2.6.32-23-generic
  14.0GB: boot/vmlinuz-2.6.32-24-generic
  16.4GB: boot/vmlinuz-2.6.32-25-generic
  29.8GB: boot/vmlinuz-2.6.32-26-generic
  26.8GB: boot/vmlinuz-2.6.32-27-generic
  13.0GB: boot/vmlinuz-2.6.32-28-generic
  15.3GB: boot/vmlinuz-2.6.32-29-generic
  49.2GB: boot/vmlinuz-2.6.32-30-generic
  49.3GB: initrd.img
   9.2GB: initrd.img.old
  49.2GB: vmlinuz
  15.3GB: vmlinuz.old

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b0f0e160-6031-4daa-83e6-1cd8e42fa460 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=9c93e080-e6a3-4154-9163-a93002955b0e none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 105.4GB: boot/initrd.img-2.6.32-21-generic
 101.0GB: boot/vmlinuz-2.6.32-21-generic
 105.4GB: initrd.img
 101.0GB: vmlinuz

================================ sda4/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  4e 04 69 cc fa 29 48 04  b5 d2 fa 1d 09 04 dc 21  |N.i..)H........!|
00000010  fa 53 49 04 b6 d8 fa 35  9d 04 a5 6f fa 48 86 04  |.SI....5...o.H..|
00000020  4c 92 fa 0c e1 04 0a 30  fa 38 d3 03 c6 24 fa 63  |L......0.8...$.c|
00000030  0d 03 c8 fe fa 9c 7a 03  ba f3 fa d7 77 03 d9 36  |......z.....w..6|
00000040  fa f4 14 03 c4 08 fb 65  96 03 db ce fb 56 41 03  |.......e.....VA.|
00000050  a7 c7 fb b1 e9 03 49 02  fc 29 40 03 11 85 fc 76  |......I..)@....v|
00000060  a1 02 be a9 fd 5c 49 02  87 f1 fe 1d f5 02 7e 1e  |.....\I.......~.|
00000070  fe a3 c5 02 41 f5 ff 5c  6d 02 2b 78 ff b1 f2 01  |....A..\m.+x....|
00000080  ef aa 00 1c b1 01 ab 79  00 61 22 01 7c 12 00 b3  |.......y.a".|...|
00000090  7c 01 31 80 00 ce d2 00  f4 07 01 11 53 00 bb d5  ||.1.........S...|
000000a0  01 14 ce 00 a1 b9 01 4f  91 00 83 a4 01 9e d8 00  |.......O........|
000000b0  8e 55 01 d3 af 00 a6 28  02 1d 44 00 95 a4 02 76  |.U.....(..D....v|
000000c0  85 00 92 71 02 af 36 00  86 4c 02 da 4f 00 4e eb  |...q..6..L..O.N.|
000000d0  03 14 2b 00 52 28 03 1d  47 00 54 67 03 30 7e 00  |..+.R(..G.Tg.0~.|
000000e0  94 b1 02 f9 ed 00 fd 1d  02 d4 d9 01 53 7f 02 74  |............S..t|
000000f0  15 01 e1 7f 02 28 29 02  16 37 01 df 05 02 72 9e  |.....()..7....r.|
00000100  01 44 fb 02 b4 1c 00 e4  2c 02 dc 95 00 83 b6 03  |.D......,.......|
00000110  24 85 00 5a ba 03 7f 23  00 15 fa 04 0a 44 ff ce  |$..Z...#.....D..|
00000120  27 04 71 fd ff 64 a8 04  c9 5b fe da 69 05 1f d2  |'.q..d...[..i...|
00000130  fe 11 e7 05 2c a0 fd 52  60 04 e5 81 fc a9 d8 04  |....,..R`.......|
00000140  80 ab fc 4d 71 04 1c 4c  fc 45 de 04 0f e0 fc 44  |...Mq..L.E.....D|
00000150  a7 03 f9 51 fc 6c 1f 04  51 7c fc 3e c2 04 76 a3  |...Q.l..Q|.>..v.|
00000160  fc 37 d0 04 86 a6 fb e3  37 04 a1 01 fb a7 87 04  |.7......7.......|
00000170  5e 8e fb 74 ee 04 2a 93  fb 97 85 03 ea b6 fb d4  |^..t..*.........|
00000180  88 03 c9 d0 fc 36 53 03  b4 9f fc 6f 0f 03 d5 66  |.....6S....o...f|
00000190  fc 97 20 03 b7 03 fc a3  7b 03 c2 2d fc 0c bb 03  |.. .....{..-....|
000001a0  55 30 fb a7 21 02 88 e1  fb 48 2a 01 7a 16 fb 6d  |U0..!....H*.z..m|
000001b0  ec 00 74 fa fb 92 46 ff  81 0e fc 0e 60 fe 00 01  |..t...F.....`...|
000001c0  01 40 82 fe bf ae 02 00  00 00 70 b7 98 00 00 fe  |.@........p.....|
000001d0  ff ff 05 fe ff ff 37 da  a6 0a f7 1e e9 00 00 00  |......7.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```And the gparted thumbnail is attached.

> **oldfred said:**
> You /boot has menu.lst from grub legacy. But you have grub2 in the MBR  and are booting sda6. I would expect the grub menu in sda6 then gives  you the choice to boot your other installs.
> **Dutch70 said:**
> 2. I don't see any windows to grub weirdness on  you computer. You have windows installed to sda4, which is a primary  partition, so you're good. That's where the boot flag should be. I don't  think Ubuntu even pays any attention to the boot flag.

Ah. Part of my confusion was from thinking the partition with the boot flag was where the boot process started.

So the MBR is attached to the drive, rather than stored in a specific partition... that makes sense. In the meantime I have learned that grub.cfg == menu.lst for grub2. Other questions arise:

4. If fdisk -l 'lies' to me about which is the boot partition... well, not really lies, you know what I mean... what's the standard tool I should use to find that out? (if bootinfoscript wasn't available)
5. My primary partition is /dev/sda8. What should I do if I want to get rid of or move /dev/sda6, which I'm apparently using to boot at the moment?

Many thanks!

---

### Post by oldfred on 2011-04-18
The boot flag is used by windows (and lilo) but not by grub. 

Only if you have boot issues would you want to know which is booting first. The boot script is real handy. 

The first install listed in the grub menu is the one booting. And you can run mount command to see which you have booted.

---

### Post by Dutch70 on 2011-04-18
To move Grub2 to sda8, run this command.
```
sudo grub-install /dev/sda8
```
Here is the link for that, you may want to look over it.
[[COLOR="Red"]https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202[/COLOR]]("https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202")

You can delete /dev/sda7 & edit fstab by removing this line.
```
# swap was on /dev/sda7 during installation
UUID=9c93e080-e6a3-4154-9163-a93002955b0e none            swap    sw              0 
```
To edit fstab, use...
```
gksudo gedit /etc/fstab
```
Then run update-grub (as root) and reboot.

I'm still looking over your partitions and boot script, it's just about as bad as mine. ;) 
I'm thinking that we could make it simpler by a) Getting rid of sda1, but I'm not sure how to do that. b) Removing the old kernels by going to synaptic & search for "linux-image-2" and mark the old ones for complete removal. Be Careful not to remove the wrong one. Ubuntu Tweak will also do it for you.

Edit: I also want to mention that using sda3 for / and sda8 for /home would be a nice set up, but it would take some work.

---

### Post by Quackers on 2011-04-18
Ignoring duplicate entries (with different kernels) what entries currently appear in the grub menu, and are they all bootable?
Which of these do you want to keep?

Dutch70, installing grub2 to a partition at this stage is probably over-complicating the already over-complicated :-)

---

### Post by doubi on 2011-04-19
Thanks for all the replies!
> **Dutch70 said:**
> 
[...]
I'm thinking that we could make it simpler by a) Getting rid of sda1,  but I'm not sure how to do that.

Couldn't I just boot from CD and use GParted to remove the partition and move everything else "to the left"?
I'm not booting from it so it's not doing anything, right?

Or would I be in danger of messing up the GPT or something somehow because it's right at the start of the drive?
Or would the change in sda device numbering break something?
> **Dutch70 said:**
> 
b) Removing the old kernels by going to  synaptic & search for "linux-image-2" and mark the old ones for  complete removal. Be Careful not to remove the wrong one. Ubuntu Tweak  will also do it for you.

You can do that!? Awesome! :D
> **Dutch70 said:**
> 
Edit: I also want to mention that using sda3 for / and sda8 for /home  would be a nice set up, but it would take some work.
Yea, I read about that when first getting set up with Ubuntu. Can't remember why I didn't. Think I read somewhere that separating out the data means your drive head has to run about more and wears it down  slightly quicker or something. Also, might it complicate things if I have 32bit distros alongside 64bit ones? (my laptop can convincingly emulate 64bit apparently, good for testing during development).
> **oldfred said:**
> The boot flag is used by windows (and lilo) but not by grub.

Ah, good to know.
> **oldfred said:**
> 
The first install listed in the grub menu is the one booting. And you  can run mount command to see which you have booted.
So, say you have two copies of Ubuntu installed side by side. Every time you do a kernel update the boot menu appears to be reordered, putting the latest installed kernel at the top. Does that mean that as part of the process of updating the kernel grub is moved to the updating partition?
> **Quackers said:**
> Ignoring duplicate entries (with different  kernels) what entries currently appear in the grub menu, and are they  all bootable?
Which of these do you want to keep?
I think it's:
Ubuntu 10.4 64bit on /dev/sda6
Ubuntu 10.4 32bit on /dev/sda3
Win XP on /dev/sda4
Ubuntu 10.4 32bit on /dev/sda8

I'm not fussed about keeping the /dev/sda3 one but I want to keep the others. I take it in general, if you want to install a new OS but keep your grub where it is, you choose not to install grub in the installation menu, then go back to your "main" OS and run grub-update and it'll find the new one and add it to the menu?

---

### Post by oldfred on 2011-04-19
While grub2 is very good at finding other installs, you do have to update it in the version you boot to find changes in any others that you boot. 

One work around is to boot the partition and boot the newest kernel. Ubuntu puts a link to the newest kernel in / (root).

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

Copy copy any entries you want from this  and add whatever else you want:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by Dutch70 on 2011-04-19
> Couldn't I just boot from CD and use GParted to remove the partition and move everything else "to the left"?
I'm not booting from it so it's not doing anything, right?
I don't think you'll be able to move the entire extended partition to the left.

> Yea, I read about that when first getting set up with Ubuntu. Can't remember why I didn't. Think I read somewhere that separating out the data means your drive head has to run about more and wears it down slightly quicker or something. Also, might it complicate things if I have 32bit distros alongside 64bit ones? (my laptop can convincingly emulate 64bit apparently, good for testing during development)
I don't know anything about wearing your hdd down quicker.
Yes, if you are using more than one distro, you don't want a /home for each of them. There are other ways to do that. However, the advantages of having a /home for your main distro are very nice.

I wouldn't worry too much about grub, it's a matter of 2 commands to reinstall or move. Sometimes only one command.

> So, say you have two copies of Ubuntu installed side by side. Every time you do a kernel update the boot menu appears to be reordered, putting the latest installed kernel at the top. Does that mean that as part of the process of updating the kernel grub is moved to the updating partition?
If I understand you correctly, the answer to that is yes. For example, just about everyday when I update Natty on Ubuntu & Kubuntu, I have to reinstall grub2 to the system I want it on, but Natty gets a lot of updates right now, and the version of grub it uses is technically 1.99 as opposed to 1.98.

---

### Post by oldfred on 2011-04-19
I do not know for sure, but if you have a large system partition then the drive heads have to search all over the drive for the most used system files. Smaller system partitions avoid that issue. Data typically is loaded one or two files at a time so having data all over drive is less wear.

We have seen 1 or 2TB drives with only a root partition and then with grub located near the end of the drive.

---

### Post by doubi on 2011-04-21
> **Dutch70 said:**
> Removing the old kernels by going to synaptic & search for "linux-image-2" and mark the old ones for complete removal.
Did that, apart from the previous two. Looking a lot neater now.

I got the 2.6.32.31 update this morning, on my main install (/dev/sda8 ). I was expecting it to do what it used to do - "take over" grub and put itself at the top of the boot menu. But oddly, this time, it didn't - I had to boot /dev/sda6 and update-grub there, as oldfred mentioned. I've been using only one install since last last summer, I guess the update to grub2 must have happened since then and I just didn't notice grub no longer did that taking-over thing.

> **Dutch70 said:**
> To move Grub2 to sda8, run this command.
```
sudo grub-install /dev/sda8
```Here is the link for that, you may want to look over it.
[[COLOR=Red]https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202[/COLOR]]("https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202")

I read over the documentation there. I'm sure it's safe to do, as you said you do it almost every day, but y'know, warnings in allcaps are worrying.

The warning (as you'll know) says that I'm asking grub to be installed to a partition rather than the MBR. Is there a way to install it "properly" to the MBR, or just update the MBR to look to /dev/sda8 rather than /dev/sda6?

e.g., The instructions for Reinstalling Grub, Method 2 on the Grub2 help page you linked show an example of using grub-setup, as opposed to grub-install, and says that the former command installs what's needed to the MBR as well as files to the partition. Might I be able to use it for my purposes? (with different arguments since I wouldn't be using a live cd, naturally)

What's weird is I read somewhere in the past half-hour that it grub-install can invoke grub-setup, so I would've thought grub-install would install to the MBR instead of throwing out threatening errors about installing to a partition...

---

### Post by dino99 on 2011-04-21
use startup-manager (system admin startup-manager) after installation from synaptic

---

### Post by Dutch70 on 2011-04-21
> **doubi said:**
> Did that, apart from the previous two. Looking a lot neater now.

I got the 2.6.32.31 update this morning, on my main install (/dev/sda8 ). I was expecting it to do what it used to do - "take over" grub and put itself at the top of the boot menu. But oddly, this time, it didn't - I had to boot /dev/sda6 and update-grub there, as oldfred mentioned. I've been using only one install since last last summer, I guess the update to grub2 must have happened since then and I just didn't notice grub no longer did that taking-over thing.
That's because you have grub installed to sda6, you're not using grub on sda8 according  to your last boot script.

> I read over the documentation there. I'm sure it's safe to do, as you said you do it almost every day, but y'know, warnings in allcaps are worrying.

The warning (as you'll know) says that I'm asking grub to be installed to a partition rather than the MBR. Is there a way to install it "properly" to the MBR, or just update the MBR to look to /dev/sda8 rather than /dev/sda6?

e.g., The instructions for Reinstalling Grub, Method 2 on the Grub2 help page you linked show an example of using grub-setup, as opposed to grub-install, and says that the former command installs what's needed to the MBR as well as files to the partition. Might I be able to use it for my purposes? (with different arguments since I wouldn't be using a live cd, naturally)

What's weird is I read somewhere in the past half-hour that it grub-install can invoke grub-setup, so I would've thought grub-install would install to the MBR instead of throwing out threatening errors about installing to a partition...

Use the live cd/usb install method and you won't get that error. This is actually the way I normally  do it, but I do it from a different install. For example, you could run these two commands from the system you have on sda6 or from the live cd/usb. I just ran these for the heck of it, and I got no warnings like that. (except mine is sda1)
```
sudo mount /dev/sda8 /mnt
``` 
and...
```
sudo grub-install --root-directory=/mnt /dev/sda
```
Here is the link for that, check it out to make sure I didn't make a mistake.
[[COLOR="Red"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Edit: After looking at oldfred's post below, I just noticed the command I originally gave you had "sda8" instead of "sda". Probably from where I'm used to doing the one in the 1st command above, which is correct. Sorry about that, glad you heeded the warning.
Thanks oldfred! :)

---

### Post by oldfred on 2011-04-21
If you boot into your install on sda8, you can directly install grub to the MBR from there with one line.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
[COLOR=Red]sudo grub-install /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

This only applies if you have more than one drive:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by doubi on 2011-04-22
> **Dutch70 said:**
> Edit: After looking at oldfred's post below, I just noticed the command I originally gave you had "sda8" instead of "sda". Probably from where I'm used to doing the one in the 1st command above, which is correct. Sorry about that, glad you heeded the warning.
Thanks oldfred! :)
Aha! Silly me for not noticing the difference on the Grub2 page you linked.

WELL, thanks to your and oldfred's advice I've finally got things looking a bit tidier :-)

> **Dutch70 said:**
> 
I'm thinking that we could make it simpler by a) Getting rid of sda1,  but I'm not sure how to do that.
Turned out GParted was fine with that - booted from CD, unmounted everything inside the extended partition and I could extend it over where sda1 used to be no problem. Got rid of the extra swap and old kernels too, and grub is now installed to /sda7 - there wasn't even any confusion with /sda8 becoming /sda7 when I removed the /sda5 swap partition, thanks to the magic of UUIDs. Joy!

The only thing left to do now really is try some themes 'n' such on the grub menu so when people see it it looks more attractive and friendly and less "Oooh that linux stuff looks scary" :)

Many thanks for your help all!

---

### Post by Dutch70 on 2011-04-22
Nice work doubi! :KS

Just want to mention, now that you've gotten rid of the /boot partition, you've got room for another primary partition if you ever wanted to create one. You could cut it out of sda3 for example. 

Here's a good place to get ideas, and show your themes when you get it the way you like it.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1718689&page=44[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1718689&page=44")

---

