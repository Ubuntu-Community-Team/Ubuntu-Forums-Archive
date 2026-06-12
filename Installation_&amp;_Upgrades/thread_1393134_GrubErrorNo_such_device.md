---
title: "Grub:Error:No such device"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by drunkenbrawler on 2010-01-29
Hello everyone,
I'm using Kubuntu 9.10 with Ubuntu-desktop installed.
I've been using kubuntu for sometime now but i dont know much technical things about it. 

I have two hard discs (160GB SATA and 80GB PATA).

I have just installed Windows XP Professional and then reinstalled grub2 from a live CD. Both OS are on 80GB PATA drive.

The Grub menu at boot time has "Windows XP Professional" entry in it. The problem is that
when i select that entry, i get an error saying:

> 
Grub:Error:No such device - "a string of letters and numbers"
Press any key to continue...

:confused:
 
When i press any key, it goes back to the grub menu. Kubuntu and Ubuntu work fine.
When i go to bios and change my hard disc boot order, grub is bypassed and Windows boots and works good. 

I dont know much technical things but i think maybe its the problem with Windows entry in grub. (something to do with lines map(hd0,hd1) and map(hd1,hd0) (But i'm nt sure. I just said wat i thought it might be)

I have done this ones with menu.lst in 9.4 but i dont know anything about grub2. I tried to read Grub2 guide but it wont help.

Any help will be greatly appreciated. 
Thanx. :)

---

### Post by presence1960 on 2010-01-29
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. See below (thanks to meierfra) for more info on boot info script:

boot_info_script is a bash script which searches all hard drives attached to the computer for information related to booting and displays it in a convenient format. Its primary use is for troubleshooting booting problems.
How to use the boot info script

    * Boot into any Linux based operating system or Live CD with an Internet connection.
    * Download the Boot Info Script
    * Open a terminal (Applications>Accessories>Terminal in Gnome) and type

       sudo bash [path/to/the/download_folder]/boot_info_script*.sh

      For example if you downloaded the file to the desktop, use

       sudo bash ~/Desktop/boot_info_script*.sh 

    * If your operation system does not use sudo, use

           su 
           bash ~/Desktop/boot_info_script*.sh
           

    * You will now have the file RESULTS.txt in the same directory as the script. But if the script is inside a system directory (like /usr or /etc) RESULTS.txt will be in the home directory.
    * If you already have an existing RESULTS.txt, subsequent files will be called RESULTS1.txt, RESULTS2.txt,...
    * Open RESULTS.txt in your favorite text editor.
    * If you came here from a Linux forum, paste the content of RESULTS.txt into your next post. Make sure to use the appropriate formating. For example in the Ubuntu forums click on the code tags (the symbol #) before pasting RESULTS.txt.

---

### Post by drunkenbrawler on 2010-01-29
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb067f032

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   312,576,704   271,610,955   5 Extended
/dev/sda5          40,965,813    81,915,434    40,949,622   7 HPFS/NTFS
/dev/sda6          81,915,498   143,347,994    61,432,497   7 HPFS/NTFS
/dev/sda7         143,348,058   204,780,554    61,432,497   7 HPFS/NTFS
/dev/sda8         204,780,618   312,576,704   107,796,087   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe99ee99e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sdb2          40,965,750    78,027,704    37,061,955  83 Linux
/dev/sdb3          78,027,705    81,931,499     3,903,795  82 Linux swap / Solaris
/dev/sdb4          81,931,500   156,360,644    74,429,145   5 Extended
/dev/sdb5          81,931,563   156,360,644    74,429,082   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6EE03EF5395416A1                       ntfs       Media                         
/dev/sda5        73632DDA28878AF0                       ntfs       Aniket                        
/dev/sda6        0F68A3ED1258C95C                       ntfs       Miscellaneous                 
/dev/sda7        5912239A7117E226                       ntfs       Games                         
/dev/sda8        623E364F0F7F3902                       ntfs       Movies                        
/dev/sdb1        2E50F7B450F780BF                       ntfs                                     
/dev/sdb2        90d54bbd-3b53-48d4-8f21-7856c64eed83   ext4                                     
/dev/sdb3        8f68416e-1ec0-4d02-b148-f68e354a13a5   swap                                     
/dev/sdb5        0023937A0DA29709                       ntfs       Downloads                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute /fastdetect 

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 12ec1c0eec1beb2d
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                 proc         defaults                          0  0  
# / was on /dev/sdb2 during installation
UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83  /                     ext4         errors=remount-ro                 0  1  
# swap was on /dev/sdb4 during installation
UUID=8f68416e-1ec0-4d02-b148-f68e354a13a5  none                  swap         sw                                0  0  
/dev/scd1                                  /media/cdrom0         udf,iso9660  user,noauto,exec,utf8             0  0  
/dev/fd0                                   /media/floppy0        auto         rw,user,noauto,exec,utf8          0  0  
/dev/sda6                                  /media/miscellaneous  ntfs-3g      user,fmask=0111,dmask=0000        0  0  

=================== sdb2: Location of files loaded by Grub: ===================


  26.2GB: boot/grub/core.img
  26.2GB: boot/grub/grub.cfg
  24.5GB: boot/initrd.img-2.6.31-14-generic
  25.1GB: boot/initrd.img-2.6.31-16-generic
  26.4GB: boot/initrd.img-2.6.31-17-generic
  22.6GB: boot/vmlinuz-2.6.31-14-generic
  24.8GB: boot/vmlinuz-2.6.31-16-generic
  25.9GB: boot/vmlinuz-2.6.31-17-generic
  26.2GB: grub/core.img
  26.4GB: initrd.img
  25.1GB: initrd.img.old
  25.9GB: vmlinuz
  24.8GB: vmlinuz.old

```

Thanx for ur reply :)

---

### Post by kansasnoob on 2010-01-29
Try running:

```
sudo update-grub
```

Wait for it to say done!

Then post the output of:

```
cat /boot/grub/grub.cfg
```

I guess I should explain. The script shows XP is on sda1 but grub.cfg:

> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 12ec1c0eec1beb2d
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###


I just want to give grub2 a chance to sort itself out.

---

### Post by Jonasan Cope on 2010-01-29
hey drunkenbrawler,

had a similar problem myself after install. to be sure if yours is the same i need you to write down and post the string of letters and numbers which GRUB posts next to "No such device -"

if it matches my experience i might be able to help.

---

### Post by drunkenbrawler on 2010-01-29
I dont have the string right now. I'll post it in smtime. but i dont know if that will be same cause i think it maybe volume number or UUID. dunno. will post the string though. need to reboot. I think the string is the one in the 3rd post- grub.cfg file- in Windows entry.

---

### Post by drunkenbrawler on 2010-01-29
@Kansasnoob

Here is the output

```
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
set root=(hd1,2)                   
search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1                         
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1                                            
        insmod ext2                                            
        set root=(hd1,2)                                       
        search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro   quiet splash                                                                      
        initrd  /boot/initrd.img-2.6.31-17-generic                                         
}                                                                                          
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {                              
        recordfail=1                                                                       
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                            
        insmod ext2                                                                        
        set root=(hd1,2)                                                                   
        search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83            
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro single                                                                              
        initrd  /boot/initrd.img-2.6.31-17-generic                                         
}                                                                                          
menuentry "Ubuntu, Linux 2.6.31-16-generic" {                                              
        recordfail=1                                                                       
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                            
        set quiet=1                                                                        
        insmod ext2                                                                        
        set root=(hd1,2)                                                                   
        search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83            
        linux   /boot/vmlinuz-2.6.31-16-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro   quiet splash                                                                      
        initrd  /boot/initrd.img-2.6.31-16-generic                                         
}                                                                                          
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {                              
        recordfail=1                                                                       
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                            
        insmod ext2                                                                        
        set root=(hd1,2)                                                                   
        search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83            
        linux   /boot/vmlinuz-2.6.31-16-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro single                                                                              
        initrd  /boot/initrd.img-2.6.31-16-generic                                         
}                                                                                          
menuentry "Ubuntu, Linux 2.6.31-14-generic" {                                              
        recordfail=1                                                                       
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                            
        set quiet=1                                                                        
        insmod ext2                                                                        
        set root=(hd1,2)                                                                   
        search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83            
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro   quiet splash                                                                      
        initrd  /boot/initrd.img-2.6.31-14-generic                                         
}                                                                                          
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {                              
        recordfail=1                                                                       
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                            
        insmod ext2                                                                        
        set root=(hd1,2)                                                                   
        search --no-floppy --fs-uuid --set 90d54bbd-3b53-48d4-8f21-7856c64eed83            
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=90d54bbd-3b53-48d4-8f21-7856c64eed83 ro single                                                                              
        initrd  /boot/initrd.img-2.6.31-14-generic                                         
}                                                                                          
### END /etc/grub.d/10_linux ###                                                           

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 6ee03ef5395416a1
        drivemap -s (hd0) ${root}
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

---

### Post by drunkenbrawler on 2010-01-29
Problem solved.
I just did update-grub and restarted my PC to find the string of numbers and it worked.

Thank you everybody.
Just curious... wat was happening and wat happened after update?
is this the generic solution ? I mean wil this work for everybody who faces this prob? :D

and can anyone explain that RESULTS.txt file plzzzzzzz...

---

### Post by Jonasan Cope on 2010-01-29
well if its the string that follows the "search - no floppy" line then your system is failing to boot because it cannot find the floppy drive (or something like that). if you press 'e' at the grub boot options, with the xp option highlighted then you should get to see the XP boot instructions. delete the entire line containing that string and press ctrl-x. might boot then.

if thats the case you need to update the grub.cfg file to permanently remove this line. i can help you do this if you need. let me know.

---

### Post by Jonasan Cope on 2010-01-29
oh sweet, well done mate. dont know what the update did though. have fun

---

### Post by audiomick on 2010-01-29
Hi.
The short answer is that grub was looking for windows in the wrong place.

"update-grub" makes it go and have another look, and yes, that is the "generic" solution, in as much as it is the first thing to try to sort out a wrongly configured grub.

---

### Post by drunkenbrawler on 2010-01-29
yeah ok. I got that much. but i hav seen that smtime u hav to edit grub entries. how to do that in grub2? :?

---

### Post by kansasnoob on 2010-01-29
It updated the grub.cfg.

---

### Post by kansasnoob on 2010-01-29
> **drunkenbrawler said:**
> yeah ok. I got that much. but i hav seen that smtime u hav to edit grub entries. how to do that in grub2? :?

If grub2 is working properly you shouldn't have to.

---

### Post by drunkenbrawler on 2010-01-29
yeah i know it updated grub.cfg and i know now i dont have to do anything. but i was just curious about how to edit entries in grub 2 like i used to edit menu.lst in older grub

---

### Post by presence1960 on 2010-01-29
> **drunkenbrawler said:**
> yeah i know it updated grub.cfg and i know now i dont have to do anything. but i was just curious about how to edit entries in grub 2 like i used to edit menu.lst in older grub

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Read that.

---

### Post by ccrawford57 on 2010-01-29
I have the same issue, but I do not have XP running.   Just Ubuntu.    I am getting Error: no such device and then a string of numbers.    I edited the boot file in Grub as suggested, and removed the Searc-floppy line and everything booted well.   I have run the update grub command and this did not fix the problem.    How do I permanently remove the "search floppy" line?
\
thanks

---

### Post by kansasnoob on 2010-01-29
> **ccrawford57 said:**
> I have the same issue, but I do not have XP running.   Just Ubuntu.    I am getting Error: no such device and then a string of numbers.    I edited the boot file in Grub as suggested, and removed the Searc-floppy line and everything booted well.   I have run the update grub command and this did not fix the problem.    How do I permanently remove the "search floppy" line?
\
thanks

From:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

> error: no such device: 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
This error is the result of a failure of the GRUB 2 search function. There are various bugs associated with the search function. To boot into your system, highlight the OS you want to boot. Press "e" to edit the menuentry. Delete the entire "search ..." line, then CTRL-x to boot.

Once you have booted into the system, you will modify the /usr/lib/grub/grub-mkconfig_lib file in accordance with this link:
Boot Problems:search

The link referred to:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by presence1960 on 2010-01-29
ccrawford57 have you fixed it yet? The link kansasnoob gave you is right on the money and it is a simple fix.

---

### Post by ccrawford57 on 2010-01-30
this worked perfectly!   thank you.   THe only problem is that I did a software update, and it reset everything back to where it was.    I am doing the fix again, and I assume it will work fine

---

