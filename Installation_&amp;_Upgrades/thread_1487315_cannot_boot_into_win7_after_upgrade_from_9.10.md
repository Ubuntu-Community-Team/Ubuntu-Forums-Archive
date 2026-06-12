---
title: "cannot boot into win7 after upgrade from 9.10"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by komoku on 2010-05-18
Hello everyone... so I had 9.10 installed for a long time as a dual boot with win7 on this computer. I mostly use win7, but today i went into ubuntu and it said there was a new version available so i installed it.

the error occured with the grub installation. it said if i was unsure of where to install it, i should install it on all drives, so I did. ever since then i've been looking online using this liveCD to find some solution to fix the problem, but I cant.

here is what i've tried:

1. i downloaded a windows 7 repair disc and used the bootrec.exe /fixboot and /fixmbr commands, but this ends up with a blank screen with a cursor blinking.

2. I've tried re-installing grub, but this ends with the boot freezing at a screen with something like: "sh:grub>" and i can't do anything.

3. I've tried testdisk but this also didn't work for me.

i've been trying to fix this problem for 7 hours now... but nothing... so i'm hoping maybe someone here would help my specific situation out.

for some information on my system, here is my fdisk -l output:

> ```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6d040ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33177   266485760    7  HPFS/NTFS
/dev/sda2           33177       36988    30611456    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           36988       38914    15471448   12  Compaq diagnostics
/dev/sda5           33177       36988    30610432    7  HPFS/NTFS
```the current status of my computer: i have uninstalled grub in sda1 and sda5 (my ubuntu should be in sda5) and i used the windows7 repair CD to /fixboot and /fixmbr, so now when i boot, it freezes at a blank screen with a blinking cursor. anyone can help me, please?

---

### Post by komoku on 2010-05-18
hello again. i have some more information for anyone that can help me. here is my boot info script output:

> ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 12072336 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 11047096 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda3 has 30722047 sectors, but according to the info 
                       from fdisk, it has 30942895 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa6d040ca

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   532,973,567   532,971,520   7 HPFS/NTFS
/dev/sda2         532,975,616   594,198,527    61,222,912   f W95 Ext d (LBA)
/dev/sda5         532,977,664   594,198,527    61,220,864   7 HPFS/NTFS
/dev/sda3         594,198,528   625,141,423    30,942,896  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       18ca5a4b-cdd4-4a8c-962d-3171943fbb66   ext4                                     
/dev/sda1        CA2CDF592CDF3EDF                       ntfs                                     
/dev/sda3        1A2E21902E2165CB                       ntfs                                     
/dev/sda5        54EAE1DAEAE1B7FE                       ntfs       Lenovo                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda3        /media/1A2E21902E2165CB  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=================== sda5: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

======================== sda5/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ca2cdf592cdf3edf
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1a2e21902e2165cb
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


   6.1GB: boot/grub/core.img
   1.8GB: boot/grub/grub.cfg
   1.8GB: boot/initrd.img-2.6.31-19-generic
   7.0GB: boot/initrd.img-2.6.32-22-generic
   2.8GB: boot/vmlinuz-2.6.31-19-generic
   1.5GB: boot/vmlinuz-2.6.32-22-generic
   7.0GB: initrd.img
   1.5GB: vmlinuz
```

---

### Post by bcbc on 2010-05-18
You have a wubi install (installed within windows) - so you shouldn't reinstall the grub bootloader. You need the windows bootloader as it is now.

Since the testdisk didn't work, you'll have to try the bootsect /fixboot again.

Some people have had success with [this link]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD") as well.

---

### Post by komoku on 2010-05-19
> **bcbc said:**
> You have a wubi install (installed within windows) - so you shouldn't reinstall the grub bootloader. You need the windows bootloader as it is now.

Since the testdisk didn't work, you'll have to try the bootsect /fixboot again.

Some people have had success with [this link]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD") as well.

hi, when i previously attempted to use the /rebuildbcd command within the win7 recovery disk, it attempted to find windows installations and it found 0. i remember reading on some forum that this could be caused by having a linux operating system installed along with windows, which is the case with my computer. i don't know how to get the command prompt to recognize my windows 7...

also, a few general questions: 

1. can i uninstall ubuntu from my sda5 with a liveCD?

2. if i uninstall the ubuntu on my computer, could this fix my problem since ubuntu and grub will no longer be the first thing my computer goes to when booting?

---

### Post by bcbc on 2010-05-19
> **komoku said:**
> hi, when i previously attempted to use the /rebuildbcd command within the win7 recovery disk, it attempted to find windows installations and it found 0. i remember reading on some forum that this could be caused by having a linux operating system installed along with windows, which is the case with my computer. i don't know how to get the command prompt to recognize my windows 7...

also, a few general questions: 

1. can i uninstall ubuntu from my sda5 with a liveCD?

2. if i uninstall the ubuntu on my computer, could this fix my problem since ubuntu and grub will no longer be the first thing my computer goes to when booting?

1. No. There is no uninstall. You can just delete the partition or reformat it if you want to remove ubuntu and use it for windows.

2. No. Removing/reinstalling ubuntu doesn't help windows. The problem is due to overwriting the windows boot sector thanks to a confusing grub installation program. So you need to repair windows.

For some reason many people have recovered easily from this by using the testdisk solution mentioned earlier (or bootsect /fixboot), but there are some where this doesn't work. I have no idea why.

I've also heard it said that you should try the win7 repair process multiple times. Honestly I don't know since I haven't gone through it, but I believe windows should be able to repair itself.

---

### Post by komoku on 2010-05-19
> **bcbc said:**
> 1. No. There is no uninstall. You can just delete the partition or reformat it if you want to remove ubuntu and use it for windows.

2. No. Removing/reinstalling ubuntu doesn't help windows. The problem is due to overwriting the windows boot sector thanks to a confusing grub installation program. So you need to repair windows.

For some reason many people have recovered easily from this by using the testdisk solution mentioned earlier (or bootsect /fixboot), but there are some where this doesn't work. I have no idea why.

I've also heard it said that you should try the win7 repair process multiple times. Honestly I don't know since I haven't gone through it, but I believe windows should be able to repair itself.

as i mentioned in the first post, i've been at this for 7+ hours, so over that time i've tried the win7 repair process multiple times with no success (i'd say i've tried it maybe 5-6 times by now). the link you posted previously seems to rely on the /rebuildbcd command as the main way to fix the problem, but i cannot use that command since the CD doesn't find any windows installations. so i fear if i attempt those instructions (specifically deleting the bcd), it might make things worse.

also, as i'm looking at the boot info script output i posted earlier, doesn't the sda1 output suggest that the windows bootloader is working fine? thx for the effort, I really do appreciate it.

---

### Post by bcbc on 2010-05-19
> **komoku said:**
> as i mentioned in the first post, i've been at this for 7+ hours, so over that time i've tried the win7 repair process multiple times with no success (i'd say i've tried it maybe 5-6 times by now). the link you posted previously seems to rely on the /rebuildbcd command as the main way to fix the problem, but i cannot use that command since the CD doesn't find any windows installations. so i fear if i attempt those instructions (specifically deleting the bcd), it might make things worse.

also, as i'm looking at the boot info script output i posted earlier, doesn't the sda1 output suggest that the windows bootloader is working fine? thx for the effort, I really do appreciate it.

Yes, I noticed that /dev/sda1 doesn't say that grub is installed in the boot sector any more. So installing the windows boot sector removed grub, but hasn't fully fixed windows.

So that link first suggests running the windows dvd 'repair' multiple times.
> The automated repair only fixes one thing at a time, and you might need several things fixed (MBR, bootmgr, boot folder). So boot the DVD again and repeat the whole process. If it's still not working after repeating the automated repair several times, carry on with the following manual steps.


Then it recommends replacing the MBR and the bootsector manually and rebuilding the bcd
> bootrec.exe /fixmbr
x:\boot\bootsect.exe /nt60 all /force
...

Yes I can see you are wary of doing this, but I don't know what else you could try. At any rate, if you haven't already I'd be taking a full backup of your data and preparing for the possibility that you might have to reinstall. 

One other thing that puzzles me - you still have grub installed in the bootsectors of sda3 and sda5. Not sure if this is doing anything, however there are some windows boot files in sda3. So maybe try doing a bootrec /fixboot on that drive as well. (I may be grasping at straws here).Edit: sda3 is your compaq diagnostics partition, so that won't work but shouldn't stop your windows from working

Anyway - sorry I can't help more. Hopefully someone more knowledgeable will pick this up if you can't get it to work.

---

### Post by komoku on 2010-05-19
how can i identify that drive/partition in the win7 repair CD command prompt?

also, i'm looking at the "sda5/wubi/boot/grub/grub.cfg" portion of the boot info script output and am i interpreting it wrong or is it basically saying it's booting windows 7?

---

### Post by bcbc on 2010-05-19
> **komoku said:**
> how can i identify that drive/partition in the win7 repair CD command prompt?

also, i'm looking at the "sda5/wubi/boot/grub/grub.cfg" portion of the boot info script output and am i interpreting it wrong or is it basically saying it's booting windows 7?

It looks like sda3 is the compaq diagnostics partition, so fixing it won't help your main windows boot. I assume grub.cfg sees it as windows7 because it is using windows 7 boot files.

---

### Post by komoku on 2010-05-19
i just tried:

"bootrec.exe /fixmbr
x:\boot\bootsect.exe /nt60 all /force"

and it didn't fix the problem. my boot still ends with a blinking cursor and a black screen.

also, i decided to "reinstall" grub into my sda5, which when i booted it said i was in grub and this: "sh:grub>" was left on the screen. this seems to indicate to me that my computer is definitely booting into sda5 before it's booting into sda1, and that the problem seems to be in sda5. is this a correct estimation?

at this stage, i'm ready to just wipe the sda5 partition and hope that the only boot possible after that is in sda1 and windows... would formatting sda5 risk my windows files in sda1?

---

### Post by bcbc on 2010-05-19
> **komoku said:**
> i just tried:

"bootrec.exe /fixmbr
x:\boot\bootsect.exe /nt60 all /force"

and it didn't fix the problem. my boot still ends with a blinking cursor and a black screen.

also, i decided to "reinstall" grub into my sda5, which when i booted it said i was in grub and this: "sh:grub>" was left on the screen. this seems to indicate to me that my computer is definitely booting into sda5 before it's booting into sda1, and that the problem seems to be in sda5. is this a correct estimation?

at this stage, i'm ready to just wipe the sda5 partition and hope that the only boot possible after that is in sda1 and windows... would formatting sda5 risk my windows files in sda1?

No.. don't do that. sda5 is a windows partition - you will lose all of the data on it if you wipe it. 
When you install ubuntu using wubi it actually creates 'virtual disks'. These are found in the directory \ubuntu\disks\xxx.disk within your windows file system. So there is no 'ubuntu partition' at all. 
> sda5: _________________________________________________________________________

    File system:       ntfs

Installing grub is not helping either - it just sets the grub bootloader in the Master boot record of your drive. So it's not actually 'booting from sda5'. It just runs the first part of grub, and can't find the second part and fails.

You need to focus on repairing windows and leave grub, ubuntu, etc. alone. The ONLY thing you should be doing with ubuntu is running a Live CD, and then copying all your files to a backup external drive. 

If you start formatting partitions you will lose the data.

---

### Post by komoku on 2010-05-19
there is no data in sda5 that i need to keep, i've saved whatever was in there aside from ubuntu, and i also have no important files in ubuntu either. all my important files are in sda1 and windows, so i'm ready to lose all the data on sda5 so long as it doesn't affect my data on sda1.

also, i don't have any extenal HD to save files to... but i can't accept that i'll have to reformat this entire computer... the only change to windows has been to the bootloaders and the accidental installation of grub into windows, the actual windows OP should be just fine, so i can't understand why a simple booting issue would result in damage to windows severe enough to warrant a format...

---

### Post by bcbc on 2010-05-19
by the way, sda5 isn't a large partition so chances are most of your data is on sda1, however, it still won't help formatting/removing it.

Which drive did you substitute when you ran the x:\boot\bootsect.exe command? It should be your cd/dvd drive, right?

---

### Post by bcbc on 2010-05-19
> **komoku said:**
> there is no data in sda5 that i need to keep, i've saved whatever was in there aside from ubuntu, and i also have no important files in ubuntu either. all my important files are in sda1 and windows, so i'm ready to lose all the data on sda5 so long as it doesn't affect my data on sda1.

also, i don't have any extenal HD to save files to... but i can't accept that i'll have to reformat this entire computer... the only change to windows has been to the bootloaders and the accidental installation of grub into windows, the actual windows OP should be just fine, so i can't understand why a simple booting issue would result in damage to windows severe enough to warrant a format...

OK... I noticed sda5 was small - I just thought you might be deleting some other data along with ubuntu.

I agree windows should be fine... the actual files must be unaffected, however it's resisting the usual method of repair. 

Try this:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by komoku on 2010-05-19
when you told me earlier to try this:
"bootrec.exe /fixmbr
x:\boot\bootsect.exe /nt60 all /force"

the output from that said it forced windows 7 bootloading into all my partitions, so i checked boot info script again and this is the output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30942895 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa6d040ca

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   532,973,567   532,971,520   7 HPFS/NTFS
/dev/sda2         532,975,616   594,198,527    61,222,912   f W95 Ext d (LBA)
/dev/sda5         532,977,664   594,198,527    61,220,864   7 HPFS/NTFS
/dev/sda3         594,198,528   625,141,423    30,942,896  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       18ca5a4b-cdd4-4a8c-962d-3171943fbb66   ext4                                     
/dev/sda1        CA2CDF592CDF3EDF                       ntfs                                     
/dev/sda3        1A2E21902E2165CB                       ntfs                                     
/dev/sda5        54EAE1DAEAE1B7FE                       ntfs       Lenovo                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=================== sda5: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

======================== sda5/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54eae1daeae1b7fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ca2cdf592cdf3edf
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 1a2e21902e2165cb
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


   6.1GB: boot/grub/core.img
   1.8GB: boot/grub/grub.cfg
   1.8GB: boot/initrd.img-2.6.31-19-generic
   7.0GB: boot/initrd.img-2.6.32-22-generic
   2.8GB: boot/vmlinuz-2.6.31-19-generic
   1.5GB: boot/vmlinuz-2.6.32-22-generic
   7.0GB: initrd.img
   1.5GB: vmlinuz
```so now it seems win7 bootloader is in all my partitions yet i still get a blinking cursor and a black screen... is it because of the "/boot/grub/core.img" in the bootfiles/dirs sections of sda5? cause that's the only thing i can think of...

also, that link you just posted is the same commands i've been trying to use with my win7 repair CD. it still won't identify any windows installations when i try /ScanOs or /Rebuildbcd

---

### Post by komoku on 2010-05-19
ok i just tried it with this seq of commands:

"bcdedit /export C:\BCD_Backup
c:
cd boot
attrib bcd -s -h -r
ren c:\boot\bcd bcd.old
bootrec /RebuildBcd"

and it actually found a windows installation in the last step. so it seems as if the bcd was rebuilt entirely, however when i boot up, it still is just a blinking cursor and a black screen...

---

### Post by komoku on 2010-05-19
I decided to format the sda5 just to maximize my chances for recovering windows, but it didn't solve the problem. i'm currently trying to do what i can with the win7 repair CD, so if there are any options i haven't tried, please let me know...

---

### Post by komoku on 2010-05-19
i just realized something. this computer originally came with windows vista home premium. I had to order an upgrade to win 7 CD from Lenovo to get windows 7.

could this be an issue? could it be trying to use a vista boot loader or is my win7 repair cd not working because i need a vista repair cd?

---

