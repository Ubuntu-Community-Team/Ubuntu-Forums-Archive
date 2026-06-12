---
title: "Windows doesn't start in grub"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by Parrallax on 2010-08-03
Hello Everyone,

Well I'm new to the world of dual booting Ubuntu, so please bare with me. My computer is currently running windows 7 64-bit, and I'm trying to install Ubuntu 32-bit to run beside it.
So I've created a boot disk, and I try to install Ubuntu. The weird thing is when I get to the frame that says "Prepare disk space" it correctly shows that I have windows 7 on the computer, but it shows it's on the wrong drive. In fact within the Ubuntu installer it doesn't even show the physical drive that windows is on, it only find the other two drives. If I load up System>Administration>Disk Utility then I can see all 3 physical hard drives and all the partitions on them, but not under the Ubuntu installer.
So I tried installing Ubuntu onto one of the other physical hard drives and that seemed to go just fine. The only problem is now when I boot, the only way I can swap operating systems is to go into my BIOS and change the boot order of my hard drives. If the hard drive with Windows is higher in the boot priority, it will boot windows, no problem. If the hard drive with Ubuntu on it is higher, then it takes me to grub, where it correctly shows windows 7 and ubuntu. Only problem is when I choose windows 7 all I get is a blinking cursor and nothing happens. If I choose Ubunutu it boots correctly and everything works. So in a way I do kind of have them both working, but it'd be nice not to have to go into my BIOS just to change operating systems.
Can anyone tell me what's happening here? I'm guessing that grub's problem is that the Ubuntu installer identifies the wrong drive that Windows is installed on, so when I pick Windows from grub it goes to the wrong drive. Can I fix grub manually? Or is there some compatibility issue between Windows 7 64-bit and Ubuntu 32-bit that is causing this conflict? Any help would be fantastic.

Sincerely,
Bob

---

### Post by Parrallax on 2010-08-03
Please? Does anyone know what's going on here, or can I provide more information?

---

### Post by Elmer Fudd on 2010-08-03
Since the experts haven't chimed in. I'll try.

Please confirm that you have 3 physical (not logical) drives.
Is raid set up on your system?

---

### Post by Parrallax on 2010-08-03
Thanks for the effort! I really appreciate it.
Yes I have three physical drives. A couple of them have partitions, but there is three physical drives.
The problem is that Ubuntu installer doesn't seem to find the physical drive that the windows installation is on, despite the fact that the Disk Manager can find it.

---

### Post by Parrallax on 2010-08-03
Ok, one thing I tried was to switch the SATA ports that each drive is plugged into, just to see what happens.
I go the GParted, and check, and sure enough the physical drive that windows is on has changed to sda (it was sdb) I then go to the ubuntu installer and now once again it's not finding that particular drive. It finds the other two (sdb and sdc) and once again thinks that Windows is on the wrong drive (sdb this time, last time it thought it was sda).
I don't understand why All the rest of ubuntu can find that drive, just not the bloody installer.

Oh and in answer to your question, there's no RAID on the drives.

---

### Post by Elmer Fudd on 2010-08-03
Would you boot from Ubuntu that you did get installed.
gedit /boot/grub/grub.cfg

copy and post the section that begins

### BEGIN /etc/grub.d/30_os-prober ###
and ends
### END /etc/grub.d/30_os-prober ###

---

### Post by Elmer Fudd on 2010-08-03
do an update-grub before looking at grub.cfg

sudo update-grub

---

### Post by Parrallax on 2010-08-03
Hello again.
Ok, so here it is

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 83d917e58d930f9f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

Now the problem is that the Windows install isn't on sdb1, it's on sda1, so I'm assuming I need to edit this file so that it says

set root='(hd0,1)' 

is that right? Is there a right way and a wrong way to do this?

---

### Post by Elmer Fudd on 2010-08-03
While we're waiting for the experts to get back from dinner, that's what I would try. I suspect that it won't work but worth a try.

To edit the file you should:

gksu gedit /boot/grub/grub.cfg

Before that, would you post a screen shot of the Disk Utility window with the windows partition selected.

Am going to dinner. Will check on your progress later

---

### Post by presence1960 on 2010-08-03
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Parrallax on 2010-08-03
Hi, thanks for the help again guys.

At the moment I'm trying to fix my Windows boot on the drive that it's on, so I've got the windows startup repair going (I'm on my laptop) it was working earlier, but there's been a few attempts at trying to install Ubuntu so i think it died somewhere in there.

Once that's done I'll get that information you asked for.
Bob

---

### Post by Parrallax on 2010-08-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Lilo is installed in the MBR of /dev/mapper/nvidia_ebaihcdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

nvidia_ebaihcdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   104,450,047   104,448,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   781,417,664   781,417,602   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   195,522,559   195,520,512  83 Linux
/dev/sdc2         195,524,606   196,694,015     1,169,410   5 Extended
/dev/sdc5         195,524,608   196,694,015     1,169,408  82 Linux swap / Solaris
/dev/sdc3         653,042,250   976,768,064   323,725,815   7 HPFS/NTFS


Drive: nvidia_ebaihcdb ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_ebaihcdb: 203.9 GB, 203928043520 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398296960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_ebaihcdb1   *          2,048   104,450,047   104,448,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/nvidia_ebaihcdb1 DC7C1FF27C1FC5E4                       ntfs                                     
/dev/mapper/nvidia_ebaihcdb: PTTYPE="dos" 
/dev/sda1        DC7C1FF27C1FC5E4                       ntfs                                     
/dev/sda                                                nvidia_raid_member                               
/dev/sdb1        83D917E58D930F9F                       ntfs       Data                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        970fd840-18c5-4120-81af-4d301bedc4b2   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc3        560EBFD24ABDC5DB                       ntfs       New Volume                    
/dev/sdc5        79fa49d5-bb8b-4fca-955c-3f24b2fc3922   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 970fd840-18c5-4120-81af-4d301bedc4b2
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 970fd840-18c5-4120-81af-4d301bedc4b2
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 970fd840-18c5-4120-81af-4d301bedc4b2
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=970fd840-18c5-4120-81af-4d301bedc4b2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 970fd840-18c5-4120-81af-4d301bedc4b2
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=970fd840-18c5-4120-81af-4d301bedc4b2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 970fd840-18c5-4120-81af-4d301bedc4b2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 970fd840-18c5-4120-81af-4d301bedc4b2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 83d917e58d930f9f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7 on sba1" {
        insmod ntfs
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 83d917e58d930f9f
        chainloader +1
}


### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=970fd840-18c5-4120-81af-4d301bedc4b2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=79fa49d5-bb8b-4fca-955c-3f24b2fc3922 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  67.0GB: boot/grub/grub.cfg
  21.8GB: boot/initrd.img-2.6.32-24-generic-pae
  21.7GB: boot/vmlinuz-2.6.32-24-generic-pae
  21.8GB: initrd.img
  21.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  82 18 ea ea fa ff ff ff  00 00 00 00 00 00 e4 20  |............... |
00000010  a2 18 fa b2 a2 aa ff ff  00 00 00 00 00 00 04 29  |...............)|
00000020  c3 18 8b ab af eb ff ff  00 00 00 00 00 00 04 29  |...............)|
00000030  c3 18 fe 5a 7f ef ff ff  00 00 00 00 00 00 e3 20  |...Z........... |
00000040  a3 18 b7 af ea a2 ff ff  00 00 00 00 00 00 04 29  |...............)|
00000050  82 10 af aa aa aa ff ff  00 00 00 00 00 00 c3 20  |............... |
00000060  82 10 b8 d8 d8 58 ff ff  00 00 00 00 00 00 c3 20  |.....X......... |
00000070  82 10 fe fe ff ab ff ff  00 00 00 00 00 00 c3 18  |................|
00000080  82 18 aa aa e0 ea ff ff  00 00 00 00 00 00 c3 18  |................|
00000090  82 18 ab fa 57 d5 ff ff  00 00 00 00 00 00 c3 18  |....W...........|
000000a0  61 10 aa aa af aa ff ff  00 00 00 00 00 00 a3 18  |a...............|
000000b0  a2 18 ab aa ef ff ff ff  00 00 00 00 00 00 a3 18  |................|
000000c0  82 10 aa aa ae af ff ff  00 00 00 00 00 00 a3 18  |................|
000000d0  82 10 2e 2e 2e 2c ff ff  00 00 00 00 00 00 e4 20  |.....,......... |
000000e0  c3 18 a5 ad bd ed ff ff  00 00 00 00 00 00 aa 52  |...............R|
000000f0  00 00 57 57 57 57 ff ff  00 00 00 00 00 00 00 00  |..WWWW..........|
00000100  00 00 00 00 00 00 ff ff  00 00 00 00 00 00 00 00  |................|
*
00000140  00 00 00 00 00 00 ff ff  00 00 00 00 00 00 00 18  |................|
00000150  00 00 55 55 b5 55 ff ff  00 00 00 00 00 00 00 38  |..UU.U.........8|
00000160  00 00 55 55 57 55 ff ff  00 00 00 00 00 00 00 00  |..UUWU..........|
00000170  00 00 00 00 00 00 ff ff  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 ff ff  00 00 00 00 00 00 e7 39  |...............9|
00000190  00 00 a9 29 a9 a9 ff ff  00 00 00 00 00 00 86 31  |...)...........1|
000001a0  82 10 0a 00 aa 5e ff ff  00 00 00 00 00 00 86 31  |.....^.........1|
000001b0  41 08 e8 78 57 d5 ff ff  00 00 00 00 00 00 00 fe  |A..xW...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d8 11 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Parrallax on 2010-08-03
Wow am I talented at making things worse.
Ok, so I somehow managed to kill my windows boot sector. And using the instructions I found on this thread
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


didn't work, So instead I installed Lilo using the instructions about half way down this post
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
And that at least worked at getting my Windows back, but of course now predictably now I can't boot to Ubuntu at all. I'm guessing this means I need to reinstall Grub and hopefully this time get it correctly pointing to the Windows installation on sda1.

I know I'm probably only making this hard for you guys, I'm sorry.

---

### Post by oldfred on 2010-08-03
nvidia_raid_member

Do you or did you have sda in RAID. Some systems are shipped with RAID set in BIOS even with one drive.

I refer to this if you do [COLOR=Red]not want [/COLOR]your RAID as the hidden settings cause problems.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

You can and should reinstall grub2 to sdc. Your link on reinstalling boot loaders has general instructions for that.

Install from LiveCD install on sdc1 and want grub2 in drive sdc's MBR:
Find linux partition, change sdc1 if not correct, and/or even sda or sdb wanted:
sudo fdisk -l
Should show sdc1 per boot script:
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sdc

You then have to change BIOS to boot sdc which is one of the two 203.9GB drives. You may have to try both becuase BIOS will not tell you which is which.

---

### Post by Parrallax on 2010-08-04
Thankyou!

That was it, the raid. I couldn't find any RAID settings in my BIOS, but that hard drive in particular has been in several different boxes with different motherboards so it very well could be a kick over from those old days. I've never intentionally put it in a raid, but as you said some motherboards will have them on by default.
But I entered the commands you gave me to get rid of the raid stuff, and then reinstalled grub onto sdc and now grub correctly loads up Windows 7. Thanks so much for your help.

Bob

---

