---
title: "Failed installing ubuntu 11&amp;10.4 now no windows"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by Pawels1984 on 2011-11-19
Hey guys!! I got massive problem, tried to install ubuntu 11.04(from  live cd) duall boot with win xp sp3 but during installation i was  getting message "no root file system is defined", i googled and advise i  found was to use gParted,i have 3 hard drives(no partitons),after using  this soft it created extra 4 partitions(didint know what i was  doing)thats after trying couple of times to run it.Then i decided to try  older version 10.4 ,till that time i was still able to chose betewen  windows and ubuntu shortly after booting my pc,during installation it  asked me how i wanted to install it,so i pressed "Side by side" ,after  installation finished i got black screen with I/O errors(I/O error, dev  sr0) then it stoped,I hited enter and i got System is restarting or so..  nothing happened ,i powered off my pc.After rebooting,i coulding chose between windows and ubuntu anymore plus i got error "no  such device 83332024-01aa-4869-86c2-599f9e419937" and ubuntu was going into rescue mode. I decided to go back  to basics ,i unpluged my 2 hard drives (leaving only 1),i run gParted  resized it(100GB NTFS,50GB EXT3),now i thought its gonna be straight  forward(i read its good to install windows 1st to create root files or  someting) so i run windows cd everything goes well till it finished  coping files and restarting ..its loop not going into second phase of  installation if i take cd out it says no boot files.Then i tried to  install ubuntu(i tried on every hard drive,by switching them)two of them  are not recognized by installator 3rd is being detected but i didint had windows on it and i got 20gb of my baby pics since birth and dont want to loose them.Im trying to solve this whole  day(litterally) ,im preety good at windows issues etc but this one  killed me,im clueless:confused:My girlfriend is pissed coz she cant do things on pc coz she think i broke it LOOOL!PLEASE HELP PEOPLE!!!!ps.guys if u have any ideas pleas explain them like to 5year old coz im green at ubuntu.I REALLY APPRECIATE ANY HELP!!!Thanks

---

### Post by darkod on 2011-11-19
First, and for the future, the "no root filesystem" message shows if you are using manual partitioning during the installation (which I prefer) but you did not select where to install. The root partition, mount point /, is the main system partition and you need to select one partition as minimum to be root. The installer can't continue without knowing where to install.

Now for your current problem. If I understood correctly XP doesn't boot now? Is that a new installation or you just resized the partition to 100GB?

Boot the computer with the ubuntu live cd to live mode (Try Ubuntu), and follow the link in my signature to run the boot info script. It will show more details about the system. Post the results here as explained in that link.

---

### Post by Pawels1984 on 2011-11-19
hey mate!!thanks 4 quick replay, like i said Ubuntu is totally new for me, i dont even know not how i can chose partition(i know how it sounds:/) all i done was slide that thingy on the bar left or right which i though only says how much space i want to give to each partition(side by side option),and second i downloaded 2 files from link u provided but dont know what to do with em,for me they look like txt files..please be patient ](*,)Ah and ye xp wont boot ,even more strange it wont even go past installation process ,i mean straight after inserting cd and installing it should reboot and carry on after but after rebooting its again going thru same process and again and so on i cant go past 1st phase of installation, right now i chosen to use whole partition for ubuntu installation lets see what will happen..

---

### Post by darkod on 2011-11-19
XP install: You remember that after the first phase and the first reboot, let it boot from the HDD. When the message Press Any Key to boot from CD-ROM shows up, don't press anything. Otherwise yes it will boot from the cd and start the install again. Better yet, during the first reboot take the cd out.

For the boot info script. Did you extract it after downloading? You can right click it and select Extract Here or something like that. Of course, you can do this only from ubuntu, not from windows.

When it is extracted you should end up with like boot_info_script_060.sh or similar file name. Most important, the extension should be .sh

Take a look in which directory is it. Most probably it got downloaded in the Downloads folder. If yes, you can run it in terminal with:

sudo bash boot_info_script*.sh

Depending on the ubuntu version and the layout, you can open terminal from Applications - Accessories or by opening the dash board and searching for Terminal.

The results.txt file will be created in the same folder where the script is. You need to post the content but please include it in cod tags (select the whole text and hit the # button in the toolbar above when creating the post.

---

### Post by Pawels1984 on 2011-11-19
hey again mate!! i tried to use that command in terminal u posted:sudo bash boot_info_script*.sh(with * and without,i tried that too:sudo bash ./boot_info_script.sh ,i found it inside the file) but it says "no such a file or directory" but i got that file extracted and it is in download folder ,it created folder boot_info_script060 and i copied those files from this subfolder to download folder coz i thought thats why it cant find it but same thing:/ Regards win installation ,it starting with scaning for hardware instead of standard "press any button" which is strange and when it finish and reboot,its doing it again scaninig for hardware then its going straight into setup after chosing partiton its copying files,reboot and again scaning for hardware(black screen,same as press any button but diffrent dialogue)and that goes in the loop, plus i decided to install ubuntu on whole partition and erase everything from it (thats 2nd option in 10.4) and after reboot(again I/O errors before restart) im getting error "No boot device avaiable" even tho i got 1hdd pluged in and thats 1 partition ubuntu plus it created small one called swap or something,any ideas?

---

### Post by Pawels1984 on 2011-11-19
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   299,730,943   299,728,896  83 Linux
/dev/sda2         299,732,990   312,498,175    12,765,186   5 Extended
/dev/sda5         299,732,992   312,498,175    12,765,184  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        225a85d2-3600-4c29-be08-cd0f0bf20a5b   ext4       
/dev/sda5        713e8bc5-f552-4b75-bea5-f33f35ef975e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/225a85d2-3600-4c29-be08-cd0f0bf20a5b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=225a85d2-3600-4c29-be08-cd0f0bf20a5b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=225a85d2-3600-4c29-be08-cd0f0bf20a5b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=225a85d2-3600-4c29-be08-cd0f0bf20a5b /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 128.129829407 = 137.578356736  boot/grub/core.img                             1
  64.187923431 = 68.921257984   boot/grub/grub.cfg                             1
 128.137290955 = 137.586368512  boot/initrd.img-2.6.32-33-generic              1
   0.469581604 = 0.504209408    boot/vmlinuz-2.6.32-33-generic                 1
 128.137290955 = 137.586368512  initrd.img                                     1
   0.469581604 = 0.504209408    vmlinuz                                        1

---

### Post by Pawels1984 on 2011-11-19
i read instruction in that link u send me and managed to do it,sorry it took so long.So is that giving u any info what the £$%£$^ is going on??Also if i eventually install Ubuntu can i install windows afterwards ?

---

### Post by darkod on 2011-11-19
The results look normal, but on this 160GB disk you have only ubuntu 10.04 installed. I hope this is not the disk where you expect to find windows or any other data because this disk looks like it has only ubuntu on it. It is taking up the whole hdd.

If you boot the computer with only this hdd connected, doesn't it boot ubuntu?

You can also connect the other two hdds too and run the script again with all of them connected so we can see what it finds.

---

### Post by Pawels1984 on 2011-11-19
yes there is only ubuntu on it, after rebooting im getting "no boot device available  strike f1 to retry boot, f2 for setup utility.I had windows files/folders after 1st phase of instalation but like i said installation wasnt taking me anywhere ,could that be something i done with gParted that win/ubuntu setup is not going thru?  Im gonna connect other drives and post results here.be right back!!!

---

### Post by Pawels1984 on 2011-11-19
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Windows is installed in the MBR of /dev/mapper/nvidia_debijdba.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda2 already mounted or sda2 busy

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /NTBOOTDD.SYS

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

nvidia_debijdba1: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /NTBOOTDD.SYS

nvidia_debijdba2: ______________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
16 heads, 63 sectors/track, 310019 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   204,802,047   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda2         204,812,685   312,496,379   107,683,695  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   222,580,733   222,580,671   7 NTFS / exFAT / HPFS
/dev/sdb2         222,580,734   488,396,799   265,816,066   5 Extended
Extended partition linking to another extended partition.
/dev/sdb5         222,580,736   227,465,215     4,884,480  83 Linux
Empty Partition.
/dev/sdb3         391,071,744   484,321,279    93,249,536  83 Linux

/dev/sdb2 overlaps with /dev/sdb3

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   299,730,943   299,728,896  83 Linux
/dev/sdc2         299,732,990   312,498,175    12,765,186   5 Extended
/dev/sdc5         299,732,992   312,498,175    12,765,184  82 Linux swap / Solaris


Drive: nvidia_debijdba _____________________________________________________________________

Disk /dev/mapper/nvidia_debijdba: 160.0 GB, 159999998976 bytes
16 heads, 63 sectors/track, 310019 cylinders, total 312499998 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/nvidia_debijdba1   *          2,048   204,802,047   204,800,000   7 NTFS / exFAT / HPFS
/dev/mapper/nvidia_debijdba2        204,812,685   312,496,379   107,683,695  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        381C9C861C9C40B4                       ntfs       
/dev/sda2        d5a2b381-a159-4f1e-88ea-b463e3cc3f9e   ext3       
/dev/sdb1        2418918F1891609A                       ntfs       
/dev/sdb3        83332024-01aa-4869-86c2-599f9e419937   ext4       
/dev/sdb5        cc5ee8e0-e7a9-4d44-8dfb-3af1c4e93021   ext4       
/dev/sdc1        225a85d2-3600-4c29-be08-cd0f0bf20a5b   ext4       
/dev/sdc5        713e8bc5-f552-4b75-bea5-f33f35ef975e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=1 
default=signature(c5b6c5b6)disk(2)rdisk(0)partition(1)\WINDOWS.0 
[operating systems] 
signature(c5b6c5b6)disk(2)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set cc5ee8e0-e7a9-4d44-8dfb-3af1c4e93021
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
set root='(hd0,9)'
search --no-floppy --fs-uuid --set cc5ee8e0-e7a9-4d44-8dfb-3af1c4e93021
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set cc5ee8e0-e7a9-4d44-8dfb-3af1c4e93021
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=cc5ee8e0-e7a9-4d44-8dfb-3af1c4e93021 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set cc5ee8e0-e7a9-4d44-8dfb-3af1c4e93021
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=cc5ee8e0-e7a9-4d44-8dfb-3af1c4e93021 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set cc5ee8e0-e7a9-4d44-8dfb-3af1c4e93021
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set cc5ee8e0-e7a9-4d44-8dfb-3af1c4e93021
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 83332024-01aa-4869-86c2-599f9e419937
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=83332024-01aa-4869-86c2-599f9e419937 ro quiet splash
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 83332024-01aa-4869-86c2-599f9e419937
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=83332024-01aa-4869-86c2-599f9e419937 ro single
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 839c0375-29d1-4199-8b96-c02426c313b2
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=839c0375-29d1-4199-8b96-c02426c313b2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 839c0375-29d1-4199-8b96-c02426c313b2
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=839c0375-29d1-4199-8b96-c02426c313b2 ro single
    initrd /boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=cc5ee8e0-e7a9-4d44-8dfb-3af1c4e93021 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=c54ac7ad-62de-4c1c-9cc0-03e22b00e613 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 108.430801392 = 116.426686464  boot/grub/core.img                             1
 107.972114563 = 115.934175232  boot/grub/grub.cfg                             1
 106.892219543 = 114.774646784  boot/initrd.img-2.6.32-33-generic              1
 108.451026917 = 116.448403456  boot/vmlinuz-2.6.32-33-generic                 1
 106.892219543 = 114.774646784  initrd.img                                     1
 108.451026917 = 116.448403456  vmlinuz                                        1

=========================== sdb3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 83332024-01aa-4869-86c2-599f9e419937
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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 83332024-01aa-4869-86c2-599f9e419937
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 83332024-01aa-4869-86c2-599f9e419937
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=83332024-01aa-4869-86c2-599f9e419937 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 83332024-01aa-4869-86c2-599f9e419937
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=83332024-01aa-4869-86c2-599f9e419937 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 83332024-01aa-4869-86c2-599f9e419937
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 83332024-01aa-4869-86c2-599f9e419937
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=83332024-01aa-4869-86c2-599f9e419937 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=07fd7c48-6c9b-4427-83d6-ed52f593c7bf none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 214.610157013 = 230.435901440  boot/grub/core.img                             1
 214.610160828 = 230.435905536  boot/grub/grub.cfg                             1
 214.617832184 = 230.444142592  boot/initrd.img-2.6.32-33-generic              1
 214.608753204 = 230.434394112  boot/vmlinuz-2.6.32-33-generic                 1
 214.617832184 = 230.444142592  initrd.img                                     1
 214.608753204 = 230.434394112  vmlinuz                                        1

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=225a85d2-3600-4c29-be08-cd0f0bf20a5b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=225a85d2-3600-4c29-be08-cd0f0bf20a5b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 225a85d2-3600-4c29-be08-cd0f0bf20a5b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=225a85d2-3600-4c29-be08-cd0f0bf20a5b /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 128.129829407 = 137.578356736  boot/grub/core.img                             1
  64.187923431 = 68.921257984   boot/grub/grub.cfg                             1
 128.137290955 = 137.586368512  boot/initrd.img-2.6.32-33-generic              1
   0.469581604 = 0.504209408    boot/vmlinuz-2.6.32-33-generic                 1
 128.137290955 = 137.586368512  initrd.img                                     1
   0.469581604 = 0.504209408    vmlinuz                                        1

========================== nvidia_debijdba1/boot.ini: ==========================

--------------------------------------------------------------------------------
[boot loader] 
timeout=1 
default=signature(ab0ed040)disk(0)rdisk(0)partition(1)\WINDOWS.0 
[operating systems] 
signature(ab0ed040)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
signature(20db0f21)disk(2)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  28 d7 54 b7 7b 8c 7c b6  f6 15 53 b2 6c 30 41 c6  |(.T.{.|...S.l0A.|
00000010  1e 9e 74 65 5a ef e1 5a  53 2b 5b ef c1 00 60 1f  |..teZ..ZS+[...`.|
00000020  4f f5 e2 62 7e 79 18 97  2b 4f 5e 8a 7f 09 d0 95  |O..b~y..+O^.....|
00000030  f4 bf 6e 78 58 b8 f6 d7  ca 1c 00 50 32 13 a5 a2  |..nxX......P2...|
00000040  5d 8e 3a 3c bc fd 18 5f  e5 84 a3 ac b7 a5 f1 35  |].:<..._.......5|
00000050  39 a3 f6 4b 23 c9 6c 19  16 74 5a ec c0 0b 64 05  |9..K#.l..tZ...d.|
00000060  bd 79 05 fb 20 a6 da de  c7 84 94 80 2c c5 87 04  |.y.. .......,...|
00000070  9c 37 c8 ad 91 f9 a6 f6  fa b4 e5 72 1b b1 e1 8e  |.7.........r....|
00000080  1e 13 6e b5 0a 07 6f 05  6c 65 e0 a9 ef 4d 51 7b  |..n...o.le...MQ{|
00000090  d0 54 9e 64 21 05 c6 9e  30 08 65 1e d3 a5 5e 06  |.T.d!...0.e...^.|
000000a0  7b 9e d8 37 18 86 3a ac  04 1a 18 07 4a 03 02 d9  |{..7..:.....J...|
000000b0  d2 84 eb 06 3b f3 15 98  f1 6d d3 d8 bf cd ca 3a  |....;....m.....:|
000000c0  91 53 0a ce 6c 90 23 fd  b7 7f 52 9c 7f 28 5b 96  |.S..l.#...R..([.|
000000d0  73 87 63 6d 6e 6b a4 4f  ed eb 28 2e 1e e6 a8 ba  |s.cmnk.O..(.....|
000000e0  50 a5 6b 93 ed cd 74 f2  9e 8f 02 fe a0 d0 40 17  |P.k...t.......@.|
000000f0  c7 bf 3b 95 40 d7 56 b5  1f 8d f4 4a 90 b2 e4 6d  |..;.@.V....J...m|
00000100  0f a0 00 19 dc c2 bb 61  ff e3 df 4f fd c8 54 79  |.......a...O..Ty|
00000110  f9 c0 d8 3b 35 dc c6 a0  8b 2d c6 b9 40 96 d4 ba  |...;5....-..@...|
00000120  98 59 b5 64 60 ca 80 7d  f8 f2 6d a6 5a 79 2b 1e  |.Y.d`..}..m.Zy+.|
00000130  f3 a5 89 c6 6f f4 5a 8e  bf 62 22 d4 c9 26 ac 2c  |....o.Z..b"..&.,|
00000140  96 53 22 78 12 f2 aa 89  1c a0 e4 8b b3 08 18 52  |.S"x...........R|
00000150  b6 89 2f 2b 99 f4 2f 33  0f d5 4a 27 52 28 9a 24  |../+../3..J'R(.$|
00000160  25 5f 61 76 83 06 c2 9c  64 b4 7d bd 77 2c 97 2d  |%_av....d.}.w,.-|
00000170  38 0a f9 6a 19 ad 17 5f  23 f3 2b d4 3e b7 ee e5  |8..j..._#.+.>...|
00000180  aa 7c 63 db ad 6d 87 aa  e5 47 c2 f0 76 9d 70 23  |.|c..m...G..v.p#|
00000190  63 fb 87 ae 51 27 18 2c  a5 fb f6 2b 3e 33 b9 3c  |c...Q'.,...+>3.<|
000001a0  55 11 6e e4 d4 18 97 25  f3 d4 0c f8 af 5c 51 42  |U.n....%.....\QB|
000001b0  0f 53 87 09 d1 75 b5 d2  fb 7d a5 f7 66 c2 00 0f  |.S...u...}..f...|
000001c0  ff ff 05 0f ff ff 01 00  00 00 01 88 4a 00 00 00  |............J...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

ERROR: nvidia: wrong # of devices in RAID set "nvidia_debijdba" [1/2] on /dev/sda
ERROR: nvidia: wrong # of devices in RAID set "nvidia_debijdba" [1/2] on /dev/sda
ERROR: creating degraded mirror mapping for "nvidia_debijdba"
ERROR: nvidia: wrong # of devices in RAID set "nvidia_debijdba" [1/2] on /dev/sda
ERROR: nvidia: wrong # of devices in RAID set "nvidia_debijdba" [1/2] on /dev/sda
ERROR: nvidia: wrong # of devices in RAID set "nvidia_debijdba" [1/2] on /dev/sda

---

### Post by Pawels1984 on 2011-11-19
all done..is that giving u any ideas??:-k

---

### Post by darkod on 2011-11-19
OK, that's one huge chaos. Lets go step by step.

It seems there is raid meta data present on /dev/sda (one of the 160GB disks).
ERROR: nvidia: wrong # of devices in RAID set "nvidia_debijdba" [1/2] on /dev/sda

Were you using the 160GB disks in raid array with windows XP installed on them or not?

---

### Post by Pawels1984 on 2011-11-19
like i posted on the begining mate, after one of my failed ubuntu installations ,i couldnt chose windows anymore(in dual boot),cant chose anything really atm, i still got it on hdd but i cant run it,plus that hard drive was disconected when i was trying to install ubuntu most recently.what should i do now?..sorry its late and im knackered cant even read properly, yes one of 160gb disks had windows on it and it is very likely it was set to raid in bios(i changed that earlier today)

---

### Post by darkod on 2011-11-19
I understand, but answering the question will help us all. The raid meta data on the disk might be from earlier use of raid that you don't care about, or it might be from current raid array that has been broken without intention. Which one is it?
Forget about the ubuntu installs that didn't finish, and that windows can't boot.
When it was booting were you running it on a raid1 array or not?

And by the way, one reason why the first install of ubuntu didn't work might be if you tried installing it on a raid array. You use different procedure to install on raid. Stick to the above question for now.

---

### Post by darkod on 2011-11-19
> sorry its late and im knackered cant even read properly, yes one of  160gb disks had windows on it and it is very likely it was set to raid  in bios(i changed that earlier today)

Yeah, but was the raid array created first and then XP installed? Because simply changing the option in bios does not mean you have the OS installed on raid. You need to first make the array and then install the OS on it.

---

### Post by Pawels1984 on 2011-11-19
Darko U R THE MAN, i fixed it thanks to u mate!!!! i turned off raid and acitvated all drives ,and now i got like 6 ubuntu's to chose from and win xp but this one is not working coz of hardware change, but that aint a problem at last im not booting up from cd loool:DI tell u man u deserve a medal or at least :popcorn::popcorn::popcorn:U rock man:guitar: In fact my friend,if u pm me ur adress im gonna send u something to show u my graditude(seriously).Thanks a lot and take care

---

### Post by darkod on 2011-11-19
OK, glad you got it going. However, there are still issues. :)

The 250GB disk has overlapping partitions (taking the same space). Long term, that's a bomb waiting to go off. The first partition on that disk is approx 110GB ntfs partition. I don't know if that holds important data.

If it does, I would try opening it from ubuntu or XP, and copying the data on external HDD, to be safe. Then I would use Gparted in ubuntu (you might need to install it) to create a new empty partition table. Then create one ntfs partition with the size you want, you might as well use the whole disk as one single ntfs partition. After that you can copy the data back.

If you need to install Gparted you can do it in terminal with:
sudo apt-get install gparted

I guess the ubuntu that is working now is from the third disk (/dev/sdc) because that's the only that looked OK.

Most important now is to make backup of your data, because there are still things to sort out. Then you can begin sorting them out one by one. Feel free to ask for help here.

---

