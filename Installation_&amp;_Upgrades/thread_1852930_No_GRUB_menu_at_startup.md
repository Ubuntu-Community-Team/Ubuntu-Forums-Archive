---
title: "No GRUB menu at startup"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by laurac1022 on 2011-10-01
I just installed Ubuntu 11.04 along side Win 7.  When I installed, I chose to install GRUB in its own /boot partition instead of the MBR and just let the window boot manager be in charge of booting.  Now when I restart the Windows boot manager boots fine and I can choose win7 or ubuntu but when I choose ubuntu It never loads the GRUB menu.  Instead it reads "Minimal BASH-like line editing supported......"  Its hard to tell what all it says cause it seems like the resolution is set too low and all the words are really big and hanging off the screen(same with desktop when I boot via usb).  Maybe a video card problem??  I have a ASUS desktop with Intel Core i5 2310 with onboard intel hd graphics and 12gb ram.

 I booted off the usb and downloaded the boot_info_script.sh

results:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 60974 of /dev/sdf1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   616,034,303   615,827,456   7 NTFS / exFAT / HPFS
/dev/sda3         616,036,350 1,069,662,207   453,625,858   5 Extended
/dev/sda5         616,036,352   616,538,111       501,760  83 Linux
/dev/sda6         616,540,160   620,443,647     3,903,488  82 Linux swap / Solaris
/dev/sda7         620,445,696   679,036,927    58,591,232  83 Linux
/dev/sda8         679,038,976 1,069,662,207   390,623,232  83 Linux


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 8019 MB, 8019509248 bytes
29 heads, 24 sectors/track, 22504 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *          2,264    15,663,103    15,660,840   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        90BC1AD2BC1AB2A8                       ntfs       System Reserved
/dev/sda2        C6E21D3DE21D32E3                       ntfs       
/dev/sda5        2a0252f3-811d-4350-821b-1f5ce4a257d0   ext2       
/dev/sda6        d1e5a220-abed-40d3-ad8c-35e5b4dabb93   swap       
/dev/sda7        35c454cd-d521-4fd0-8836-d86ae20bc7c2   ext4       
/dev/sda8        0b470176-7c0c-4b95-9324-7e466cfeae51   ext4       
/dev/sdf1        1BE5-443B                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda5/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 35c454cd-d521-4fd0-8836-d86ae20bc7c2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 2a0252f3-811d-4350-821b-1f5ce4a257d0
set locale_dir=($root)/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 2a0252f3-811d-4350-821b-1f5ce4a257d0
    linux    /vmlinuz-2.6.38-8-generic root=UUID=35c454cd-d521-4fd0-8836-d86ae20bc7c2 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 2a0252f3-811d-4350-821b-1f5ce4a257d0
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=35c454cd-d521-4fd0-8836-d86ae20bc7c2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 2a0252f3-811d-4350-821b-1f5ce4a257d0
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 2a0252f3-811d-4350-821b-1f5ce4a257d0
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 90BC1AD2BC1AB2A8
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
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 293.919198990 = 315.593336832  grub/grub.cfg                                  1
 293.792879105 = 315.457701888  initrd.img-2.6.38-8-generic                   56
 293.763688087 = 315.426358272  vmlinuz-2.6.38-8-generic                      19

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=35c454cd-d521-4fd0-8836-d86ae20bc7c2 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=2a0252f3-811d-4350-821b-1f5ce4a257d0 /boot           ext2    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=0b470176-7c0c-4b95-9324-7e466cfeae51 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=d1e5a220-abed-40d3-ad8c-35e5b4dabb93 none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sdf1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdf1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdf1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdf1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdf1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by oldfred on 2011-10-01
I do not understand how you are booting at all. Normally you have to have grub2's boot loader installed to a MBR or PBR, but you show neither. Are you using EasyBCD or another third party boot loader? Script does not show it.

Do you get the grub menu? With video issues a setting in the grub menu as you boot often gets you started then you can make permanent chages it the one time boot change works.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by laurac1022 on 2011-10-01
Yes I did use EasyBCD...sorry I forgot to add that part.

After I select ubuntu from the windows boot manager, the screen shows:
[ Minimal BASH-Like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists the possible  completions of a device/filename. ]
Grub> (well I thing it says grub but all I can see is "ub>"

---

### Post by oldfred on 2011-10-01
If it is just grub> you have not got past the boot stage.

We can try manual booting, spaces are important, # is comment do not type and do not type the grub>:

You do have a grub config in sda5.

# try this first:
grub> **configfile (hd0,5)/boot/grub/grub.cfg**


#Separate /boot on sda5, / on sda7:
grub> set prefix=(hd0,5)/grub
grub> insmod linux
grub> set root=(hd0,7)
grub> linux (hd0,5)/vmlinuz-2.6.38-8-generic root=/dev/sda7 ro
grub> initrd (hd0,5)/initrd.img-2.6.38-8-generic
grub> boot

additonal info:
[https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode](https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode)

---

### Post by laurac1022 on 2011-10-01
# try this first:
grub> **configfile (hd0,5)/boot/grub/grub.cfg**
 
tried this^
 
it generated this response:
error 17: Cannot mount selected partition

---

### Post by laurac1022 on 2011-10-01
after the configfile command didnt work I tried the ones you originally suggested without much luck...see below:
 
```
 
grub> set prefix=(hd0,5)/grub
 
grub> insmod linux
 
error 15: File not found
 
grub> set root=(hd0,7)
 
grub> linux (hd0,5)/vmlinuz-2.6.38-8-generic root=/dev/sda7 ro
Warning! No such command: linux
 
grub> _

```

---

### Post by oldfred on 2011-10-01
If the insmod file did not work, that is saying that all of grub must not be in your /boot partition. Separate /boot partitions for standard desktops make it a bit more difficult to manually boot or repair as you always have to remember to separately mount the /boot and many instructions do tell you that or just have it as a foot note.

How do you want to proceed? I am used to repairing and putting grub2's boot loader in the MBR and do not know much about what EasyBCD needs.

If a new install you can reinstall (but without separte /boot) in about an hour. You can chroot into your system and repair it, lots of typing but much can be copy & pasted from your liveCD.

Check for separate mount of /boot in chroot commands.
Reinstall grub2 - Short version &** full chroot version**
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - **see METHOD 3 - CHROOT**:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

chroot & grub uninstall & reinstall -drs305 (you may not have to uninstall but it would not hurt)
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I have these links but have never installed EasyBCD.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by drs305 on 2011-10-01
I don't know what is going on, but getting an error message number is Grub legacy and not a characteristic of Grub 2, which doesn't display error messages in this manner.

---

### Post by oldfred on 2011-10-01
Good catch drs305, I missed that. But I do not see any evidence of old grub in the boot script. grub. cfg, no menu.lst. But grub2's core.img is not shown also.

@laurac1022
Are you perhaps booting thru the flash drive?

---

### Post by laurac1022 on 2011-10-01
> **oldfred said:**
> Good catch drs305, I missed that. But I do not see any evidence of old grub in the boot script. grub. cfg, no menu.lst. But grub2's core.img is not shown also.

@laurac1022
Are you perhaps booting thru the flash drive?
I wish that was the problem...the flash drive isn't even inserted

---

### Post by oldfred on 2011-10-02
Did you follow any old commands to reinstall grub which is now grub legacy?

It may just be easier to fully uninstall grub & grub2 and reinstall grub2 to the MBR, then reinstall EasyBCD.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by laurac1022 on 2011-10-02
I followed this tutorial to install:
 
[http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/)
 
In concern to the GRUB2 issue should I try the boot-repair option that was listed in the link you provided to me?

---

### Post by oldfred on 2011-10-02
I agree with everything in your link except the separate /boot partition. Not really required for most desktops. But if a server or server type configuration with RAID or LVM or a very old computer then a /boot may be required.

You can try boot repair, but I do not know how it works with EasyBCD. There is another thread where the user has issues with EasyBCD and switched to the 32 bit and it worked. Not sure if it was just a new install or if there is some odd difference??

---

### Post by laurac1022 on 2011-10-02
I dont know what I did to screw it up in the first place but boot repair fixed it! I booted via live usb and used this page as reference:
 
[https://help.ubuntu.com/community/Boot-Repair#Using%20Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair#Using%20Boot-Repair")
 
The instructions were a little unclear as to whether or not to change the advanced settings so I did change a few things and the process was relatively easy. After it was done, I booted to the harddisk and first wanted to make sure Win7 was still intact...it ran a chkdisk then rebooted normally. Restarted again and this time chose ubuntu @ the Windows boot manager...and voila!! there was the GRUB menu! Ubuntu booted and asked me for the login I made when I installed it and everything seems to be working perfectly. 
 
THank you so much
 
eta: I didn't have to reinstall EasyBCD

---

### Post by laurac1022 on 2011-10-02
Oh and I forgot to add that boot repair gave me a link to the results:
 
[http://paste.ubuntu.com/701167/](http://paste.ubuntu.com/701167/)

---

### Post by laurac1022 on 2011-10-02
ok now I just encountered another problem.  I attempted to change the resolution because I could only see half the toolbar on the left hand side and none of the one along the top.  When I changed it the display went black but I can still see and move my mouse around.  Is this an issue you can help me with or should I start a new thread?

---

### Post by laurac1022 on 2011-10-02
Nevermind my last post.  I resolved my issue with the resolution.

---

### Post by oldfred on 2011-10-03
Glad to know boot repair worked. 

You do have grub2 installed to the partition. If an update includes updates to grub2's boot files it may break an install of the boot loader to a partition. Just be prepared to reinstall the boot loader. If you notice an update is installing new grub files you can reinstall then, but every update may not cause problems. Just have a liveCD as a backup and know how to fix it. Boot repair also has a bootable liveCD version or you can redownload it into the Ubuntu liveCD.

To reinstall grub from a working system, normally you do not specify partition, but in you case you want to specify sda5.

sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, normally do not choose partitions

---

### Post by laurac1022 on 2011-10-03
Ok.  Thanks for the heads up.

---

