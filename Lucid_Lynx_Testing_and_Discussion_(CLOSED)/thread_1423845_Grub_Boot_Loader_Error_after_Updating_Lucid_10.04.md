---
title: "Grub Boot Loader Error after Updating Lucid 10.04"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by stuu on 2010-03-07
Hello, Greetings,

I installed Ubuntu Lucid 10.04, then updated the software, Grub updated.  Since I'm new to this, the technical aspect when the popup presented a menu to choose which options, I looked through the drop down list.  I picked the second one.

Unfortunately, the wording leaves little room to pick the correct one.  the first one on the list did seem right so I picked the second one which seemed right.   this however turned out to be a disaster.  

The menu list on grub, lists:
Ubuntu
Ubuntu in recovery mode
memtest
memtest
Windows Vista 

I used the 'e' key to edit the Windows Vista to see if any information was missing, but it looked good (don't know really there was plenty of wording there) then used Ctrl+X no go.

Before the updating process I booted in Windows Vista no problems.
After updating not able to boot into Windows Vista, what happens is the screen attempts to boot, but, promptly returns to the Grub Menu this is odd.

I used this command: in Ubuntu to see if the road map was destroyed:  sudo blkid 
and this was returned:

bobo@bobo-desktop:~$ sudo blkid
/dev/sdb1: LABEL="Drive" UUID="B428D63128D5F1FA" TYPE="ntfs" 
/dev/sda1: LABEL="Win6x32" UUID="56ACD21DACD1F787" TYPE="ntfs" 
/dev/sda5: UUID="9c4effcf-234e-4395-b8ed-2300367e2a68" TYPE="ext4"

how do I rebuild Grub and the MBR?

I tried the Windows Recovery method it did not work.

Bootrec /RebuildBcd produces "No Windows Installations detected with : 0
what is says it "Windows Installation: 0"

Then I used the Bootrec /FixMBR and it did not fix the MBR.

This is quite a mess.

Also to throw in a bit more:  AMD/ATI driver doesn't work.  I cannot use ATI R5670 HD Radeon DDR5 1 GB video graphics Card in 3D Mode, right now using a lowgrade Desktop OutPut.  


How do I correct the Grub problem?

Is there a fix for the AMD/ATI problem?  Installed AMD/ATI 10.2 Catalyst for x86_64.

Running Ubuntu Lucid AMD64 x86_64 on second partition, with Windows Vista on the first partition.

thanks

---

### Post by byStanderone on 2010-03-07
...not sure if lucid have an fstab file as in karmic, if it does, compare your blkid result with it...there maybe some editing needed in fstab, assuming that it also exist in lucid.

---

### Post by meierfra. on 2010-03-07
Let's check out the situation: Follow these [instructions]("http://bootinfoscript.sourceforge.net") to run the boot info script and post the RESULTS.txt.

---

### Post by alexsimps on 2010-04-11
I am having the same problem. So far i have succesfully repaired my vista boot loader as in instructions from here [http://ubuntuforums.org/showthread.php?t=828862](http://ubuntuforums.org/showthread.php?t=828862) using a free vista cd from here: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) (i think; i used a similar torrent i found). now i am back to the old vista bootloader so i will need to reinstall the grub boot loader to be able to access Ubuntu on boot. i have had no luck repairing from the ubuntu 9.04 live cd so far (sudo grub returns "sudo: grub: command not found" ?). I am currently using super grub disk (from: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) to access my Ubuntu OS as i figure out how to fix it. Ill let you know how it goes for me and would appreciate any other ideas?

---

### Post by alexsimps on 2010-04-11
Also here are the results of a current(post vista bootloader reinstall) boot info script if that helps anyone.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 2540298 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 2860018 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 3188698 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2             160,650    21,125,474    20,964,825  83 Linux
/dev/sda3    *     21,133,312   362,008,709   340,875,398   7 HPFS/NTFS
/dev/sda4         362,008,710   488,392,064   126,383,355   f W95 Ext d (LBA)
/dev/sda5         362,024,775   475,957,754   113,932,980   7 HPFS/NTFS
/dev/sda6         475,957,818   482,801,444     6,843,627  82 Linux swap / Solaris
/dev/sda7         482,801,508   488,392,064     5,590,557   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,576,704   312,576,642   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-0416                              vfat       DellUtility                   
/dev/sda2        216065a9-7ff0-4f0c-b801-45ec4c096d20   ext3       allinux                       
/dev/sda3        3EB40125382E2B62                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        B0C64650C64616CE                       ntfs       xp                            
/dev/sda6        69aba461-d5f3-40a1-8509-813d9252bbae   swap       linswap                       
/dev/sda7        1CE18FF0455BDC2C                       ntfs       free download space           
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0BDE-3817                              vfat       ALSIMPSON                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,errors=remount-ro)
/dev/sda3        /media/sda3              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/sda5              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/sdb1              vfat       (rw,noexec,nosuid,nodev)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=alex)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 216065a9-7ff0-4f0c-b801-45ec4c096d20
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 216065a9-7ff0-4f0c-b801-45ec4c096d20
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
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 216065a9-7ff0-4f0c-b801-45ec4c096d20
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=216065a9-7ff0-4f0c-b801-45ec4c096d20 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 216065a9-7ff0-4f0c-b801-45ec4c096d20
    echo    Loading Linux 2.6.32-19-generic ...
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=216065a9-7ff0-4f0c-b801-45ec4c096d20 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 216065a9-7ff0-4f0c-b801-45ec4c096d20
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=216065a9-7ff0-4f0c-b801-45ec4c096d20 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 216065a9-7ff0-4f0c-b801-45ec4c096d20
    echo    Loading Linux 2.6.31-20-generic ...
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=216065a9-7ff0-4f0c-b801-45ec4c096d20 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 216065a9-7ff0-4f0c-b801-45ec4c096d20
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 216065a9-7ff0-4f0c-b801-45ec4c096d20
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 3eb40125382e2b62
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                 0  0  
# / was on /dev/sda2 during installation
UUID=216065a9-7ff0-4f0c-b801-45ec4c096d20  /              ext3         errors=remount-ro        0  1  
# swap was on /dev/sda6 during installation
UUID=69aba461-d5f3-40a1-8509-813d9252bbae  none           swap         swap                     0  1  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8    0  0  
/dev/sdb1                                  /media/sdb1    vfat         owner,users,user         0  0  
/dev/sda3                                  /media/sda3    ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda5                                  /media/sda5    ntfs         nls=iso8859-1,umask=000  0  0  

=================== sda2: Location of files loaded by Grub: ===================


   1.3GB: boot/grub/core.img
   1.4GB: boot/grub/grub.cfg
   2.1GB: boot/initrd.img-2.6.31-20-generic
   1.3GB: boot/initrd.img-2.6.32-19-generic
  10.1GB: boot/vmlinuz-2.6.31-20-generic
   2.1GB: boot/vmlinuz-2.6.32-19-generic
   1.3GB: initrd.img
   2.1GB: initrd.img.old
   2.1GB: vmlinuz
  10.1GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
[spybotsd] 
timeout.old=15

---

### Post by alexsimps on 2010-04-11
> **stuu said:**
> 

I tried the Windows Recovery method it did not work.

Bootrec /RebuildBcd produces "No Windows Installations detected with : 0
what is says it "Windows Installation: 0"

Then I used the Bootrec /FixMBR and it did not fix the MBR.



The method from [http://ubuntuforums.org/showthread.php?t=828862](http://ubuntuforums.org/showthread.php?t=828862) used 3 different commands?
"
Fix the Master Boot Record: (commands)

[B]bootrec /fixmbr
bootrec /rebuildbcd
bootrec /fixboot[/B]
"
Perhaps its the bootrec /fixboot command that you are missing? as my vista bootloader is now working fine.

---

### Post by alexsimps on 2010-04-11
Now i have sucessfuly reinstalled my grub bootloader. The problem was that i am using grub2 and the command sudo grub only works for the original grub. I booted into ubuntu using the supergrub livecd(as mentioned before) and then as in [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html) I typed into the terminal
"sudo grub-install /dev/sda" and all is now well. Hope someone finds this helpful.

---

### Post by VMC on 2010-04-11
> **alexsimps said:**
> Now i have sucessfuly reinstalled my grub bootloader. The problem was that i am using grub2 and the command sudo grub only works for the original grub. I booted into ubuntu using the supergrub livecd(as mentioned before) and then as in [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html) I typed into the terminal
"sudo grub-install /dev/sda" and all is now well. Hope someone finds this helpful.

alex, Glad you got your booting straighten out.

If everything is ok, please mark this topic as **[solved**].
Thanks

---

