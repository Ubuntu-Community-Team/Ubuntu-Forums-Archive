---
title: "Boot errors when dual-booting Ubuntu 10.04 w/ Win7"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by speedy2686 on 2010-05-19
I just bought a new laptop--Asus G51J-A1--and I've installed Ubuntu 10.04 in a 20GB partition of my hard drive.  Windows 7 still loads and seems to function just fine, but Ubuntu loads only sporadically.  Sometimes it stops while booting, in terminal mode, with a few errors listed.  Starting at the top of the screen:

"init: plymouth main process (505) killed by kill signal"
"init: plymouth main process (503) killed by kill signal"

There might be other errors, but I haven't had a chance to write them down yet.  I'll update this post later with any other errors I see.

Aside from the above scenario, there has been at least one occasion, when booting in recovery mode, the screen went black--as it does the moment before the first Ubuntu graphics load--and two lines appear on the screen in smaller but similar type to terminal mode.  Those lines are as follows:

"init: plymouth-splash main process (1093) terminated with status 1"
"init: ureadahead-other main process (1100) terminated with status 4"
"init: ureadahead-other main process (1117) terminated with status 4"

Does anyone have any experience solving this problem or any like this?  I'm a new Ubuntu user and would really like to be able to dual-boot Ubuntu and Windows 7 on my laptop.

---

### Post by CalmB4theStorm on 2010-05-20
Similar issue here.  Half the time I just get a black screen on boot, other half of the time I get the above error messages followed by the system actually booting.

Also I just set up dual boot with Windows 7 as well.

---

### Post by tommcd on 2010-05-20
> **speedy2686 said:**
> I just bought a new laptop--Asus G51J-A1--and I've installed Ubuntu 10.04 in a 20GB partition of my hard drive.  Windows 7 still loads and seems to function just fine, but Ubuntu loads only sporadically. 
Were you able to run the Ubuntu live CD without problems? And then when you installed Ubuntu to the 20GB partition, you could not boot to the desktop?
Did you run the option "*check disc for defects*" when you boot the Ubuntu CD to be sure the CD isfree from errors?
Assuming the CD is good and passes the check, have you installed the nvidia proprietary driver for your card?
Since your laptop uses a late model nvidia card:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220605](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220605)
 Try booting to recovery mode, login, and install the nvidia driver:
```

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

```
Then see if you can get to the Ubuntu desktop without problems. Ubuntu uses by default the nouveau open source driver for nvidia. It is possible that nouveau is just not working well with your nvidia card.
If you have already installed the nvidia driver, you can disregard this. Anyway, post back either way.

And welcome to the Ubuntu forums!

---

### Post by speedy2686 on 2010-05-21
The Ubuntu Live CD worked just fine.  After the installation, it only boots without problems about 1/5 times.  The majority of the time, it stops in the way that I described in the original post.  I was going to try re-installing from a USB, but my BIOS didn't list the USB as an option.

As for the suggestion about the Nvidia driver, that could very well be the case.  I do remember beneath the errors I listed there being some lines with the word "nouveau," but I haven't had a chance to write those down and post them here.  I'll try installing the Nvidia driver on Ubuntu and let you know what happens.

Thanks for your help, so far.  I'm quite pleased and somewhat surprised by how helpful people are on these forums.

---

### Post by wilee-nilee on 2010-05-21
Post the bootscript in code tags so we can see exactly what going on.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
To get the code tags just highlight the script readout in the reply window and hit the # in the reply gui. Without it being posted this way it makes it very hard to read.

---

### Post by speedy2686 on 2010-05-22
I've updated my NVidia drivers and that's reduced the list of errors when booting.  It still doesn't boot properly everytime, so I've used bootinfoscrip, as suggested and here are the results:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    40,965,749    40,963,702  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     40,965,750   285,153,749   244,188,000   7 HPFS/NTFS
/dev/sda3         285,153,811   976,773,119   691,619,309   f W95 Ext d (LBA)
/dev/sda5         285,153,813   934,825,024   649,671,212   7 HPFS/NTFS
/dev/sda6         934,825,984   974,936,063    40,110,080  83 Linux
/dev/sda7         974,938,112   976,773,119     1,835,008  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        9EDAE585DAE559D3                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda5        7A2401CABF18F905                       ntfs       DATA                          
/dev/sda6        8bd8f5fd-cfcb-47ed-b599-f553aab2b57e   ext4                                     
/dev/sda7        a806fd22-99c7-40a2-8dbf-c728e220400b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
search --no-floppy --fs-uuid --set 8bd8f5fd-cfcb-47ed-b599-f553aab2b57e
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
search --no-floppy --fs-uuid --set 8bd8f5fd-cfcb-47ed-b599-f553aab2b57e
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8bd8f5fd-cfcb-47ed-b599-f553aab2b57e
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=8bd8f5fd-cfcb-47ed-b599-f553aab2b57e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8bd8f5fd-cfcb-47ed-b599-f553aab2b57e
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=8bd8f5fd-cfcb-47ed-b599-f553aab2b57e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8bd8f5fd-cfcb-47ed-b599-f553aab2b57e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8bd8f5fd-cfcb-47ed-b599-f553aab2b57e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8bd8f5fd-cfcb-47ed-b599-f553aab2b57e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8bd8f5fd-cfcb-47ed-b599-f553aab2b57e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8bd8f5fd-cfcb-47ed-b599-f553aab2b57e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8bd8f5fd-cfcb-47ed-b599-f553aab2b57e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3c98-ac5d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 9edae585dae559d3
    chainloader +1
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda6 :
UUID=8bd8f5fd-cfcb-47ed-b599-f553aab2b57e    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda5 :
UUID=7A2401CABF18F905    /media/DATA    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda2 :
UUID=9EDAE585DAE559D3    /media/OS    ntfs-3g    defaults,locale=en_US.utf8    0    0
#Entry for /dev/sda7 :
UUID=a806fd22-99c7-40a2-8dbf-c728e220400b    none    swap    sw    0    0



=================== sda6: Location of files loaded by Grub: ===================


 495.9GB: boot/grub/core.img
 481.1GB: boot/grub/grub.cfg
 495.9GB: boot/initrd.img-2.6.32-21-generic
 495.9GB: boot/initrd.img-2.6.32-22-generic
 495.9GB: boot/vmlinuz-2.6.32-21-generic
 495.9GB: boot/vmlinuz-2.6.32-22-generic
 495.9GB: initrd.img
 495.9GB: initrd.img.old
 495.9GB: vmlinuz
 495.9GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-05-22
The only thing I would suggest here is that changing the boot to sda1 might be the fix that works. You should do this with the live Ubuntu CD>gparted right click on sda1 and then flags and set it to boot. The boot is usually set in the recovery on new laptops so that it can be run to recover sda2 annd boot the computer. 

If this works then just be sure to run sudo update-grub in the booted Ubuntu install. The correct boot manager files are in sda2 but I suspect it booted from sda1 as a boot point to begin with, but I could be totally wrong.

Changing the boot partition will do no harm and it can be set back to sda2 if needed.

---

### Post by mpgarate on 2010-05-22
I am having the same issue with 10.04 and Windows 7.

my error reads:

```
init: plymouth main process (451) killed by KILL signal
init: unreadahead main process (450) killed by Kill signal
fsck from util-linux-ng 2.17.2
/dev/sda5 clean, xxxxx/xxxxxx files, xxxxxxx/xxxxxx blocks
init: plymouth-log main process (872) terminated with status 1
```

---

### Post by j_patterson on 2010-05-29
I have had the same issue ever since i upgraded to 10.04 a few days ago, although i can never successfully boot.  I have an ATI video card, not nVidea, and have already tried using the generic xforcevesa or nomodeset with no luck...  I am also dual booting with windows 7, but can't really see how this would mess up ubuntu.

I can boot with the live CD just fine, and have chroot'd  to try and reinstall plymouth, grub, mountall, did apt-get upgrade and such.  none of that has fixed it either.  Also tried changing the boot flag to sda1 in gparted.  

If it comes to it i can do a fresh install, but i would rather not format the hard drive again.  And it sounds like speedy2686 was doing a fresh install not an upgrade and had the same problem, so its possible the fresh install would't get it working either.

I have tried pretty much everything i can think of, although i'm not that experienced with linux...

Speedy did you get this fixed?  Anyone else have any ideas?

thanks

---

### Post by mpgarate on 2010-05-29
I have also been having an issue where GRUB freezes on boot. Might be related to having USB devices plugged in. This release isn't starting up smoothly on my thinkpad w510

---

### Post by blagosphere on 2010-05-29
I have installed my dual boot using the WUBI [windows ubuntu installer] and have had no problems dual booting with XP. Did all of you with the problem install from the cd? and did you have a working ubuntu before the update?

---

### Post by j_patterson on 2010-05-29
mpgarate - the error messages you listed aren't the same as Speedy2686's, i am getting the exact error the Speedy pasted.  init: plymouth-spash main process (xxx) terminated with status 1   then the ureadahead errors.  i don't know if plymouth-splash v plymouth-log is a clue....

i had the dual boot set up with ubuntu 9.10 and windows 7, then upgraded to 10.04 through update manager and have been trying to figure this out since

---

### Post by j_patterson on 2010-05-30
ya so i just did a fresh install and it works fine now.  There was no need to format the whole drive of course just linux partitions.

Actually, after the re-install, if i turn off quiet boot in /etc/default/grub, i can still see the same errors during boot.

So those errors were not the problem in case someone else tries to boot and it hangs on those error messages.

---

### Post by Mykro on 2010-07-01
Hi, I'm having what looks like a very similar problem.  I have  Ubuntu and Windows 7 each on their own SATA drive plus an IDE external drive.  Somehow at some point (likely after upgrading 9.10 to 10.04), I realised that Ubuntu wouldn't boot with the external drive turned off.  It looked like the MBR had been moved there.

So I disconnected the external drive, blew away any remnants of grub on the internal Ubuntu drive and installed grub2 on there.  But my system still won't boot - both normal and recovery modes produce the error:

init: plymouth-splash main process (xxx) terminated with status 1

and nothing more happens, though I can type characters and the system responds to things like Ctrl-Alt-Del and Alt-SyReq-1.

Output of Boot Info Script from a 10.04 LiveCD, which boots just fine:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   409,599,999   409,393,152   7 HPFS/NTFS
/dev/sda3         409,609,305 2,930,272,064 2,520,662,760  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    69,240,149    69,240,087  83 Linux
/dev/sdb2          69,240,150    72,292,499     3,052,350   5 Extended
/dev/sdb5          69,240,213    72,292,499     3,052,287  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        463EA46B3EA45629                       ntfs       System Reserved               
/dev/sda2        E0B6C604B6C5DB64                       ntfs                                     
/dev/sda3        fae8dc32-04d2-4310-aad4-ba8f3eef364a   ext3       bigdata                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        bec09d7d-c420-4c89-b8c4-221ee23d9829   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        30cd8266-2a55-4eaf-a9ed-644c3296793b   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=bec09d7d-c420-4c89-b8c4-221ee23d9829 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=bec09d7d-c420-4c89-b8c4-221ee23d9829 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=bec09d7d-c420-4c89-b8c4-221ee23d9829 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=bec09d7d-c420-4c89-b8c4-221ee23d9829 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=bec09d7d-c420-4c89-b8c4-221ee23d9829 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=bec09d7d-c420-4c89-b8c4-221ee23d9829 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.27-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
	linux	/boot/vmlinuz-2.6.27-14-generic root=UUID=bec09d7d-c420-4c89-b8c4-221ee23d9829 ro   quiet splash
	initrd	/boot/initrd.img-2.6.27-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.27-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
	echo	'Loading Linux 2.6.27-14-generic ...'
	linux	/boot/vmlinuz-2.6.27-14-generic root=UUID=bec09d7d-c420-4c89-b8c4-221ee23d9829 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.27-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set bec09d7d-c420-4c89-b8c4-221ee23d9829
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 463ea46b3ea45629
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
# <file system> 				<mount point>   <type>  	<options>       	<dump>  <pass>
proc            				/proc           proc    	defaults       		0       0
# /dev/sdb1
UUID=bec09d7d-c420-4c89-b8c4-221ee23d9829 	/               ext3    	relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=30cd8266-2a55-4eaf-a9ed-644c3296793b 	none            swap    	sw              	0       0
/dev/scd0       				/media/cdrom0   udf,iso9660	user,noauto,exec,utf8 	0       0
# /dev/sda1 200GB (automounts with : ext3 rw,nosuid,nodev,uhelper=hal 0 0)
UUID=24f02e59-c08f-4de4-a299-daa8c3219f5a 	/media/disk1    ext3    	relatime,errors=remount-ro 0       1
# /dev/sda2 500GB (automounts with : xfs rw,nosuid,nodev,uhelper=hal 0 0)
UUID=0c3d09a8-c742-4dad-ab85-3b56a215999c 	/media/disk2    xfs	    	relatime 0       1


=================== sdb1: Location of files loaded by Grub: ===================


   4.9GB: boot/grub/core.img
   4.9GB: boot/grub/grub.cfg
   4.9GB: boot/grub/stage2
  30.1GB: boot/initrd.img-2.6.27-14-generic
   5.4GB: boot/initrd.img-2.6.31-21-generic
  11.4GB: boot/initrd.img-2.6.32-22-generic
   8.7GB: boot/initrd.img-2.6.32-23-generic
  14.9GB: boot/vmlinuz-2.6.27-14-generic
  11.4GB: boot/vmlinuz-2.6.31-21-generic
  30.1GB: boot/vmlinuz-2.6.32-22-generic
  30.1GB: boot/vmlinuz-2.6.32-23-generic
   8.7GB: initrd.img
  11.4GB: initrd.img.old
  30.1GB: vmlinuz
  30.1GB: vmlinuz.old

```

I've been struggling with this for a couple of nights.  I'd really, really appreciate any suggestions anyone can give me.  

Thanks!

---

### Post by tommcd on 2010-07-01
[QUOTE=Mykro]Somehow at some point (likely after upgrading 9.10 to 10.04), I realised that Ubuntu wouldn't boot with the external drive turned off. It looked like the MBR had been moved there.

So I disconnected the external drive, blew away any remnants of grub on the internal Ubuntu drive and installed grub2 on there. But my system still won't boot - both normal and recovery modes produce the error:[/QUOTE]
So /dev/sda and /dev/sdb are both internal drives? Is that correct?
Assuming that is correct, it looks like Ubuntu is installed to /dev/sdb1 and the grub files are there as well. Grub is installed to the MBR of /dev/sdb.
As near as I can tell, there is nothing wrong with the output of your bootinfo script. I am not an expert in reading that though.
Make sure that /dev/sdb is set as *the first boot device* in the computer's BIOS. I am not sure what else you could try.

FYI: It is always a good idea to disconnect any external drives, flash drives, and the like when you are installing or upgrading Ubuntu.

---

### Post by Mykro on 2010-07-01
Yes, they are both internal, the external drive is out of the picture (until I can get this working). What I'm trying to work out here is whether this is still a GRUB2 problem (I've tried grub-legacy with the same result) or whether it is a problem elsewhere. Incidentally after mounting sdb1 on the livecd there is no /var/boot/boot.log file.  All there is in that dir is a "boot" file with one line to the effect of logging has not commenced, and a "bootstrap.log" file.

Yes, the sdb drive is the first selected in the BIOS.  I use the bios's "F8" boot selector menu if I want to boot into Windows.
 
The point about disconnecting external drives is a good one, though Ubuntu makes it so easy to upgrade that I completely overlooked that the external drive was attached.

---

### Post by tommcd on 2010-07-02
> **Mykro said:**
>  What I'm trying to work out here is whether this is still a GRUB2 problem (I've tried grub-legacy with the same result) or whether it is a problem elsewhere. Incidentally after mounting sdb1 on the livecd there is no /var/boot/boot.log file. 
Why do you have grub2 and grub-legacy? What version of Ubuntu were you upgrading *from*?
Your bootinfo output only indicates grub2. I would leave grub-legacy out. Grub2 should work just fine.
When you mount /dev/sdb1 with the live CD, can you post your */boot/grub/grub.cfg* file?
You could also try reinstalling grub2 to the MBR of /dev/sdb from the live CD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Are you able to boot Ubuntu at all yet?

---

### Post by Mykro on 2010-07-02
Hi tommcd,

Thanks for replying.  I initially had grub-legacy, having upgraded to every release since about 8.10.  I wasn't having any luck getting a successful boot and thought I might do better with GRUB2 so I had uninstalled grub-legacy and installed GRUB2, all using that same page you referenced - I've reinstalled GRUB2 several times, following both Method 1 and Method 3 and they always gave the impression of a successful install.  However, the boot failure is still the same in all cases.

The code snippet I pasted earlier does contain "sdb1/boot/grub/grub.cfg" from what I can tell.

Can it be a plymouth issue?  Do I need to reinstall that?

---

### Post by oldfred on 2010-07-02
I think it was another thread where someone was having issues with xfs partitions. I would just as a test, comment out the mounting of your xfs partition and see it that makes a difference.

---

### Post by Mykro on 2010-07-03
Solved!  My fstab still had entries referencing the external drive's partitions as sda1 and sda2.  After disconnecting that drive the Windows 7 drive became sda and Ubuntu was getting hung up on either trying to find the old UUIDs or in trying to mount the Win7 partitions as ext3 and xfs.  

I commented out the offending fstab entries and successfully booted.

Big thanks to oldfred and tommcd for your help in getting me on the right track.  Cheers :)

---

### Post by gregwilkins on 2010-07-14
I've been having the same issues listed here.  Previously only 1 in 5 boots would succeed, with the other boots failing either with segv or with the ureadahead/plymouth killed.

Now this problem has got a lot worse, in fact I cannot boot at all.  I have tried all the kernels listed in grub menu, and the recovery options, but all have failed.

will try a reinstall

---

### Post by oldfred on 2010-07-14
Are you also mounting additional partitions and does one of them have some issues making it slow or difficult to mount? Might try chkdsk on NTFS and fsck on ext partitions:

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

