---
title: "win 7 not booting but ubuntu does :("
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by ashintomson on 2011-10-24
hai friends

i have installed win 7 and ubuntu 11.04 in my 1 tb HDD win 7 was installed first in my c drive and ubuntu was installed in my f drive now the problem is when i select win 7 from boot screen it shows -- 
no such decive : 2cc8p09dc8fxxxxxx 
no such drive 
but ubuntu works fine 
when i searched disk utility i found that my c drive became unknown :'( 
[IMG]http://i56.tinypic.com/14a3a1.png[/IMG]

i dont know what to do it was all working fine till morning :( 
i dont want to loose my data my project files and everything was there.... 
guys please HELP!!!!!! how can i recover from this mess ..

---

### Post by westie457 on 2011-10-24
Hello, welcome to the Forum.
Before any suggestions are made go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) Follow the download and usage instructions. Post the file back here between [code] tags by clicking the # at the top of the message pane.

Thank you.

---

### Post by ashintomson on 2011-10-24
here is it 
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   314,568,764   314,568,702   7 NTFS / exFAT / HPFS
/dev/sda2         314,568,826 1,953,503,999 1,638,935,174   f W95 Extended (LBA)
/dev/sda5         314,568,828   838,850,039   524,281,212   7 NTFS / exFAT / HPFS
/dev/sda6         838,850,103 1,624,283,606   785,433,504   7 NTFS / exFAT / HPFS
/dev/sda7       1,698,681,033 1,953,503,999   254,822,967   7 NTFS / exFAT / HPFS
/dev/sda8       1,624,285,184 1,694,752,767    70,467,584  83 Linux
/dev/sda9       1,694,754,816 1,698,680,831     3,926,016  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda5        8EAC92B6AC929873                       ntfs       
/dev/sda6        06B0214FB0214691                       ntfs       
/dev/sda7        D8D22873D22857D0                       ntfs       
/dev/sda8        7d900125-2285-4159-9293-2da180de39cc   ext4       
/dev/sda9        d9fffdf3-48b9-4108-8fe0-4af9fbb9e7bb   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /media/D8D22873D22857D0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 7d900125-2285-4159-9293-2da180de39cc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 7d900125-2285-4159-9293-2da180de39cc
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 7d900125-2285-4159-9293-2da180de39cc
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=7d900125-2285-4159-9293-2da180de39cc ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 7d900125-2285-4159-9293-2da180de39cc
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=7d900125-2285-4159-9293-2da180de39cc ro single 
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
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 7d900125-2285-4159-9293-2da180de39cc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 7d900125-2285-4159-9293-2da180de39cc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 2CC8F04DC8F01734
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=7d900125-2285-4159-9293-2da180de39cc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=d9fffdf3-48b9-4108-8fe0-4af9fbb9e7bb none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 802.661266327 = 861.850972160  boot/grub/core.img                             1
 786.994403839 = 845.028806656  boot/grub/grub.cfg                             1
 774.949218750 = 832.095387648  boot/initrd.img-2.6.38-8-generic               2
 802.659538269 = 861.849116672  boot/vmlinuz-2.6.38-8-generic                  1
 774.949218750 = 832.095387648  initrd.img                                     2
 802.659538269 = 861.849116672  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by westie457 on 2011-10-24
First things first **make backups of your personal files/everything you want to keep**, just in case things go horribly wrong.

Once that has been done get your Windows install disc and boot that into recovery mode to attempt repairs of Windows. This might take 5 minutes or quite a long time depending on the Windows problems. Also it might have to be run several times until Windows reports that repairs are successful. If it still will not boot then boot the Windows disc again into repair mode, drop to a Command prompt and run ```
bootrec.exe /fixmbr
``` and rboot.

If unsuccessful try again and this time run these three commands ```
bootrec.exe /fixmbr

bootrec.exe /fixboot

bootrec.exe /rebuildbcd
```
* note there is a space between the exe and the /.

Windows should now be working properly.

Then get your Ubuntu liveCD and boot that in Try mode. Open a terminal and run ```
sudo update-grub 
```. 
Everything should now be okay.

Any problems or questions feel free to post back and ask.

Thank you.

---

### Post by ashintomson on 2011-10-24
ok thanks ... let me try .. nw i have to find a hdd to backup files :/

do you know how this happened ? how to prevent this ?

---

### Post by cooldoctormohitm on 2011-10-24
sir,...
           Mine ubuntu11.04 partition was missing after installing  windows xp,but as i restored ubuntu11.04 using live usb now, I am unable  to boot into my xp partition, even though i can see windows as well as  ubuntu in boot list...and i m able to login into ubuntu, but as i try to  login into xp part..i got such a error message-

error:no such device: 266041B560418DOD
error:device format: "dev sd,msdos 1" invalid: must be (f/h/dN,with 0<=N<12:cool:
erorr:no such disk.


i want to login into xp as well as ubuntu..pls help regaring this..
additional info about my system ia attached: thank you

---

### Post by Mark Phelps on 2011-10-24
cooldoctormohitm: Yours is a very different problem.  Please do not hijack this thread as that will only make problem solving very difficult.  Please start your own thread.

---

### Post by ashintomson on 2011-10-29
windows is booting but its not loading fully cursor came but nothing else came full blackscreen and cursor thats all ... what 2 do now ??

---

### Post by ashintomson on 2011-10-29
whn i run tht ubuntu command in terminal i think tht dint work 
this was the result 

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot stat `aufs'.
ubuntu@ubuntu:~$ 

(ubuntu was booted with usb)

---

### Post by oldfred on 2011-10-29
You cannot run sudo update-grub from liveCD/USB unless you chroot into your system. If your windows is working then you can reinstall grub2's boot loader to the MBR. Did you run chkdsk on the Windows partition from a Windows repairCD or f8 on windows boot?

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda8 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda8 if not correct:
sudo fdisk -l
#confirm that linux is sda8
sudo mount /dev/sda8 /mnt
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

