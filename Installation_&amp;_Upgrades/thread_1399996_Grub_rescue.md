---
title: "Grub rescue"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by AmbiguousOutlier on 2010-02-06
Hello, I've just tried to dual boot Ubuntu and XBMC live but I'm getting the grub rescue prompt. After googling I found that I this might help;


[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Does anyone know what it means?

```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/mapper/pdc_fafihciji and looks at 
    sector 500527 of the same hard drive for core.img, core.img is at this 
    location on /dev/sda and looks for 
    (UUID=af32da0d-5370-438f-80aa-4c9e43d67fcb)/boot/grub.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ce878

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,302,559    29,302,497  83 Linux
/dev/sda2          58,605,120   976,768,064   918,162,945   5 Extended
/dev/sda5         960,189,048   976,768,064    16,579,017  82 Linux swap / Solaris
/dev/sda6          58,605,246   960,188,984   901,583,739  83 Linux
/dev/sda3          29,302,560    58,605,119    29,302,560  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009f55d

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   5 Extended
/dev/sdc5                 126 1,953,520,064 1,953,519,939  83 Linux


Drive: pdc_fafihciji ___________________ _____________________________________________________

Disk /dev/mapper/pdc_fafihciji: 1000.1 GB, 1000136638464 bytes
255 heads, 63 sectors/track, 121593 cylinders, total 1953391872 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        77711583-1fe8-434c-82d3-e2710e06495a   ext4                                     
/dev/sda3        e3a4a8a6-b4b8-43b6-9676-5156becda79c   ext4                                     
/dev/sda5        859d3ad6-3cdb-46a9-be01-1efdaaa5f150   swap                                     
/dev/sda6        ce2a5994-4b2a-472f-9916-c65bc1840c8f   ext4                                     
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc5        ce4f41da-4f3c-4c3b-bc11-fc0c08879ff7   ext4       Library                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=77711583-1fe8-434c-82d3-e2710e06495a ro xbmc=autostart,nodiskmount,setvolume loglevel=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=77711583-1fe8-434c-82d3-e2710e06495a

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

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		77711583-1fe8-434c-82d3-e2710e06495a
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=77711583-1fe8-434c-82d3-e2710e06495a ro quiet splash  xbmc=autostart,nodiskmount,setvolume loglevel=0
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		77711583-1fe8-434c-82d3-e2710e06495a
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=77711583-1fe8-434c-82d3-e2710e06495a ro  single xbmc=autostart,nodiskmount,setvolume loglevel=0
initrd		/boot/initrd.img-2.6.31-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, Linux 2.6.31-19-generic-pae (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=e3a4a8a6-b4b8-43b6-9676-5156becda79c ro quiet splash  xbmc=autostart,nodiskmount,setvolume loglevel=0
initrd		/boot/initrd.img-2.6.31-19-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=e3a4a8a6-b4b8-43b6-9676-5156becda79c ro single  xbmc=autostart,nodiskmount,setvolume loglevel=0
initrd		/boot/initrd.img-2.6.31-19-generic-pae
savedefault
boot


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=77711583-1fe8-434c-82d3-e2710e06495a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ce2a5994-4b2a-472f-9916-c65bc1840c8f /home           ext4    defaults        0       2
# /media/library was on /dev/sdc5 during installation
UUID=ce4f41da-4f3c-4c3b-bc11-fc0c08879ff7 /media/library  ext4    defaults        0       2
# /media/ubuntu was on /dev/sda3 during installation
UUID=e3a4a8a6-b4b8-43b6-9676-5156becda79c /media/ubuntu   ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=859d3ad6-3cdb-46a9-be01-1efdaaa5f150 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: vmlinuz

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set e3a4a8a6-b4b8-43b6-9676-5156becda79c
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set e3a4a8a6-b4b8-43b6-9676-5156becda79c
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=e3a4a8a6-b4b8-43b6-9676-5156becda79c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set e3a4a8a6-b4b8-43b6-9676-5156becda79c
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=e3a4a8a6-b4b8-43b6-9676-5156becda79c ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 77711583-1fe8-434c-82d3-e2710e06495a
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=77711583-1fe8-434c-82d3-e2710e06495a ro quiet splash xbmc=autostart,nodiskmount,setvolume loglevel=0
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 77711583-1fe8-434c-82d3-e2710e06495a
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=77711583-1fe8-434c-82d3-e2710e06495a ro single xbmc=autostart,nodiskmount,setvolume loglevel=0
	initrd /boot/initrd.img-2.6.31-16-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=e3a4a8a6-b4b8-43b6-9676-5156becda79c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ce2a5994-4b2a-472f-9916-c65bc1840c8f /home           ext4    defaults        0       2
# /media/library was on /dev/sdc5 during installation
UUID=ce4f41da-4f3c-4c3b-bc11-fc0c08879ff7 /media/library  ext4    defaults        0       2
# /media/xbmc was on /dev/sda1 during installation
UUID=39300625-5bfe-4e5d-8afc-307f883b6f01 /media/xbmc     ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=859d3ad6-3cdb-46a9-be01-1efdaaa5f150 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  15.0GB: boot/grub/core.img
  15.0GB: boot/grub/grub.cfg
  15.0GB: boot/initrd.img-2.6.31-19-generic-pae
  15.0GB: boot/vmlinuz-2.6.31-19-generic-pae
  15.0GB: initrd.img
  15.0GB: vmlinuz
=============================== StdErr Messages: ===============================

ERROR: creating degraded mirror mapping for "pdc_fafihciji"

```

---

### Post by darkod on 2010-02-06
First of all, /dev/sdb disk is a raid member as you can see in the results. So, since it seems you're not running a raid, get rid of the settings remains because they create confusion. Best is to boot with ubuntu 9.10 cd, Try Ubuntu option, and in terminal do:

sudo dmraid -E -r /dev/sdb
sudo apt-get remove dmraid

That should get rid of it.

Second thing is, it seems you installed a bootloader (grub/grub2) with both ubuntu and xbmc. Why? You only need one grub and you can boot as many linux versions as you want. DO NOT let all of your linux installations to install a bootloader, it will just confuse you.
Depending which bootloader you want to use now, you will need to make sure it's installed on the MBR of /dev/sda and make that disk first choice in BIOS in hdd boot order.

---

### Post by AmbiguousOutlier on 2010-02-06
I am running a RAID but it's hardware raid and the mobo takes care of it. 

Within the ubuntu live cd. I did; 

sudo dmraid -E -r /dev/sdb
sudo apt-get remove dmraid

When I rebooted. It destroyed my raid. (It's backed up so I'm not too bothered if data has been lost). 

I still get the grub rescue> prompt.

I'm not sure how to install a linux distro without installing grub. I want my xbmc on sda1 to boot by default. With Ubuntu a secondary boot device. How do I that?

---

### Post by darkod on 2010-02-06
> **RhysGM said:**
> I am running a RAID but it's hardware raid and the mobo takes care of it. 

Within the ubuntu live cd. I did; 

sudo dmraid -E -r /dev/sdb
sudo apt-get remove dmraid

When I rebooted. It destroyed my raid. (It's backed up so I'm not too bothered if data has been lost). 

I still get the grub rescue> prompt.

I'm not sure how to install a linux distro without installing grub. I want my xbmc on sda1 to boot by default. With Ubuntu a secondary boot device. How do I that?

I said "it seems you're not running a raid". If you did you shouldn't have executed those commands. In the results I never saw a second drive for a raid array.

Anyway, for install on fakeraid (motherboard raid), read here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

There are some additional steps for grub, maybe that's why it's not working. Read carefully, probably you don't need to reinstall ubuntu, just grub.
I don't have much experience with fakeraid so I can't help much except for that link.

---

### Post by darkod on 2010-02-06
> **RhysGM said:**
> 
I'm not sure how to install a linux distro without installing grub. I want my xbmc on sda1 to boot by default. With Ubuntu a secondary boot device. How do I that?

I'm not sure about xbmc but when using the ubuntu desktop livecd (and for raid you should use the alterernate install cd by the way), in the last screen before clicking Install, click on Advanced and you can cancel the bootloader install there.

---

### Post by AmbiguousOutlier on 2010-02-06
I deleted my hdd, and installed xbmc on sda1, then I installed ubuntu on sda3 without installing the bootloader.

However I can now only boot into xbmc. How do I add Ubuntu to the grub menu?

---

### Post by darkod on 2010-02-06
> **RhysGM said:**
> I deleted my hdd, and installed xbmc on sda1, then I installed ubuntu on sda3 without installing the bootloader.

However I can now only boot into xbmc. How do I add Ubuntu to the grub menu?

I don't know the exact commands. I guess xbmc is using grub1, in that case you would need to edit:
sudo gedit /boot/grub/menu.lst

NOTE: if it open an empty file, just close it. That means you're using grub2 most probably.

Grub1 does not detect an OS automatically like grub2 (so maybe it was better to use the ubuntu bootloader), but google should give you an answer how to boot ubuntu 9.10 in grub legacy.

In menu.lst you would need to add at the end something like:

title Ubuntu 9.10
root (hd0,2)               -> if it's on /dev/sda3
kernel /boot/grub/kernel....
initrd /boot/grub/initrd....
boot

But look on google for the right syntax.

---

### Post by AmbiguousOutlier on 2010-02-06
This was the closest thing I found in google;

title Ubuntu 9.10
root (hd0,2)
makeactive
chainloader+1


so I did as you said, but nothing happens when I select it.


EDIT:
Would it be easier if I just installed Grub2

---

### Post by darkod on 2010-02-06
> **RhysGM said:**
> This was the closest thing I found in google;

title Ubuntu 9.10
root (hd0,2)
makeactive
chainloader+1


so I did as you said, but nothing happens when I select it.

No, that is only to chainload it. For this your would have to have ubuntu's grub2 on /dev/sda3, on the actual partition.
Give me a sec to search, I'm sure I've seen it around.

---

### Post by darkod on 2010-02-06
In fact, we can copy part from your results file, the:

linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=e3a4a8a6-b4b8-43b6-9676-5156becda79c ro   quiet splash
  initrd    /boot/initrd.img-2.6.31-19-generic-pae

So it would be like (lets drop the UUID):

title Ubuntu 9.10
root (hd0,2)
linux /boot/vmlinuz-2.6.31-19-generic-pae root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-2.6.31-19-generic-pae
boot

Check for the new install whether the kernel is again 2.6.31-19 if not, adjust in the above to match the exact kernel name and initrd name.
Save the edited menu.lst and reboot. If that helped, if you want to create the recovery mode entry too, just copy again the same and in the linux line at the end just use:
ro single

instead of:
ro quiet splash

---

### Post by AmbiguousOutlier on 2010-02-06
The Kernal is correct, however I now get this

```

Error 19: Linux kernal nust be loaded before initrd

Press any key to continue...
```

[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

Although this error really doesn't make any sense.

---

### Post by darkod on 2010-02-06
> **RhysGM said:**
> The Kernal is correct, however I now get this

```

Error 19: Linux kernal nust be loaded before initrd

Press any key to continue...
```[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

Although this error really doesn't make any sense.

I'm puzzled. If the linux line is before the initrd line, it does get loaded before initrd. At least it should.

---

### Post by AmbiguousOutlier on 2010-02-06
I coppied the original from the beginning of my post, and it got further now it says, copying by hand;

```

Gave up waiting for root device. Common problem:
- Boot arys (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
-Missing modules (cat /proc modules: ls /dev)
ALERT! /dev/disk/by-uuid/e3a4a8a6-b4b8-43b6-9676-5156becda79c does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ask)
Enter 'help' for a list of built-in commands

(initanfs)
```

---

### Post by AmbiguousOutlier on 2010-02-06
I did another boot info script if that helps

```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 500527 of 
    the same hard drive for core.img, core.img is at this location on /dev/sda 
    and looks for (UUID=af32da0d-5370-438f-80aa-4c9e43d67fcb)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ce878

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    29,302,559    29,302,497  83 Linux
/dev/sda2          58,605,120   976,768,064   918,162,945   5 Extended
/dev/sda5         960,189,048   976,768,064    16,579,017  82 Linux swap / Solaris
/dev/sda6          58,605,246   960,188,984   901,583,739  83 Linux
/dev/sda3    *     29,302,560    58,605,119    29,302,560  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009f55d

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   5 Extended
/dev/sdc5                 126 1,953,520,064 1,953,519,939  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b18498d2-0874-42fe-a0de-714fd744a7ae   ext4       xbmc                          
/dev/sda3        238f4bb2-10da-4855-ad17-3a21b1799d9f   ext4                                     
/dev/sda5        859d3ad6-3cdb-46a9-be01-1efdaaa5f150   swap                                     
/dev/sda6        fca1adb1-bd03-452e-a9e2-da2486f6ff25   ext4       home                          
/dev/sdc5        ce4f41da-4f3c-4c3b-bc11-fc0c08879ff7   ext4       Library                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b18498d2-0874-42fe-a0de-714fd744a7ae ro xbmc=autostart,nodiskmount,setvolume loglevel=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=b18498d2-0874-42fe-a0de-714fd744a7ae

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

title		XBMC Live
uuid		b18498d2-0874-42fe-a0de-714fd744a7ae
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=b18498d2-0874-42fe-a0de-714fd744a7ae ro quiet splash  xbmc=autostart,nodiskmount,setvolume loglevel=0
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		XBMC Live (recovery mode)
uuid		b18498d2-0874-42fe-a0de-714fd744a7ae
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=b18498d2-0874-42fe-a0de-714fd744a7ae ro  single xbmc=autostart,nodiskmount,setvolume loglevel=0
initrd		/boot/initrd.img-2.6.31-16-generic

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, Linux 2.6.31-19-generic-pae (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=e3a4a8a6-b4b8-43b6-9676-5156becda79c ro quiet splash  xbmc=autostart,nodiskmount,setvolume loglevel=0
initrd		/boot/initrd.img-2.6.31-19-generic-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=e3a4a8a6-b4b8-43b6-9676-5156becda79c ro single  xbmc=autostart,nodiskmount,setvolume loglevel=0
initrd		/boot/initrd.img-2.6.31-19-generic-pae
savedefault
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b18498d2-0874-42fe-a0de-714fd744a7ae /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=fca1adb1-bd03-452e-a9e2-da2486f6ff25 /home           ext4    defaults        0       2
# /media/library was on /dev/sdc5 during installation
UUID=ce4f41da-4f3c-4c3b-bc11-fc0c08879ff7 /media/library  ext4    defaults        0       2
# /media/ubuntu was on /dev/sda3 during installation
UUID=ec0d0416-3a19-4fc0-a3be-29eb079a68bb /media/ubuntu   ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=859d3ad6-3cdb-46a9-be01-1efdaaa5f150 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: vmlinuz

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=238f4bb2-10da-4855-ad17-3a21b1799d9f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=fca1adb1-bd03-452e-a9e2-da2486f6ff25 /home           ext4    defaults        0       2
# /media/library was on /dev/sdc5 during installation
UUID=ce4f41da-4f3c-4c3b-bc11-fc0c08879ff7 /media/library  ext4    defaults        0       2
# /media/xbmc was on /dev/sda1 during installation
UUID=b18498d2-0874-42fe-a0de-714fd744a7ae /media/xbmc     ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=859d3ad6-3cdb-46a9-be01-1efdaaa5f150 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  15.0GB: boot/initrd.img-2.6.31-19-generic-pae
  15.0GB: boot/vmlinuz-2.6.31-19-generic-pae
  15.0GB: initrd.img
  15.0GB: vmlinuz
```

---

### Post by darkod on 2010-02-06
> **RhysGM said:**
> I coppied the original from the beginning of my post, and it got further now it says, copying by hand;

```

Gave up waiting for root device. Common problem:
- Boot arys (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
-Missing modules (cat /proc modules: ls /dev)
ALERT! /dev/disk/by-uuid/e3a4a8a6-b4b8-43b6-9676-5156becda79c does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ask)
Enter 'help' for a list of built-in commands

(initanfs)
```

You can't use UUID e3a4..... because you reinstalled and the new partitions have new UUIDs. That's why I was trying to avoid it.
But you can use the exact lines only change the UUID value. You can find out UUID values with:
sudo blkid

You need the one for /dev/sda3, the ubuntu root partition.

PS.
/dev/sda3        [COLOR=Red]238f4bb2-10da-4855-ad17-3a21b1799d9f[/COLOR]

---

### Post by AmbiguousOutlier on 2010-02-06
> **darkod said:**
> 
PS.
/dev/sda3        [COLOR=Red]238f4bb2-10da-4855-ad17-3a21b1799d9f[/COLOR]

Are you trying to tell me this is the name of my new partition and all I need to do is replace the UUID= with this value?

It worked. 

Thank you so very much. I've been trying for days to get my dual boot work and now it does. :D:D:D

---

### Post by darkod on 2010-02-06
> **RhysGM said:**
> Are you trying to tell me this is the name of my new partition and all I need to do is replace the UUID= with this value?

It worked. 

Thank you so very much. I've been trying for days to get my dual boot work and now it does. :D:D:D

OK, excellent. Yes, I got the UUID of /dev/sda3 from the latest results file you posted.

Just to remind you (look at the top of the results file), you have invalid grub2 (from the previous install) on the MBR of /dev/sdb, but as long as you have /dev/sda as first option to boot from, you won't even notice it.

---

### Post by lat297 on 2010-10-22
Hi

I have exactly this issue, but am at a loss as to how I can fix it...  I do apologise, as I am a Linux/Ubuntu novice and have been introduced to this by XBMC!

How do I:
1) get the boot info output that will tell me what the correct UUID for my partition is?
2) modify this so that it boots?

Thanks!

Luke

---

