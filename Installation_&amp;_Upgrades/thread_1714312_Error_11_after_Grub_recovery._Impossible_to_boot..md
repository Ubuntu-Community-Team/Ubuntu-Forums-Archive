---
title: "Error 11 after Grub recovery. Impossible to boot."
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by CydMM on 2011-03-25
Good morning,


  in my system I have dual boot between Kubuntu latest version (in one disk) and Windows 7 64 bit in another disk.


  Well, I had to format and proceed to a fresh install of Win7 due to huge problems and, as it was supposed to, it is nomore available the possibility to choose the OS to boot.
  [FONT=&quot] [/FONT]
  [FONT=&quot]I followed the official guide to recover Grub through Live CD but, probably due to the fact I am a Linux Newbie and due to the fact I almost twice tried to install Grub 2 without succeeding I came back to Grub and this is what happens now each time I reboot:[/FONT]
[FONT=&quot]
[/FONT]
  [FONT=&quot]I get the following message for a couple of seconds:[/FONT]
  [FONT=&quot] [/FONT]
  **GRUB Loading stage 1.5 ….**
 
 [FONT=&quot][/FONT]
  [FONT=&quot]Then the screen shows the following message:[/FONT]
  [FONT=&quot] [/FONT]
  **ERROR 11: unrecognized error string, press any key to continue...**
 
 [FONT=&quot][/FONT]
  [FONT=&quot]Pressing any key the screen now shows a window with only one option: [/FONT]**Chainload into Grub 2. ** After the only option I have, pressing OK, the scrren shows again the previous **Error 11** message.
   
  This is the configuration of my Kubuntu Install:
   
  /dev/sdb1            1              48829536       83   Linux
/dev/sdb2            6080           4883760       82   Linux Swap / Solaris
/dev/sdb3            6688        195310237+    83   Linux
 
 [FONT=&quot][/FONT]
  [FONT=&quot]Following the Grub recovery procedure from the official Ubuntu Site I mounted **sdb1** as partition where Linux is placed and **sdb3** as separate boot partition (was that correct?)[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Please help me, I really don’t know how to fix that disaster :-([/FONT]

---

### Post by Quackers on 2011-03-25
If you are running Kubuntu 10.10 you should be trying to install grub2, which is the default for later versions.
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by CydMM on 2011-03-25
Hi Quackers,

thanks for your answer. As soon as I come back home this evening, after job, I will follow your instructions and promptly post here the results.

I hope to find you here this evening at around 7.30pm, so that we can try to fix this huge problem.

Thank you so much :)

---

### Post by Quackers on 2011-03-25
If your 7-30 is the UK version, that shouldn't be a problem :wink:
Don't worry, there are many here who can help you.

---

### Post by CydMM on 2011-03-25
My 7.30PM is italian time so...let's say it is ok with me even if we are talking about 7.30PM UK time ;-) I will be here.

---

### Post by Quackers on 2011-03-25
No problem then :-)
A couple of bits of info would be good.
Are both your hard drives internal drives or is one a usb drive?
If internal, are both selectable as first boot devices in your bios? Or just the first?

---

### Post by CydMM on 2011-03-25
Both hard drives are internal. As far as the other query is concerned, I am not really sure of the answer but&#8230;I am inclined to say that they both should be selectable as first boot devices.
 In fact, at the very first beginning of my PC life, the hard drive that now holds Win7 was the one to boot&#8230;and the hard drive now with Linux once was just destined to get data for backup.
But I am not totally sure that all that implies that both drives can be selected as first boot device

---

### Post by Quackers on 2011-03-25
Ok thanks. You will need to look in your bios settings and see which of the drives is set to boot first at the moment, please.

---

### Post by CydMM on 2011-03-25
Sure I will, as soon as I come back home.

Is there anything else I should do with my system later before getting back to you?

---

### Post by Quackers on 2011-03-25
There are a couple of things you should have already. A set of Windows recovery dvd's or an installation disc. A Windows repair disc can also be needed (made via Control Panel > Backup & Restore Centre > left pane).

Apart from the bios check, the boot info script should give the needed information.

---

### Post by CydMM on 2011-03-25
I do have the Windows 7 installation disc but I never created a Windows repair disc. Naturally, I am now unable to create one of it because it is impossible for me to boot Win 7 (nor Kubuntu either).
  As far as the boot info script is concerned, I will run it as you asked me to.

---

### Post by Quackers on 2011-03-25
The Win 7 installation disc will do fine :-)

---

### Post by CydMM on 2011-03-25
Great then ;-)

---

### Post by CydMM on 2011-03-25
Here we are! :D

So, as regards Bios boot sequence, now the first device is the CD drive then, second place the only one hard drive that can be chosen.

In other words, there is only one hard drive selectable, and it is SATA PM-WDC WD 3000 and I don't know which one is it...I guess it is the one where Windows 7 is installed.

As regards the bootinfoscript, here follows the result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #3 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/core.img /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   586,070,015   586,067,968   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    97,659,134    97,659,072  83 Linux
/dev/sdb2          97,659,135   107,426,654     9,767,520  82 Linux swap / Solaris
/dev/sdb3         107,426,655   498,047,129   390,620,475  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C0308C6A308C68EC                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        178f3bbd-ca03-4573-a98d-3c66a91a48dd   reiserfs                                 
/dev/sdb2        58cb03f5-1376-4614-9e9c-1ef68f5e1700   swap                                     
/dev/sdb3        92ca6a12-741c-4f8b-a579-ff8c91b951c0   reiserfs                                 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1210-114C                              vfat       VERBATIM                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        001E08B91E08A9AC                       ntfs       LaCie                         
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

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
default        10

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        15

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=178f3bbd-ca03-4573-a98d-3c66a91a48dd

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash 
initrd        /boot/initrd.img-2.6.32-26-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro  single
initrd        /boot/initrd.img-2.6.32-26-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-16-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-16-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-11-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-11-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd /               reiserfs notail,relatime 0       1
# /dev/sdb3
UUID=92ca6a12-741c-4f8b-a579-ff8c91b951c0 /home           reiserfs relatime        0       2
# /dev/sdb2
UUID=58cb03f5-1376-4614-9e9c-1ef68f5e1700 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2
    ??GB: boot/initrd.img-2.6.27-11-generic
    ??GB: boot/initrd.img-2.6.28-11-generic
    ??GB: boot/initrd.img-2.6.31-16-generic
    ??GB: boot/initrd.img-2.6.32-22-generic
    ??GB: boot/initrd.img-2.6.32-23-generic
    ??GB: boot/initrd.img-2.6.32-26-generic
    ??GB: boot/vmlinuz-2.6.27-11-generic
    ??GB: boot/vmlinuz-2.6.28-11-generic
    ??GB: boot/vmlinuz-2.6.31-16-generic
    ??GB: boot/vmlinuz-2.6.32-22-generic
    ??GB: boot/vmlinuz-2.6.32-23-generic
    ??GB: boot/vmlinuz-2.6.32-26-generic
    ??GB: initrd.img
    ??GB: initrd.img.old
    ??GB: vmlinuz
    ??GB: vmlinuz.old

============================= sdb3/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
# kopt=root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=178f3bbd-ca03-4573-a98d-3c66a91a48dd

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

title        Chainload into GRUB 2
root        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/grub/core.img

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sdb3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: grub/core.img
    ??GB: grub/menu.lst
    ??GB: grub/stage2
```Waiting for your instructions...:roll:

---

### Post by Quackers on 2011-03-25
Ok, so Windows boots ok, yes? Is that via a grub menu?

---

### Post by CydMM on 2011-03-25
Windows used to boot through Grub menu, exactly like used Kubuntu till I had to reinstall Win7.

Now nothing boots.

---

### Post by Quackers on 2011-03-25
Ah right, sorry :-)  I can't say I'm surprised by that!
Firstly, if you have 4 hard drives and none of those are usb drives, I would expect you to be able to choose all 4 drives as bootable devices. I'm not sure why you cant.
Next, in sda1 you have Windows XP boot files in with Windows 7 boot files, but you have no Windows XP system installed, apparently. You also have ?NTDETECT.COM in there too, which to my knowledge is usually a boot file for a recovery partition. grldr is also in there too, for good measure :-)
Ubuntu is installed in sdb, though Windows is shown as its bootloader, for some reason. You also appear to be using reiserfs as a file system for Ubuntu. Any reason for that?
You seem to have 2 Linux partitions (sdb1 and sdb3) yet neither appears to be a boot partition (which is fine, but not what you said earlier, I believe).

It is fixable I'm sure, but there are many inconsistencies.

---

### Post by CydMM on 2011-03-25
I really do not know how to answer to your questions, if I was able to I guess I wouldn't be here.
As regards the hard drives, as I already told you, my machine has only 2 hard drives installed. 1 Cd-rom drive. That's it.
As far as the disk with Linux is concerned, when I installed it I followed keen instructions from an expert who guided me step by step and I remember he suggested me to create more than one partition for the Linux hard drive but i do not remember the reasons and neither how I acted that. 

The only thing I can tell you is that everything worked fine till I had to reinstall Win7. Once switched the PC on, Grub used to show a menu with some choices between many "versions" of kubuntu and, at the end, the one for Windows.
But after selecting the Windows one, another Menu used to appear letting me choose between three options, one of which Win7, the other one I guess it was Winxp, the other I do not remember. I used to always choose the Win7 one and everything worked fine. Also for Linux choices.

Now, i really do not know how I can help you more than that

---

### Post by Quackers on 2011-03-25
Ok, thanks again.
The boot script says that you have the following drives
sda which is 300GB and has Windows 7 installed
sdb which is 500GB and has Ubuntu 10.04 installed
sdc which is 250GB and has one FAT32 partition only
sdd which is 1000GB and has one NTFS partition only

Are you saying that this is not correct?

---

### Post by CydMM on 2011-03-25
I am only saying that I have only 2 physical hard drives, and I am saying that because I directly purchased each component of my PC and had it assembled by a technician. So i perfectly know how many hard drives are in there.

So, how can we move along from this point? Is that possible?

---

### Post by CydMM on 2011-03-25
Hey my friend, sdd and sdc, as your script calls them are external Hard drives. Here its is the point :D

I was not even thinking of that. i believed you were referring only to internal ones. My God! ;)

Is that crucial for our aims? These two hard drives are used only for data storage, i have not installed any OS in them. The 1Tb one is a Lacie and the other one is a Verbatim.

---

### Post by Quackers on 2011-03-25
No, that's fine, no problem then.
What I suggest is to purge then re-install grub(2). It may work this way, but Windows may still need to be fixed later. We shall see :-)

Please boot from the Ubuntu (or Kubuntu, if that's what you've installed) live cd/usb and select "try (K)Ubuntu" and when the desktop loads connect to the internet.
Then open up a terminal and copy/paste the following lines in one line at a time, pressing enter after each line.
```
sudo mkdir /mnt/temp
sudo mount /dev/sdb1 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```
At this point the terminal prompt should change from ubuntu@ubuntu to root@ubuntu.
If it hasn't changed you missed something :wink:

If it has changed please follow all the instructions from number 2 to number 8 in the CHROOT section of the guide below.
#### NOTE when you get the option about where to install grub, choose /dev/sda by pressing the space bar as explained in the guide

(In step 7, you just need to use the first command - beginning "for i..........."not the second)
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

On rebooting Kubuntu should boot up directly.
If it does, open a terminal and type ```
sudo update-grub
``` and watch as grub.cfg is run to see if the Windows Loader for sda1 is found. If it is, reboot and choose Windows from the grub menu, to see if it loads.
Take care, good luck :-)
If you get stuck, just post here again.

---

### Post by CydMM on 2011-03-25
Thank you my friend, I hope I will be able to correctly follow your keen instructions :D.

Let' keep fingers crossed ;-)

Let's go at work...I will let you know soonest :-)

---

### Post by Quackers on 2011-03-25
I'll be waiting for good news :-)

---

### Post by CydMM on 2011-03-25
Only a question....I am booting from a Ubuntu CD Live, while I have installed Kubuntu on the PC.

Is that a Problem? :-/

---

### Post by Quackers on 2011-03-25
If both are a recent version, say 10.04, that will be ok.

---

### Post by CydMM on 2011-03-25
Good.

thanks again :D. I'll BRB with good news I hope ;-)

---

### Post by CydMM on 2011-03-25
\\:D/\\:D/ Hi my friend!!! =D>=D>
 
My congratulations to you! Everything just worket out brilliantly. Thank you!
 
Now Bot Kubuntu and Win7 do boot perfectly.
 
There is only one weird stuff left....once chosen the Windows7 option on Grub 2 window...a new window with some sort of Windows loader opens up (like before this mess) and three options are provided:
1) Earlier version of Windows
2) Windows 7
3) Microsoft Windows XP
 
How do you think we can just avoid this additional "loader" and directly jump to Win7 if so chosen from Grub2 window?

---

### Post by Quackers on 2011-03-25
Oh happy day :-)

I would suggest this.
Boot Windows 7 and from its root delete the following files/folders (or alternatively cut/paste them to somewhere else)
/boot.ini
/grldr
/ntldr
/NTDETECT.COM

These files/folders may be in the boot folder of Windows root.
After moving these files, reboot and choose Kubuntu, then open a terminal and run ```
sudo update-grub
```and check that only the Windows Loader for sda1 is found.
This step may not be required, but it won't do any harm.
Then reboot and choose Windows 7 from the grub menu and see if the second Windows menu has disappeared.

---

### Post by CydMM on 2011-03-25
I am not able to find those files anywhere in the root of win7. There is a Boot folder under Windows folder but it doesn't cointain any of those files :confused:

---

### Post by Quackers on 2011-03-25
Is there a file called BCD in that folder?
Please post a screenshot of the root and the boot folder, if unsure.

---

### Post by CydMM on 2011-03-25
My friend, I have to leave now. I Will check tomorrow morning and I Will get back to you. Thank you. See u tomorrow. Bye :-)

---

### Post by Quackers on 2011-03-25
Ok, have fun :-)  Bye

---

### Post by CydMM on 2011-03-26
Hi, there is not any BCD folder in the Boot subfolder of C:\Windows.

There are some files spread all over Windows directory and some subfolders, files that contain BCD in their names but no folders with that name

---

### Post by Quackers on 2011-03-26
Good morning :-)
What do you mean by Windows directory?
If you click on Start then Computer then double-click on the C: drive do you see a folder called boot? What is in that folder please?

EDIT The names you are looking for can be files, not folders

---

### Post by CydMM on 2011-03-26
Good Morning to you my friend :D

There is not any Boot folder in the root. The only Boot folder is C:\Windows\Boot\ but it doesn't contain any BCD subfolder

---

### Post by Quackers on 2011-03-26
In Windows you should see a window like this

---

### Post by CydMM on 2011-03-26
Here it is my root

---

### Post by CydMM on 2011-03-26
You know what my friend?

When I re-installed Win7, I tried to boot from DVD but the screen showed a splash image with anything else so...I had no chunce but to re-boot normally and launch the re-install from inside Windows. So I guess the new install only completely chenged and replaced the old System files and folders (and the old OS was put under the*.ol folder) but all the rest is the same.

Maybe this is the reason why I still encounter these weird behaviour on Win boot and strange folders.

Do you think I should try again to make a real fresh install formatting the drive where Windows is installed and, therefore, doing again the Grub procedure we made yesterday?

---

### Post by Quackers on 2011-03-26
There shouldn't be any need for that. If Windows is running ok, it should be fine.
Please try this, click on Start then right-click on Computer and select "run as administrator". Do you now see a different window, with boot folder and others?

---

### Post by CydMM on 2011-03-26
There is not the option "Run as Administrator" but the only relevant option is the one with the shield which leads to Administration Tools.

---

### Post by Quackers on 2011-03-26
Sorry, it's been a while since I used Windows 7. Click Start, then Computer, then right-click on the C: drive and select "run as administrator" - maybe :-)

---

### Post by CydMM on 2011-03-26
Sorry my friend but neither right-clicking on C: drive "run as administrator" is offered as an option...the relevant option is just possibility to activate BitLocker.....

---

### Post by Quackers on 2011-03-26
Oh dear, it seems my memory is failing - it must be my age!
We'll do it from within Ubuntu. Please boot into Ubuntu. There should be an entry in the Places menu for Windows, please click on that and it should show on your desktop as a HDD symbol. Open that and you should see a window like the one I posted earlier. A screenshot will give us details.

---

### Post by CydMM on 2011-03-26
Ok. don't move....I am switching to Linux ;-)

---

### Post by Quackers on 2011-03-26
Like a marble statue :wink:

---

### Post by CydMM on 2011-03-26
Here I am my friend .-)

So I got a screen-capture of the Root content, you will see that now this Boot folder is shown and, on the right the content of this folder. All the sub-folders that are not visible on the latter window are just those from any language possible of windows.

---

### Post by Quackers on 2011-03-26
Please expand the left hand screenshot, so that all folders and files can be seen. They could be in there. Or have a look through that window for the file names I gave earlier.

---

### Post by CydMM on 2011-03-26
Sorry for my late answer but my girlfriend decided to call me just now!! ;-)

Ok man, the files are all there!!! What shall I do?

---

### Post by Quackers on 2011-03-26
Aha! :-)
I would suggest that if they are all in one folder (maybe grub?) cut and paste that folder to somewhere else - like the documents folder, for instance.
If they are separate files, cut/paste each one that I mentioned earlier to the documents folder, or a folder of your choice.

When that's done for all files, open up a terminal and run ```
sudo update-grub
```
then reboot and choose Windows from the grub menu. Hopefully you won't see a second menu.

---

### Post by CydMM on 2011-03-26
:(

Nothing changed my friend. I placed all those files in another folder, in an external disc but....nothing changed

---

### Post by Quackers on 2011-03-26
Did you run sudo update-grub?
Please re-run the boot info script and post the results. Thanks.

---

### Post by CydMM on 2011-03-26
Yes I did.

Ok.

---

### Post by CydMM on 2011-03-26
this time, after having saved the script on the Desktop and having run the command on Terminal, here it follows the message I received:

```
marco@MM:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/marco/Desktop/boot_info_script*.sh: Nessun file o directory

```

---

### Post by Quackers on 2011-03-26
Does the script file appear on the desktop?

---

### Post by CydMM on 2011-03-26
Unfortunately it doesn't. The desktop is empty. You know what? Since when I made an update of Kubuntu some time ago, I am nomore able to minimize windows: I am compelled to close them if I want to see the Desktop :-(

Maybe after I installed CompizFusion update

---

### Post by Quackers on 2011-03-26
From a terminal try ```
compiz --replace
```

---

### Post by CydMM on 2011-03-26
This is what I received after launching that command

```
marco@MM:~$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting kde4-window-decorator
compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
kde-window-decorator(2045) KWD::KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_oxygen.so"  for  "kwin3_oxygen"
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
KCrash: Application 'kde4-window-decorator' crashing...
sock_file=/home/marco/.kde/socket-MM/kdeinit4__0
compiz (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
compiz (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
compiz (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
compiz (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
compiz (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
compiz (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.

```

---

### Post by Quackers on 2011-03-26
Which window manager are you using? metacity --replace, if you are using metacity - I am not familiar with Kubuntu :-)
Anyway, if the boot script has been downloaded, find out where it is - maybe in Downloads.
Change the command to
```
sudo bash ~/Downloads/boot_info_script*.sh
``` for instance.

The results.txt file would then be in Downloads too.

---

### Post by CydMM on 2011-03-26
You know what my friend?

I am transferring a folder of files from Linux to one external hard drive, it is an old big backup. Once this will be made, I would change from Kubuntu to Ubuntu.

What do you think? I like Ubuntu most and when I chase for Kubuntu it was just for silly graphical and "appearance" motivations that, all considered, are not worth.

What do you believe about that? Would you help me in the transition to Ubuntu and maybe also finalizing the problem of the Windows boot?

---

### Post by Quackers on 2011-03-26
If you want to, you can just over-write Kubuntu with Ubuntu, by using the same partitions as Kubuntu is now using, during the installation.
If you can run the boot script we will be able to see what files are still in sda1 that shouldn't be (if any).

---

### Post by CydMM on 2011-03-26
I have Dolphin, and it shows the script on the Desktop. So I don't understand why the command at the Terminal is not working out

---

### Post by Quackers on 2011-03-26
I don't know why that may be either.

---

### Post by CydMM on 2011-03-26
Ah AH Ah my friend!!! :D

It's natural that the command you told me to use will never work out in my system because the folder names here are in Italian language ;-)

I am posting the result of the script :popcorn:

---

### Post by CydMM on 2011-03-26
Here it is

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/core.img /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 300.1 GB, 300069052416 byte
255 testine, 63 settori/tracce, 36481 cilindri, totale 586072368 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   586,070,015   586,067,968   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 500.1 GB, 500107862016 byte
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    97,659,134    97,659,072  83 Linux
/dev/sdb2          97,659,135   107,426,654     9,767,520  82 Linux swap / Solaris
/dev/sdb3         107,426,655   498,047,129   390,620,475  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 250.1 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri, totale 488397168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disco /dev/sdd: 1000.2 GB, 1000204886016 byte
255 testine, 63 settori/tracce, 121601 cilindri, totale 1953525168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C0308C6A308C68EC                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        178f3bbd-ca03-4573-a98d-3c66a91a48dd   reiserfs                                 
/dev/sdb2        58cb03f5-1376-4614-9e9c-1ef68f5e1700   swap                                     
/dev/sdb3        92ca6a12-741c-4f8b-a579-ff8c91b951c0   reiserfs                                 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1210-114C                              vfat       VERBATIM                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        001E08B91E08A9AC                       ntfs       LaCie                         
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        reiserfs   (rw,relatime,notail)
/dev/sdb3        /home                    reiserfs   (rw,relatime)
/dev/sdd1        /media/LaCie             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        15

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=178f3bbd-ca03-4573-a98d-3c66a91a48dd

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash
initrd        /boot/initrd.img-2.6.32-26-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single
initrd        /boot/initrd.img-2.6.32-26-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-16-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-16-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-11-generic
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro quiet splash
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-11-generic (recovery mode)
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
insmod reiserfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
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
insmod reiserfs
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
set locale_dir=($root)/boot/grub/locale
set lang=it
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
menuentry 'Ubuntu, con Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-26-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    echo    'Caricamento Linux 2.6.32-26-generic...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-23-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    echo    'Caricamento Linux 2.6.32-23-generic...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    echo    'Caricamento Linux 2.6.32-22-generic...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.31-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, con Linux 2.6.31-16-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    echo    'Caricamento Linux 2.6.31-16-generic...'
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, con Linux 2.6.28-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-11-generic
}
menuentry 'Ubuntu, con Linux 2.6.28-11-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    echo    'Caricamento Linux 2.6.28-11-generic...'
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.28-11-generic
}
menuentry 'Ubuntu, con Linux 2.6.27-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    linux    /boot/vmlinuz-2.6.27-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.27-11-generic
}
menuentry 'Ubuntu, con Linux 2.6.27-11-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    echo    'Caricamento Linux 2.6.27-11-generic...'
    linux    /boot/vmlinuz-2.6.27-11-generic root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.27-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod reiserfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 178f3bbd-ca03-4573-a98d-3c66a91a48dd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0308c6a308c68ec
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd /               reiserfs notail,relatime 0       1
# /dev/sdb3
UUID=92ca6a12-741c-4f8b-a579-ff8c91b951c0 /home           reiserfs relatime        0       2
# /dev/sdb2
UUID=58cb03f5-1376-4614-9e9c-1ef68f5e1700 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg
    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2
    ??GB: boot/initrd.img-2.6.27-11-generic
    ??GB: boot/initrd.img-2.6.28-11-generic
    ??GB: boot/initrd.img-2.6.31-16-generic
    ??GB: boot/initrd.img-2.6.32-22-generic
    ??GB: boot/initrd.img-2.6.32-23-generic
    ??GB: boot/initrd.img-2.6.32-26-generic
    ??GB: boot/vmlinuz-2.6.27-11-generic
    ??GB: boot/vmlinuz-2.6.28-11-generic
    ??GB: boot/vmlinuz-2.6.31-16-generic
    ??GB: boot/vmlinuz-2.6.32-22-generic
    ??GB: boot/vmlinuz-2.6.32-23-generic
    ??GB: boot/vmlinuz-2.6.32-26-generic
    ??GB: initrd.img
    ??GB: initrd.img.old
    ??GB: vmlinuz
    ??GB: vmlinuz.old

============================= sdb3/grub/menu.lst: =============================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
# kopt=root=UUID=178f3bbd-ca03-4573-a98d-3c66a91a48dd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=178f3bbd-ca03-4573-a98d-3c66a91a48dd

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

title        Chainload into GRUB 2
root        178f3bbd-ca03-4573-a98d-3c66a91a48dd
kernel        /boot/grub/core.img

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sdb3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: grub/core.img
    ??GB: grub/menu.lst
    ??GB: grub/stage2
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo0/sdc1: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

---

### Post by Quackers on 2011-03-26
ROFL, that would do it :-)
Ok, sda1 looks good now :-)
However, I see that both sdb1 and sdb3 still have a /boot/grub/menu.lst file in them. I would recommend deleting both of those files (just the menu.lst file!)
Then run sudo update-grub again (in Italian, maybe) :-)
I suspect that the Windows bootmgr may have something to do with your Windows menu, but, sadly, I don't know how to change that. I have never had to do that before.
Maybe if somebody else has seen anything similar they can make a suggestion for you.

---

### Post by Quackers on 2011-03-26
There is also something else that is troubling me.
The boot script says
```
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
```
But this isn't strictly true. Partition 1 on sda is the Windows partition. Grub2 should be looking at partition 1 on sdb for its boot files.
I've seen this before on my system, but, as with yours, it still boots Ubuntu ok.
It's not normal though.

---

### Post by CydMM on 2011-03-26
How can I delete those two files?

---

### Post by Quackers on 2011-03-26
Just before we go that far, is it your intention to over-write your kubuntu installation with Ubuntu?
Another question
You have confirmed, I think, that only the 300GB drive appears as a boot device in your bios. I am thinking that this may be the case because your sdb drive has no boot flag set on it. Some bioses won't boot a drive that has no boot flag.
So, before you install Ubuntu, if that is your intention, please open a terminal and install gparted, if you haven't installed it already.
```
sudo apt-get install gparted
``` then go to System > Admin > gparted
When gparted opens up it will display the /dev/sda drive. Near the top on the right is a small box which will show /dev/sda. Click on the little arrow next to it and select /dev/sdb from the drop-down box.
The display will now show your sdb partitions.
Right-click on sdb1 and select "manage" and in the new window click on the box marked "boot". Then, if necessary click on the green tick mark in the toolbar to apply the change.
Then quit gparted and shutdown. Then start the machine and enter the bios and see if the 500GB drive is now a bootable device.

---

### Post by CydMM on 2011-03-26
I attended all the tasks you asked me to :-)

I just realized from the Bios that the procedure to select the hard drive to boot is a two-step one. First one shall choose the priority between all the hard drives detected, both IDE, SATA and USB, than in another window, not linked, one shall choose the boot priority between the first hard drive from the previous option and other devices (floppy...CD-R...)

So I don't know if also before these actions we just made it was already ok but...now for sure both hard drives can be selected for boot :-)

---

### Post by Quackers on 2011-03-26
Aha! :-) That's good!
So the first hard drive is the frist bootable device at the moment.
What I would suggest now, is to replace grub in sda with the Windows bootloader.
Then, after making sure Windows boots ok, I would suggest choosing the 500GB drive as first bootable device then install Ubuntu in the same partitions that Kubuntu is now using, installing grub to SDB - NOT sda.
That way, the Windows bootloader remains untouched by grub, yet grub2 will still be able to boot Windows from sdb.
We may also be able to get rid of the dodgy second Windows menu this way.
Does that sound agreeable?

---

### Post by CydMM on 2011-03-26
It sounds nice :-)

But I have only one condition.....:guitar:

which is....that you will guide me step by step through all that.

:-)

---

### Post by Quackers on 2011-03-26
I've got nothing else to do :-)

I take it that you've got an Ubuntu live cd or usb?

Ok, so put your Windows installation disc in the drive then boot from it.
Press the necessary keys as required to get to the recovery console.
When the recovery console opens it may offer a startup repair, just let it run then choose near the bottom left the advanced options (or similar)
Choose the Command Prompt option
In the command prompt window type in
```
bootrec.exe /RebuildBCD
```  ## Note the space after exe and before /RebuildBCD
When that's run it may offer you the chance to add an entry to the BCD store - just answer Y for yes.

Then in the command prompt window enter
```
bootrec.exe /fixmbr
``` and hit enter. ## Note the space after exe and before /fixmbr.
If that runs ok, reboot and Windows 7 should, hopefully, boot directly - no menu.

If all is well please report back here - then we can install Ubuntu to sdb.

---

### Post by CydMM on 2011-03-26
Ok :-)

So before doing that I shall change the Bios selectiong the 500Gb drive as the bootable one?

---

### Post by Quackers on 2011-03-26
No, that's for later. Leave the 300GB drive selected for now

---

### Post by CydMM on 2011-03-26
Good. Last question.

I have a Quadcore processor....better the x64 or x32 for Ubuntu?

---

### Post by Quackers on 2011-03-26
I use 64 bit, but whatever you've got should be good.

---

### Post by CydMM on 2011-03-26
Also I use to install 64bit (Win7 is x64 in my machine).

But I need 3 hours to download now the x64 and burn CD.

EIther we catch up later with x64 platform or we do that now with the x32 one.

What do you prefer? It's not a problem for me to come back in 3 hours and a half but it's up to you my friend

---

### Post by Quackers on 2011-03-26
No, that's fine. There's no point installing what you don't want.
Can you download it while fixing the Windows 7 drive? Or are you using the same computer?

Which version are you downloading? 10.04?

---

### Post by CydMM on 2011-03-26
I cannot because I am using the same computer. I switched to win 7 and I am now downloading at 900Kb/s...while on Linux I was at 60k/s ;-) Mmmm...bad  bad for the open-source this time. :-)

In half an hour I should be ready for fixing the win 7 drive

yes. i am downloading the 10.10. Is there a newer one?

---

### Post by Quackers on 2011-03-26
Ok, if you're downloading 10.04 ???? (are you?) I'll check the installer for defining where grub is installed. I can't remember :-(

---

### Post by CydMM on 2011-03-26
No No. I am installing **10.10**

---

### Post by Quackers on 2011-03-26
Ok, no problem.
I'll be back :-)

---

### Post by CydMM on 2011-03-26
Ok :)

---

### Post by CydMM on 2011-03-26
I tried to boot with Win7 DVD but after the screen showing the message....**installing files**....then the splash logo and the message** starting Windows**.....the background image appears and the arrow of the mouse but nothing more happens. I had to press the button of the PC to reboot

---

### Post by Quackers on 2011-03-26
Is that definitely a Windows installation disc, or could it be a recovery disc?
Do you have a repair disc? You can make one in Start > Control Panel > Backup & Restore Centre then in the left pane select "make a recovery cd"

---

### Post by CydMM on 2011-03-26
this is an installation disc. I am burning a repair one then

---

### Post by Quackers on 2011-03-26
Ok, but it's strange!

---

### Post by CydMM on 2011-03-26
DOne. SO I follow the same procedure?

---

### Post by CydMM on 2011-03-26
Yes it is

---

### Post by Quackers on 2011-03-26
Yes, same procedure.

---

### Post by CydMM on 2011-03-26
I followed your instructions but after having prompted the command 

```
bootrec.exe /RebuildBCD
```

I received the following message inside the prompt:

Successfully scanned Windows installations.
Total identified installations: 0
The operation completed suffessfully

And the Command Prompt remained waiting for my instructions.

:confused:

---

### Post by Quackers on 2011-03-26
And the Windows drive was left as first boot device (after cd drive)?
Strange. Run the fixmbr then please.

---

### Post by CydMM on 2011-03-26
Done, but with no results. Like before. after fixmbr The prompt said that operation was successfull but the prompt remained like that. And after rebooting naturally grub is disappeared but not the Windows loader :-(

A weird thing....during the recovery...a window showed the partition where the Win 7 installation is located and...it showed it was on C but with a dimension of around 270GB !!!

:confused:

---

### Post by Quackers on 2011-03-26
So you are still getting a Windows menu to choose XP or Windows 7?
How big is your Windows partition? It's about that size isn't it?

---

### Post by CydMM on 2011-03-26
Yes, I am still getting a Windows menu to choose XP or Windows 7 or an earlier versione of operating system. Three chioces.

As regards the win partition it is approximately close to that number

---

### Post by Quackers on 2011-03-26
Please try something for me.
Boot from the repair cd again please. Once in the recovery environment you should get an option to "repair my computer". Did you see that before?
Click on that option and you should see your Windows 7 system appear as an option in the window. Click on Windows 7 and click on next.
(If the Windows 7 option is not listed in that window then something is wrong, probably with BCD. It should find Win 7 as an option).
Let the repair run and then choose the command prompt option and run the rebuildbcd and fixmbr commands again please. See if anything different is reported for the rebuildbcd option. Thanks.

---

### Post by CydMM on 2011-03-26
I did what you asked and, as I told you before, Win 7 is shown insie that window from the repair environment.
I followed the instructions, I prompted again those two command but nothing to do.

It's crazy

---

### Post by CydMM on 2011-03-26
If it was possible to boot from the Installation disc (not from the repair one) I would format that damned disc and make a new, fresh install of Win7 there :mad:

---

### Post by Quackers on 2011-03-26
Well we tried!
We can look for a fix for that later. We should now install Ubuntu :-)

Please go back into your bios and set the cd drive as the first boot device, then the 500GB (Ubuntu) drive as second boot device and the 300GB Windows drive as third boot device.

Then reboot with the Ubuntu live cd in the cd drive.

At the first screen choose to "try Ubuntu" rather than "install ubuntu", so that we can see if it runs ok to a desktop (10.10 is different to other versions and has problems with some hardware - particularly graphics).
If the desktop loads ok you can connect to the internet (if you wish to download updates during the installation) and then click on the "install" icon on the desktop.

Fill in the details of the first screen or two until you get to the screen for partitioning. It will have the top option (use entire disk) selected. You must choose "specify manually" at this time (the third option, I think).
This will bring you to the screen below

On that screen scroll down slightly until your sdb1 partition is shown then double-click on it. A new window will open. Leave the size as before. Choose partition type as ext4 and tick the box to format it.
Choose the mount point as "/" for root, then click on OK.

Then scroll to the sdb3 partition and double-click on that. In the new window do the same as above, except for mount point choose /home from the drop-down menu, then click on OK.

At the bottom of that screen you will see "Boot Loader"
"device for bootloader installation"
You MUST click on the little arrow on the right and select /dev/sdb, the 500GB drive.
We don't want grub in /dev/sda this time!
Then, when you're happy, click on "install now" and confirm in the next screen.
Then off it goes, installing.

After installation it should ask for a reboot. Don't worry if Ubuntu boots directly without a menu. It should do.

Speak again later, unless you have any problems :-)

---

### Post by CydMM on 2011-03-26
Hi my friend :D.

Ubuntu 10.10 just correctly installed. I don't know if it might be useful for you but I launched that script in order to see how the situation is now. Here follows the result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 300.1 GB, 300069052416 byte
255 testine, 63 settori/tracce, 36481 cilindri, totale 586072368 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   586,070,015   586,067,968   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 500.1 GB, 500107862016 byte
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    97,659,134    97,659,072  83 Linux
/dev/sdb2          97,659,135   107,426,654     9,767,520  82 Linux swap / Solaris
/dev/sdb3         107,426,655   498,047,129   390,620,475  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 250.1 GB, 250059350016 byte
255 testine, 63 settori/tracce, 30401 cilindri, totale 488397168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disco /dev/sdd: 1000.2 GB, 1000204886016 byte
255 testine, 63 settori/tracce, 121601 cilindri, totale 1953525168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C0308C6A308C68EC                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5cf0befc-96da-4ebf-9f8f-3e7a17b46767   ext4                                     
/dev/sdb2        58cb03f5-1376-4614-9e9c-1ef68f5e1700   swap                                     
/dev/sdb3        600452ed-bc21-44bc-b24b-398db901d362   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1210-114C                              vfat       VERBATIM                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        001E08B91E08A9AC                       ntfs       LaCie                         
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb3        /home                    ext4       (rw,commit=0)
/dev/sdc1        /media/VERBATIM          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdd1        /media/LaCie             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
set locale_dir=($root)/boot/grub/locale
set lang=it
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5cf0befc-96da-4ebf-9f8f-3e7a17b46767 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5cf0befc-96da-4ebf-9f8f-3e7a17b46767 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c0308c6a308c68ec
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sdb3       /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=58cb03f5-1376-4614-9e9c-1ef68f5e1700 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  10.9GB: boot/grub/core.img
   6.6GB: boot/grub/grub.cfg
  48.0GB: boot/initrd.img-2.6.35-22-generic
  10.9GB: boot/vmlinuz-2.6.35-22-generic
  48.0GB: initrd.img
  10.9GB: vmlinuz
```

Once rebooted the PC after installation....Grub2 appeared with its menu...including Windows 7 ;-)
Selecting that one, we jump to the other bootloader like before.

---

### Post by Quackers on 2011-03-26
Ok that looks good. Much tidier without all those menu.lst files :-)
Ok, I thought of something for the Windows menu, maybe!
If you boot into Windows I'll do the same and see you in 5.

---

### Post by CydMM on 2011-03-26
Give me 10 at least because my Ubuntu is installing updates :-)

---

### Post by CydMM on 2011-03-26
Here I am :)

---

### Post by Quackers on 2011-03-26
Ok, I'm in Windows 7 now.
No problem, take your time.

If you hold down the Windows key (next to Alt) and press the R key, a run dialogue box will open up. Type in msconfig and press enter.
In the new window click on the Boot tab.
Yours should show 3 entries, Windows 7, Windows XP and previous version.
Make Windows 7 the default option (if it isn't the top one already), by highlighting it then clicking on the "Set as default" box underneath.
Then highlight the next one down and then click on the "Delete" box underneath.
Then highlight the last one and click on the "delete" box underneath.

Then go back to the first tab (General) and click on the Apply box, then on the OK box, to close it. You may get a box appearing now or on the next boot, to say that a configuration change has taken place. You should accept that change and, if necessary, tick the box for the message not to show again.
Then reboot and see if the extra Windows menu is gone. You may need to reboot twice.
Good luck :-)

---

### Post by CydMM on 2011-03-26
Sorry but...opening Msconfig didn't resulted in showing under Boot tab what we expected my friend....I made two screen-captures to show you the content of two tabs...one is the Boot Options and the other one is Boot....all the options inside the Boot Options tab are not clickable.

---

### Post by CydMM on 2011-03-26
sorry...I pressed "submit reply" before attaching files :-)

---

### Post by Quackers on 2011-03-26
I see no screenshots :-)
Aha, they appeared!

---

### Post by Quackers on 2011-03-26
Oh dear, something is wrong! :confused:
Here is a screenshot of my msconfig > Boot tab

---

### Post by CydMM on 2011-03-26
Oh my God!!

This really drives me nuts!! :-s

The strange thing, if it was not enough the absence of any entry inside that tab, is the total impossibility to click those buttons.

---

### Post by Quackers on 2011-03-26
Yes, unless there is an entry to click on in the main window, those buttons won't be clickable.
There have been a few mysteries along the way. The Windows cd should have found the BCD, but it did not. Now, msconfig doesn't find the same thing. It seems it just isn't there! Which also brings up another question! How is Windows booting without one? I don't know.
Maybe a Windows 7 expert will see this thread and give us an idea :-)

For now, I think I have exhausted my knowledge :-(
If I think of anything I will send you a private message :-)

Alternatively, as grub is now installed on sdb, you can re-install Windows 7 on sda without affecting grub :-)  So if you get the dvd booting again you can have a go :-)

---

### Post by CydMM on 2011-03-26
I understand my friend. Thank you so much for your help!! :-)

So I could re-install Windows Seven on its disk without affecting the Grub we just fixed?

---

### Post by Quackers on 2011-03-26
Yes, that was one of the advantages of doing it that way. Both operating systems are now bootable independently of each other, by changing the boot order in bios.
As long as you are careful about where grub is installed in future (not sda), you can re-install everything if you want to, and it shouldn't affect the other system.

You're welcome :-) Enjoy yourself :-)

---

### Post by Quackers on 2011-03-26
You don't have EasyBCD installed in Windows do you?

And if you're happy, would you mark the thread as solved please, using the Thread Tools tab near the top of the page. It may help others when searching.
Thanks.

---

### Post by CydMM on 2011-03-27
Good Morning my friend :D

I succeeded to make a clean install of Windows 7 x64 !! It works out brilliantly :D

Now, naturally, there is nomore any boot menu and I directly arrive to Win7.

So my friend, now we should have succeeded to get rid of that Winloader that seemed like to be everlasting ;-)

But now, would you explain to me the correct, exact procedure to establish a new, unique, bootloader through which I can easily decide which OS to boot?

---

### Post by CydMM on 2011-03-27
I just run the script you gave me. Here it is the result :-)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   586,070,015   586,067,968   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    97,659,134    97,659,072  83 Linux
/dev/sdb2          97,659,135   107,426,654     9,767,520  82 Linux swap / Solaris
/dev/sdb3         107,426,655   498,047,129   390,620,475  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0C3EACA33EAC86F4                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5cf0befc-96da-4ebf-9f8f-3e7a17b46767   ext4                                     
/dev/sdb2        58cb03f5-1376-4614-9e9c-1ef68f5e1700   swap                                     
/dev/sdb3        600452ed-bc21-44bc-b24b-398db901d362   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1210-114C                              vfat       VERBATIM                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        001E08B91E08A9AC                       ntfs       LaCie                         
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
set locale_dir=($root)/boot/grub/locale
set lang=it
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=5cf0befc-96da-4ebf-9f8f-3e7a17b46767 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=5cf0befc-96da-4ebf-9f8f-3e7a17b46767 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5cf0befc-96da-4ebf-9f8f-3e7a17b46767 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5cf0befc-96da-4ebf-9f8f-3e7a17b46767 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5cf0befc-96da-4ebf-9f8f-3e7a17b46767
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c0308c6a308c68ec
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sdb3       /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=58cb03f5-1376-4614-9e9c-1ef68f5e1700 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  10.9GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
   1.0GB: boot/initrd.img-2.6.35-28-generic
  10.9GB: boot/vmlinuz-2.6.35-22-generic
    .7GB: boot/vmlinuz-2.6.35-28-generic
   1.0GB: initrd.img
    .9GB: initrd.img.old
    .7GB: vmlinuz
  10.9GB: vmlinuz.old
```

---

### Post by Quackers on 2011-03-27
Did you change the bios boot order so that the Windows drive is first?
Change it back so that the 500GB drive is bootable before the 300GB drive and when Ubuntu loads open a terminal and run ```
sudo update-grub
```

---

### Post by CydMM on 2011-03-28
Everything is working out perfectly. Thanks for your help. :)

---

### Post by Quackers on 2011-03-28
You're welcome :-)
Please mark the thread as solved, using the Thread Tools near the top of the page. It may help others when searching.

---

