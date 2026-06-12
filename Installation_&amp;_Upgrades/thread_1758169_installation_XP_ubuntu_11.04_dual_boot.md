---
title: "installation XP /ubuntu 11.04 dual boot"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by daemon52 on 2011-05-14
I am running windows XP and want to dual boot with ubuntu 11.04, but am having trouble with the installation

the first time i installed i managed to overwrite the MBR, at least i think that's what happened, and had to restore the windows from a back-up. So i tried to install again which i believe i did at least i can see all the ubuntu files, but i cant boot ubuntu
reading previous posts i'm sure that grub is in the wrong place but cant figure out how to go about putting it right
info from gparted
/dev/sdb1 - ntfs - flag= boot
/dev/sdb2  - extended - no flag
/dev/sdb5 - ext4 - no flag
/dv/sdb6 - linux-swap - no flag
any help would be greatly appreciated, please bear in mind that i am a total novice with linux ( it took me 2 hours to figure out how to open a terminal! and then i didnt know what to do with it LOL)
thanks in advance

---

### Post by Rubi1200 on 2011-05-14
Hi and welcome to the forums :-)

Please do the following so we can get a better overview of the current state of the system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by YesWeCan on 2011-05-14
> **daemon52 said:**
> any help would be greatly appreciated, please bear in mind that i am a total novice with linux ( it took me 2 hours to figure out how to open a terminal! and then i didnt know what to do with it LOL)
thanks in advance
Don't feel bad, it took me 2 months after first trying Ubuntu to transition from "This is an impossibly complicated and unintuitive nightmare" to "Ah. Now I get it. This is so much better than Windows!"

Grub and the Ubuntu installer, however, still make me wince sometimes. Some background for a novice:

The MBR (master boot record) is just 512 bytes in the very first sector of a DOS formatted disk. It tells the bios which partitions exist and where they are and which one to look for a bootloader in (the one with the boot flag set). It is sort of limited because it can only specify 4 partitions.

Grub is an alternative bootloader to the Windows one. Either can boot the other (which isn't publicized in here much) and if I were doing a dual boot on the same disk I would choose to forego Grub and add Ubuntu to my Windows bootloader. But this is another story.

The way Ubuntu installer works by default, the Grub bootloader is in 3 sections in different places. The main bit is inside the root partition of Ubuntu itself, in /boot/grub. Another intermediate bit is in the sectors immediately after the MBR sector where other OSes don't normally write anything, and finally Grub replaces the standard MBR code with it's own custom code that Windows does not recognize (Windows will sometimes repair it back to standard if it thinks there is a problem).

All 3 sections of Grub are needed for it to work at all. So if you happen to delete your Ubuntu partition one part is erased and Grub won't work. So you cannot boot anything. If you use the Windows bootloader to boot Ubuntu then no problem if you delete Ubuntu. But if you delete Windows you won't be able to boot Ubuntu. Either MBR can be recovered by using Windows CD or using Ubuntu CD as appropriate.

Sometimes some versions of Windows will not do updates correctly if the MBR is not the standard DOS one. I suspect XP is probably ok (no updates anymore anyhow) but Vista barfs. Windows 7 is probably almost always ok but I have read reports where Win7 does a self-repair for some reason and reinstates the MBR.

Personally, I like to keep Windows as untouched as possible - it is a very sensitive OS and will throw its toys out of the pram. So I put them on separate disks and actually unplug the Windows disk during Ubuntu install to make sure it isn't accidentally Grubbed. If I had both OSes on one disk I would not install Grub to that disk. I would install it to a USB stick and boot off the stick. This is actually very easy - just install Ubuntu to a USB stick and then boot off it into Ubuntu and then run 'sudo update-grub' from a terminal and the OSes on your HD (XP and Ubuntu) will be added to the boot menu of the USB stick. And if you remove the USB stick your OS will default to booting XP as normal.

Grub is very good and it is not Microsoft which is partly why it gets much more air-time here than using the Windows bootloader to boot Ubuntu.

---

### Post by daemon52 on 2011-05-14
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for ccdc2.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   402,572,834   402,572,772   7 HPFS/NTFS
/dev/sdb2         402,573,310   488,396,799    85,823,490   5 Extended
/dev/sdb5         402,573,312   484,204,543    81,631,232  83 Linux
/dev/sdb6         484,206,592   488,396,799     4,190,208  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4E50701950700A4B                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9AF4AD79F4AD57F1                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        e3c4dd7c-6814-4b6f-81ea-65b80504032a   ext4                                     
/dev/sdb6        9f2b7ed6-cf53-42bd-8e53-4dc69e39a20c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/e3c4dd7c-6814-4b6f-81ea-65b80504032a ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sdb1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root e3c4dd7c-6814-4b6f-81ea-65b80504032a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root e3c4dd7c-6814-4b6f-81ea-65b80504032a
set locale_dir=($root)/boot/grub/locale
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
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root e3c4dd7c-6814-4b6f-81ea-65b80504032a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=e3c4dd7c-6814-4b6f-81ea-65b80504032a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root e3c4dd7c-6814-4b6f-81ea-65b80504032a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=e3c4dd7c-6814-4b6f-81ea-65b80504032a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root e3c4dd7c-6814-4b6f-81ea-65b80504032a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root e3c4dd7c-6814-4b6f-81ea-65b80504032a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 9AF4AD79F4AD57F1
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=e3c4dd7c-6814-4b6f-81ea-65b80504032a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=9f2b7ed6-cf53-42bd-8e53-4dc69e39a20c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 221.3GB: boot/grub/core.img
 219.1GB: boot/grub/grub.cfg
 207.2GB: boot/initrd.img-2.6.38-8-generic
 221.3GB: boot/vmlinuz-2.6.38-8-generic
 207.2GB: initrd.img
 221.3GB: vmlinuz
```

---

### Post by YesWeCan on 2011-05-14
It appears you have two HDs,
sda has XP and Grub in the MBR
sdb has Win7 and Ubuntu and DOS MBR

You can't boot XP because Grub is looking on sda for its other files instead of looking on sdb in the Ubuntu partition.
Presumably you can boot sdb and go straight into Windows 7?

Do you want grub in the MBR of sda? This may have been done by the Ubuntu installer by default and may not be what you intended (another wince). If you hadn't intended this:
1) Unplug the XP HD (not strictly necessary but simplifies things)
2) Boot a live CD/USB.
3) Follow the instructions under "Reinstalling from LiveCD" here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
4) Shut down. Reconnect XP HD. Reboot. Set bios to boot Win7 HD first.
5) In Ubuntu, 'sudo update-grub'.

On next reboot you should get a Grub menu offering a choice of XP, Win7, Ubuntu.

If you want to restore the DOS MBR on the XP HD you can use an XP CD to repair it or, in Ubuntu, install lilo and repair it:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
This means you can choose to boot XP directly from bios.

-----OR-----
Boot into Win7. Download the free app EasyBCD. Run it and add the Ubuntu OS to the Windows bootloader.
Reboot and choose Ubuntu.
Presumably, the Win7 boot menu already had XP on it. Or it could have...
Then repair XP MBR as above if you wish.

---

### Post by Normank on 2011-05-14
Hi Guys

I have a similar problem but getting mighty confused.

I was dual booting with xp on one hard disk and ubuntu on second hard disk.
Due to issues I had to re-install xp and now can't access second hard disk at all.
Any help greatly appreciated as am missing linux (more than I did xp.

---

### Post by YesWeCan on 2011-05-14
> **Normank said:**
> Hi Guys

I have a similar problem but getting mighty confused.

I was dual booting with xp on one hard disk and ubuntu on second hard disk.
Due to issues I had to re-install xp and now can't access second hard disk at all.
Any help greatly appreciated as am missing linux (more than I did xp.
I am guessing that when you installed Ubuntu, the installer put the Grub MBR on your XP disk. You accessed the 2nd disk using Grub. So when you reinstalled XP it removed the Grub MBR and now you can only boot XP, right?

You also need to install Grub on the 2nd HD. So you need to follow my instructions 1) to 5) above.

Would you like to try that and then post if you get stuck?

---

### Post by YesWeCan on 2011-05-14
BTW this recovery is even easier if you already have Grub2 installed somewhere. For example, if you install Ubuntu to a USB drive or stick. You only need a 3GB stick.

In this case, you can boot the USB into Ubuntu and simply add all you existing OS's to the Grub menu of the USB drive. With one command 'sudo update-grub'.

Then you can boot into the orphaned Ubuntu on your HD and reinstall grub from there:
'sudo update-grub'
'sudo grub-install /dev/sdn'
where n is the letter of your Ubuntu HD...or whichever HD you want the Grub MBR written to.


It would be rather useful if the Ubuntu live CD allowed you to boot an OS in any partition on any HD but I don't think it can do that. :(

---

### Post by daemon52 on 2011-05-15
that solved it 
many thanks

---

### Post by Gajet on 2011-06-21
I am also running windows XP. then my friend promote linux ubuntu to me. so i wanna try it. but when i want install it doesnt detect any OS in my laptop. i only have 1 HD and have 2 partition. but ubuntu setup also dont detect my partition (format NTFS). i try install ubuntu many times but still doesnt detect my XP OS. if can i want to make it dual boot with XP. Help me pls. i really want to try ubuntu. thanks in advance.

---

### Post by Rubi1200 on 2011-10-26
Thread closed.

@Gajet; if you still need help please start your own thread.

---

