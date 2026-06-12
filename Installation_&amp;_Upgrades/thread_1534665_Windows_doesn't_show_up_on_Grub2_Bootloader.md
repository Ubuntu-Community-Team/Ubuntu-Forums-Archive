---
title: "Windows doesn't show up on Grub2 Bootloader"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by Mistiq Dragon on 2010-07-19
Hi, 
    I'm relatively new to Ubuntu, I've installed it in Virtual  Box and through Wubi on  other computers but this was the first time  that I've done a live install on my production computer.  I had problems  from the get go, I was using a Live CD of 10.04 (64 bit AMD)  to  install it and when it got to the part about choosing a partition no  drives would show up at all.  Eventually after some searching around, I  discoverd that Using an Alternate install CD would work.  I did that,  installing Ubuntu into one of the free partitions I had set up prior to  this.  Eventually my system turned on but the monitor went to sleep so I  had to hit E on the grubmenu and change something to nomodeset (or  something like that) so that I could see the screen.  I installed Compiz  and it was all good from there.


Except for One issue,  I can  not boot Into windows at all, it doesn't show up on the bootloader even  though the partition shows up in Gparted.  I've tried updating Grub2  with no results, here are the results of Sudo fdisk -l

[I]Disk  /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track,  48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector  size (logical/physical): 512 bytes / 512 bytes
I/O size  (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

    Device Boot      Start         End      Blocks   Id  System
/dev/sda1    *           1        4132    33190258+   7  HPFS/NTFS
/dev/sda2             4133       39524   284285619    f  W95 Ext'd (LBA)
/dev/sda3            47485       48641     9293602+   7  HPFS/NTFS
/dev/sda5            15458       39524   193318177+   7  HPFS/NTFS
/dev/sda6             4133       14991    87221248   83  Linux
/dev/sda7            14991       15457     3737600   82  Linux swap / Solaris

Partition  table entries are not in disk order
[/I]
and from my searching  I've used the script that everybody recommends in troubleshooting issues  like this,
[I]============================= Boot Info Summary:  ==============================

 => Grub 2 is installed in the  MBR of /dev/sda and looks on the same drive in 
    partition #6 for  /boot/grub.

sda1:  _________________________________________________________________________

     File system:       ntfs
    Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  Windows 7
    Boot files/dirs:   /bootmgr  /Boot/BCD /Windows/System32/winload.exe 
                        /wubildr.mbr /wubildr

sda2:  _________________________________________________________________________

     File system:       Extended Partition
    Boot sector type:  Unknown
     Boot sector info:  

sda5:  _________________________________________________________________________

     File system:       ntfs
    Boot sector type:  Windows XP
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  
    Boot files/dirs:    /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                        /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi:  _________________________________________________________________________

     File system:       
    Boot sector type:  Unknown
    Boot  sector info:  
    Mounting failed:
mount: unknown filesystem type  ''

sda6:  _________________________________________________________________________

     File system:       ext4
    Boot sector type:  -
    Boot sector  info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot  files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7:   _________________________________________________________________________

     File system:       
    Boot sector type:  -
    Boot sector  info:  
    Mounting failed:
mount: unknown filesystem type ''
mount:  unknown filesystem type ''

sda3:  _________________________________________________________________________

     File system:       ntfs
    Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

===========================  Drive/Partition Info: =============================

Drive: sda  ___________________  _____________________________________________________

Disk  /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track,  48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 =  512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition   Boot         Start           End          Size  Id System

/dev/sda1     *             63    66,380,579    66,380,517   7 HPFS/NTFS
/dev/sda2           66,381,822   634,953,059   568,571,238   f W95 Ext d (LBA)
/dev/sda5          248,316,705   634,953,059   386,636,355   7 HPFS/NTFS
/dev/sda6           66,381,824   240,824,319   174,442,496  83 Linux
/dev/sda7          240,826,368   248,301,567     7,475,200  82 Linux swap / Solaris
/dev/sda3          762,830,460   781,417,664    18,587,205   7 HPFS/NTFS


blkid  -c /dev/null:  ____________________________________________________________

Device            UUID                                   TYPE        LABEL                         

/dev/loop0                                               squashfs                                 
/dev/sda1         ECDC8D24DC8CEA62                       ntfs       Windows  7                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3         2C88743C8874071C                       ntfs       Back  Up?                      
/dev/sda5         01CADE5E9157E870                       ntfs       The  Goods                     
/dev/sda6         ccd274de-b814-4fe1-ae0f-9d1682e2b9c4    ext4                                     
/dev/sda                                                 nvidia_raid_member                               
error: /dev/sdb:  No medium found
error: /dev/sdc: No medium found
error: /dev/sdd:  No medium found
error: /dev/sde: No medium found

============================  "mount | grep ^/dev  output: ===========================

Device            Mount_Point              Type       Options

aufs              /                        aufs       (rw)
/dev/sr0          /cdrom                   iso9660    (ro,noatime)
/dev/loop0        /rofs                    squashfs   (ro,noatime)


===========================  sda6/boot/grub/grub.cfg: ===========================

#
# DO  NOT EDIT THIS FILE
#
# It is automatically generated by  /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and  settings from /etc/default/grub
#

### BEGIN  /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
   load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
   set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set  prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function  savedefault {
  if [ -z ${boot_once} ]; then
     saved_entry=${chosen}
    save_env saved_entry
  fi
}

function  recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then  if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod  ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set  ccd274de-b814-4fe1-ae0f-9d1682e2b9c4
if loadfont  /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod  gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ;  else
    # For backward compatibility with versions of terminal.mod  that don't
    # understand terminal_output
    terminal gfxterm
   fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy  --fs-uuid --set ccd274de-b814-4fe1-ae0f-9d1682e2b9c4
set  locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if  [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set  timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN  /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set  menu_color_highlight=black/light-gray
### END  /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux  ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu  --class gnu-linux --class gnu --class os {
    recordfail
     insmod ext2
    set root='(hd0,6)'
    search --no-floppy  --fs-uuid --set ccd274de-b814-4fe1-ae0f-9d1682e2b9c4
    linux     /boot/vmlinuz-2.6.32-23-generic  root=UUID=ccd274de-b814-4fe1-ae0f-9d1682e2b9c4 ro   quiet splash
     initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu,  with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
     set root='(hd0,6)'
    search --no-floppy --fs-uuid --set  ccd274de-b814-4fe1-ae0f-9d1682e2b9c4
    echo    'Loading Linux  2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic  root=UUID=ccd274de-b814-4fe1-ae0f-9d1682e2b9c4 ro single 
    echo     'Loading initial ramdisk ...'
    initrd     /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux  2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class  os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
     search --no-floppy --fs-uuid --set ccd274de-b814-4fe1-ae0f-9d1682e2b9c4
     linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=ccd274de-b814-4fe1-ae0f-9d1682e2b9c4 ro   quiet splash
     initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu,  with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
     set root='(hd0,6)'
    search --no-floppy --fs-uuid --set  ccd274de-b814-4fe1-ae0f-9d1682e2b9c4
    echo    'Loading Linux  2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=ccd274de-b814-4fe1-ae0f-9d1682e2b9c4 ro single 
    echo     'Loading initial ramdisk ...'
    initrd     /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux  ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory  test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
     search --no-floppy --fs-uuid --set ccd274de-b814-4fe1-ae0f-9d1682e2b9c4
     linux16    /boot/memtest86+.bin
}
menuentry "Memory test  (memtest86+, serial console 115200)" {
    insmod ext2
    set  root='(hd0,6)'
    search --no-floppy --fs-uuid --set  ccd274de-b814-4fe1-ae0f-9d1682e2b9c4
    linux16     /boot/memtest86+.bin console=ttyS0,115200n8
}
### END  /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober  ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if  keystatus --shift; then
      set timeout=-1
    else
      set  timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
       set timeout=0
    fi
  fi
fi
### END  /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
#  This file provides an easy way to add custom menu entries.  Simply type  the
# menu entries you want to add after this comment.  Be careful  not to change
# the 'exec tail' line above.
### END  /etc/grub.d/40_custom ###

===============================  sda6/etc/fstab: ===============================

# /etc/fstab:  static file system information.
#
# Use 'blkid -o value -s UUID'  to print the universally unique identifier
# for a device; this may  be used with UUID= as a more robust way to name
# devices that works  even if disks are added and removed. See fstab(5).
#
# <file  system> <mount point>   <type>  <options>        <dump>  <pass>
proc            /proc           proc     nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during  installation
UUID=ccd274de-b814-4fe1-ae0f-9d1682e2b9c4  /               ext4    errors=remount-ro 0       1
# swap was on  /dev/sda7 during installation
#UUID=b96cbb8e-50aa-49e2-9eb5-843bb821aa49  none            swap    sw              0       0
/dev/mapper/cryptswap1  none swap sw 0 0

=================== sda6: Location of files  loaded by Grub: ===================


  64.1GB:  boot/grub/core.img
  73.0GB: boot/grub/grub.cfg
  64.3GB:  boot/initrd.img-2.6.32-21-generic
  64.3GB:  boot/initrd.img-2.6.32-23-generic
  34.2GB:  boot/vmlinuz-2.6.32-21-generic
  64.3GB:  boot/vmlinuz-2.6.32-23-generic
  64.3GB: initrd.img
  64.3GB:  initrd.img.old
  64.3GB: vmlinuz
  34.2GB: vmlinuz.old
===========================  Unknown MBRs/Boot Sectors/etc =======================

Unknown  BootLoader  on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff  ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff  ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 07  fe ff ff 23 1b  d8 0a 43 9a 0b 17 00 fe  |......#...C.....|
000001d0   ff ff 05 fe ff ff 01 00  00 00 01 c8 65 0a 00 00  |............e...|
000001e0   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0   00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown  BootLoader  on sda5/Wubi

00000000  30 30 30 30 30 30 30 30  30  30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=======Devices  which don't seem to have a corresponding hard drive==============

sdb  sdc sdd sde [/I]





I would greatly appreciate any  help that anybody could offer,  I have a project due tomorrow and all  the pertinent information is on my Google Chrome browser in Windows

---

### Post by oldfred on 2010-07-19
Did you try?

sudo update-grub

Was this drive ever part of a RAID set? Do you have RAID turned on in BIOS even if you are not using it. That was why you had troubles installing.

If you have RAID do not run this:
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

If you want to reinstall a windows boot loader. You will have to reinstall grub2 if you want to get back to Ubuntu.
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Mistiq Dragon on 2010-07-20
I did try update-grub and it didn't recognise my windows partition,  the hard drive I'm using was set up as a Raid in the bios even though it's never been used in a raid array(?) but I'm not sure but I think after I finally got Ubuntu installed I had to do something like Sudo Dmraid to get the system working correctly.

I'm about to try what you advised but I just want to make sure I understand this correctly, ingore the first part of your advice due to this having been a raid setup and do the 2nd part starting from Restore basic windows Boot loader right?

If I have universe enabled already in my Sources(?)  then I can just do the spt-get install lilo right and then follow the directions in your last link?

---

### Post by oldfred on 2010-07-20
The install of lilo to the MBR will let you directly boot windows if the windows is working. That was to quickly get you into windows if you wanted. 
But the lilo boot loader will not boot Ubuntu (unless grub is installed in the partition and the boot flag is moved as lilo is an older linux boot loader).

If windows does not boot with the lilo boot loader then you will have to do windows repairs which may remove the wubi boot from your windows.

---

### Post by Mistiq Dragon on 2010-07-20
Thank you so much, I restarted the computer this morning and Windows came back up like it had never been missing.  I should be working on this project for the rest of the day, but once I'm done with it, what do I need to do to get this into a true dual boot system?

I'm pretty sure I need to reinstall Grub2 (using the link you provided) but what should I do to make sure that Windows shows up on the Grub Bootloader?

---

### Post by mittugrace on 2010-07-20
Dynamic loading of modules in order to extend itself at the run time rather than at the build time.
Portability for various architectures.
Internationalization. This includes support for non-ASCII character code, message catalogs like gettext, fonts, graphics console, and so on.
Real memory management, to make GNU GRUB more extensible.
Modular, hierarchical, object-oriented framework for file systems, files, devices, drives, terminals, commands, partition tables and OS loaders.
Cross-platform installation which allows for installing GRUB from a different architecture.
Rescue mode saves unbootable cases. Stage 1.5 was eliminated.
Fix design mistakes in GRUB Legacy, which could not be solved for backward-compatibility, such as the way of numbering partitions.
I do not issue any guarantee that this will work for you!

_______________________________________


[portable lectern ](http://www.lecternsandpodiums.com) [indoor fountain](http://www.fountainspirit.com)

---

### Post by mittugrace on 2010-07-20
falko@falko-desktop:~$ sudo upgrade-from-grub-legacy
[sudo] password for falko:

Installing GRUB to Master Boot Record of your first hard drive ...

Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)        /dev/sda


_____________________________________


[portable lectern ](http://www.lecternsandpodiums.com) [indoor fountain](http://www.fountainspirit.com)

---

### Post by mittugrace on 2010-07-20
This is too complicated.

A better way is:

In synaptic or using apt-get or aptitude, install package grub2. Accept the message to chainload from menu.lst
Reboot and check that the system starts OK
Optional, recommended: "sudo upgrade-from-grub-legacy", as advised in step 1
Optional, if you have extra OSes: Convert any menu items from menu.lst for other OSes to entries in /etc/grub.d/40_custom as per [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2). Run command "sudo update-grub". Reboot and check that the extra menu items appear. Remove /boot/grub/menu.lst* as also advised in step 1.

_________________________________


[portable lectern ](http://www.lecternsandpodiums.com) [indoor fountain](http://www.fountainspirit.com)

---

### Post by Mistiq Dragon on 2010-08-03
Ok, I didn't understand any of those last instructions. 

My situation was that I attempted to dual boot Ubuntu, Ubuntu eventually started working on my computer but Windows no longer showed up on the bootloader. I tried updating grub, grub2, doing the os prober thing and etc.... None of that worked.

Oldfred helped me get rid of Ubuntu's bootloader by using the sudo lilo command. I finished the majority of my project, now I'm ready to go back to dual booting again. 

So what I need to know is how to get the Grub2 bootloader back BUT with Windows 7 showing in the proper place. I'm pretty sure that I'll have to use a live Cd to install Grub2 but I need to have Windows 7 show up. 

So can anybody help me with that.
I have the results from sudo fdisk and running that script in my very first post. Helping me set this computer up properly would be greatly appreciated.

---

### Post by oldfred on 2010-08-03
If the lilo install let you boot windows, then windows is working fine. I do not know why the osprober would not find it. But lets try again. IF necessary we can add a manual boot stanza.

Install from LiveCD install on sda6 and want grub2 in drive sda's MBR:
Find linux partition, change sda6 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Once booted into Ubuntu

sudo update-grub

---

### Post by Mistiq Dragon on 2010-08-09
Sorry I was gone so long, I had a surprise trip come up and didn't get back until yesterday.   
I followed your directions (I think)  I just entered all your commands into the Terminal
"[I]sudo fdisk -l
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Once booted into Ubuntu

sudo update-grub[/I]  "

Unfortunately, I'm back to the exact same issue I started off with.  Ubuntu with no Windows showing up in the bootloader.  Actually the bootloader doesn't even show up anymore(I remember that you can press something during boot to show the bootloader but I've been away from Ubuntu to long to remember it)  Plus when I did the update-grub, it only shows linux kernels and no Windows.

So can you think of anything that may be the issue?
If worst comes to worst, I'm not all that adverse to formatting this partition and either reinstalling Ubuntu or I'm strongly leaning towards Linux Mint 9 KDE instead.  
My main concern is that I'm able to boot into whichever OS necessary whenever I want to.

---

### Post by oldfred on 2010-08-09
Did you ever run the command in post #2?
sudo dmraid -E -r /dev/sda
 Then run 
sudo update-grub

If above does not work:
Grub2 is really good at finding windows so I do not know why it is not working here.

We can manually add a windows stanza to 40_custom.

menuentry "Microsoft Windows 7 (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set *ECDC8D24DC8CEA62*
    drivemap -s (hd0) ${root}
    chainloader +1
}

Copy the above entry and paste into:
gksudo gedit /etc/grub.d/40_custom

after saving :
sudo update-grub

---

### Post by Mistiq Dragon on 2010-08-09
> **oldfred said:**
> [I]Did you ever run the command in post #2?
sudo dmraid -E -r /dev/sda
 Then run 
sudo update-grub
[/I] 
I'[SIZE=1]**m almost positive I did, I started to try it again but I got a prompt asking "Do you really want to erase "nvidia" ondisk metadata on /dev/sda ? [y/n]"  which didn't happen the first time.  I get the feeling that I'll erase something to do with my graphics card.  Should I go ahead and do this or is that not supposed to pop up?**[/SIZE]


If above does not work:
Grub2 is really good at finding windows so I do not know why it is not working here.

We can manually add a windows stanza to 40_custom.

menuentry "Microsoft Windows 7 (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set *ECDC8D24DC8CEA62*
    drivemap -s (hd0) ${root}
    chainloader +1
}

Copy the above entry and paste into:
[COLOR=DarkOrange]_gksudo gedit /etc/grub.d/40_custom_[/COLOR]

**This part (gksudo etc...) is that something that I type into the terminal and then a text file will pop up that I paste the Windows stanza in or am I completely off?**
after saving :
sudo update-grub


Thank You

---

### Post by oldfred on 2010-08-10
No that nvidia is the mapper or RAID that leaves a setting on the hard drive that interferes with grub. That may be the entire problem. So this and you probably do not have to paste the custom entry into 40_custom. run sudo update-grub after deleting the RAID data.

This will open your current 40_custom in administrative mode (gksudo or sudo for graphic applications) so you can edit it. 40_custom just has a couple of lines. Add your windows stanza lines to 40_custom. After the update-grub then when you reboot that will add a new menu item to your grub menu.

---

### Post by Mistiq Dragon on 2010-08-10
> **oldfred said:**
> No that nvidia is the mapper or RAID that leaves a setting on the hard drive that interferes with grub. That may be the entire problem. So this and you probably do not have to paste the custom entry into 40_custom. run sudo update-grub after deleting the RAID data.

This will open your current 40_custom in administrative mode (gksudo or sudo for graphic applications) so you can edit it. 40_custom just has a couple of lines. Add your windows stanza lines to 40_custom. After the update-grub then when you reboot that will add a new menu item to your grub menu.




Well.............. I ran the sudo dmraid etc...., updated Grub and Windows Appeared in the output.  So now I feel extremely stupid that I went through this long session with you, due to the fact that I skipped the first step in Post #2.   
Anyway, I'm very thankful for your help and patience with this situation.  :KS
I do have a few more questions that I would be happy if you could answer for me.  If I'm to continue to install Various buntu flavored Distro's, will I always need to uitlize the Sudo dmraid command?  I would assume that I can change the settings in my Bios to IDE or ACHI to avoid the problem but then my Windows won't boot up correctly.... plus what do I do if I do end up using Raid on my Next build?

Also I was wondering if you had any opinions on Linux Mint 9 KDE (Kubuntu Derivative) I'm strongly considering replacing my Lucid Lynx set up with this instead.....


Anyway Once again Thank You so much for all of your Help

---

### Post by oldfred on 2010-08-10
Once you have removed the RAID setting you should be find. Just create several 20-25GB partitions for / (root) of all the installs you want to try. Just decide which you want to be primary and leave its grub in control. Most installs will let you choose not to install grub with an advance button or other method.

I have many posts on multiple installs about having separate /data partitions as you should not share /home. I currently boot 9.10,10.04 & 10.10 with the same /data mounted in each so I can access the same files and firefox bookmarks.

I have not used Mint nor RAID. So I cannot help on those.

---

