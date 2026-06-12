---
title: "Windows 7 + Ubuntu 10.10 windows 7 installed first"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by 7thDrea on 2010-12-15
Windows 7 was pre installed on my PC.
I installed Ubuntu 10.10 along side with Windows 7 using live CD.
After installation i am allowed to enter only to Ubuntu.
No bootmenu (grub) on startup - can't choose OS.

```
$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x995efd8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18215   146310279    7  HPFS/NTFS
/dev/sda2           18216       30402    97886209    5  Extended
/dev/sda5           18216       29901    93860864   83  Linux
/dev/sda6           29901       30402     4024320   82  Linux swap / Solaris
```

Tried  
```

$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
done
```

I could mount Windows, but the folder is empty however in properties 48.7 GB Used 90.8 GB free.

Booted Knoppix from USB stick and it can see content of Windows folder.

Need help, what should i do?

---

### Post by garvinrick4 on 2010-12-15
Go to this link and download bootscript to DESKTOP and then open a terminal and
copy and paste code will put a file on desktop that says RESULTS. Copy and paste
that in this thread and if you would highlight whole thing and hit the # sign in upper
right of message box and will put in nice box to read in. 

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by 7thDrea on 2010-12-15
**garvinrick4**, thanks for quick response

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
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

/dev/sda1    *          2,048   292,622,605   292,620,558   7 HPFS/NTFS
/dev/sda2         292,624,382   488,396,799   195,772,418   5 Extended
/dev/sda5         292,624,384   480,346,111   187,721,728  83 Linux
/dev/sda6         480,348,160   488,396,799     8,048,640  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2064 MB, 2064646144 bytes
255 heads, 63 sectors/track, 251 cylinders, total 4032512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     4,032,314     4,032,252   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        428ECD3D8ECD2A6D                       ntfs       Windows                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6559770a-454e-4cc2-96e6-910745ec9c6f   ext4                                     
/dev/sda6        c483ee88-1848-48a0-a50d-6a83fe2b3917   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        471B-222B                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 6559770a-454e-4cc2-96e6-910745ec9c6f
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 6559770a-454e-4cc2-96e6-910745ec9c6f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=11
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6559770a-454e-4cc2-96e6-910745ec9c6f
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=6559770a-454e-4cc2-96e6-910745ec9c6f ro  quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6559770a-454e-4cc2-96e6-910745ec9c6f
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=6559770a-454e-4cc2-96e6-910745ec9c6f ro single  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6559770a-454e-4cc2-96e6-910745ec9c6f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 6559770a-454e-4cc2-96e6-910745ec9c6f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
menuentry "Windows 7" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 400aa41b7790b28a
    chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.

# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6559770a-454e-4cc2-96e6-910745ec9c6f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c483ee88-1848-48a0-a50d-6a83fe2b3917 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 220.8GB: boot/grub/core.img
 152.5GB: boot/grub/grub.cfg
 152.1GB: boot/grub/stage2
 177.3GB: boot/initrd.img-2.6.35-23-generic-pae
 177.3GB: boot/vmlinuz-2.6.35-23-generic-pae
 177.3GB: initrd.img
 177.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  08 b5 19 9f 00 00 00 00  00 00 00 00 02 00 00 00  |................|
00000010  01 00 00 00 00 00 00 00  3f 00 00 00 00 00 00 00  |........?.......|
00000020  3c 00 0a c0 00 00 00 00  f4 01 00 00 04 00 00 00  |<...............|
00000030  d3 16 22 56 03 00 00 00  36 da 17 f3 01 6c 92 41  |.."V....6....l.A|
00000040  a5 27 76 a8 14 b0 52 15  17 00 00 00 00 00 00 00  |.'v...R.........|
00000050  08 b5 19 9f 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000060  40 00 0a c0 00 00 00 00  f4 01 00 00 04 00 00 00  |@...............|
00000070  e9 16 22 56 03 00 00 00  8e 0d 5e 29 ec 51 b8 43  |.."V......^).Q.C|
00000080  9c c6 9f 79 33 1d 27 d6  17 00 00 00 00 00 00 00  |...y3.'.........|
00000090  08 b5 19 9f 00 00 00 00  00 00 00 00 a8 13 00 00  |................|
000000a0  44 00 0a c0 01 00 00 00  f4 01 00 00 04 00 00 00  |D...............|
000000b0  02 17 22 56 03 00 00 00  fb 6f f7 8b 3c d0 60 4f  |.."V.....o..<.`O|
000000c0  89 85 9c a7 34 cc f6 ce  17 00 00 00 00 00 00 00  |....4...........|
000000d0  08 b5 19 9f 00 00 00 00  c8 b7 aa 87 00 00 00 00  |................|
000000e0  23 00 00 00 00 00 00 00  34 00 0a c0 02 00 00 00  |#.......4.......|
000000f0  f4 01 00 00 04 00 00 00  6e 17 22 56 03 00 00 00  |........n."V....|
00000100  fb 6f f7 8b 3c d0 60 4f  89 85 9c a7 34 cc f6 ce  |.o..<.`O....4...|
00000110  17 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  4c 00 0a c0 00 00 00 00  f4 01 00 00 04 00 00 00  |L...............|
00000130  9b 17 22 56 03 00 00 00  95 5e b1 c7 81 af ec 4f  |.."V.....^.....O|
00000140  b7 a1 0b 71 dc 61 03 91  17 00 00 00 00 00 00 00  |...q.a..........|
00000150  08 b5 19 9f 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  50 c3 00 00 00 00 00 00  03 00 00 00 00 00 00 00  |P...............|
00000170  54 00 0a c0 01 00 00 00  f4 01 00 00 04 00 00 00  |T...............|
00000180  a9 17 22 56 03 00 00 00  2b dd 46 47 d7 20 3f 49  |.."V....+.FG. ?I|
00000190  bc 1b 24 03 97 c8 5b 25  17 00 00 00 00 00 00 00  |..$...[%........|
000001a0  08 b5 19 9f 00 00 00 00  00 00 00 00 3d 26 00 00  |............=&..|
000001b0  00 00 00 00 a8 13 00 00  c8 b7 aa 87 00 00 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 68 30 0b 00 fe  |...........h0...|
000001d0  ff ff 05 fe ff ff 02 68  30 0b 00 d8 7a 00 00 00  |.......h0...z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

ls: reading directory sda1/: Invalid or incomplete multibyte or wide character
```

---

### Post by garvinrick4 on 2010-12-15
Here is a link to purge then reinstall grub.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by sikander3786 on 2010-12-15
I don't think there is a need to purge and re-install Grub as Grub is able to boot Ubuntu successfully.

The problem seems to lie with Windows partition. This error,

> ls: reading directory sda1/: Invalid or incomplete multibyte or wide character

It suggests that there is some problem with character encoding on sda1.

---

### Post by 7thDrea on 2010-12-15
done what is said in chapter "Purge & Reinstall without Chroot"
Same errors occur at the and of 
```
sudo apt-get purge grub grub-pc grub-common
```and 
```
sudo update-grub 
``````

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
ls: reading directory /var/lib/os-prober/mount: Invalid or incomplete multibyte or wide character
done

```
Rebooted and nothing is changed[B]

sikander3786[/B], any ideas how to resolve these problem?

---

### Post by sikander3786 on 2010-12-15
First reboot and make sure you are able to boot Ubuntu successfully.

I have not much ideas for solving that encoding problem. The only thing I can suggest is to repair Windows startup from a Windows installation/repair disc. Once you are able to boot Windows successfully, independent of Grub, re-install Grub. Post back if you need help on that.

---

### Post by 7thDrea on 2010-12-15
**sikander3786**, Ubuntu boots same - no grub(boot menu).

I don't have Windows Installation disk. Is there is any althernative to Windows Installation disk ?

---

### Post by sikander3786 on 2010-12-15
Ubuntu is able to boot successfully, that is enough for the moment.

You can Google and download a Windows 7 repair disc easily. Here's one of those links.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by garvinrick4 on 2010-12-15
sikander3786 you think anything to do with custom menu entry for Windows 7?
And the boot/grub/stage2 entry?

 220.8GB: boot/grub/core.img
 152.5GB: boot/grub/grub.cfg
 [COLOR=Red]152.1GB: boot/grub/stage2[/COLOR]
 177.3GB: boot/initrd.img-2.6.35-23-generic-pae
 177.3GB: boot/vmlinuz-2.6.35-23-generic-pae
 177.3GB: initrd.img
 177.3GB: vmlinuz

---

### Post by sikander3786 on 2010-12-15
> **garvinrick4 said:**
> sikander3786 you think anything to do with custom menu entry for Windows 7?
Good Point :-)

The OP can try removing that custom entry and try update-grub again. I don't know why that was added as custom entry? UUIDs don't match.

I am sure you can guide the OP there. I have to leave but I'll be back soon.

Carry on :-)

---

### Post by wilee-nilee on 2010-12-15
Was W7 re-sized by the installer, if so it might just need a chkdsk /f/r

---

### Post by sikander3786 on 2010-12-15
> **wilee-nilee said:**
> Was W7 re-sized by the installer, if so it might just need a chkdsk /f/r
Glad to see the most experience member on Windows boot issues here :-)

I was just going to PM you.

Good Luck!

---

### Post by 7thDrea on 2010-12-15
**sikander3786**, is windows 7 repair disk from neosmart is legal?
**wilee-nilee**, yes it was through Live CD

---

### Post by theasprint on 2010-12-15
Is there like any screen lag before it goes to load Ubuntu?

I may suspect that your MBR for Windows 7 is spoilt. In this case, go and get a repair disc to fix your MBR.

---

### Post by wilee-nilee on 2010-12-15
> **7thDrea said:**
> **sikander3786**, is windows 7 repair disk from neosmart is legal?
**wilee-nilee**, yes it was through Live CD

The recovery disc is legal and here is a per oldfred the real windows expert,;) the instructions and a W7 forum link to get you to the command line to run the chkdsk /f/r. It will ask you if you want to run it at startup say yes and reboot to W7 and see if it runs.

1) Boot with your Vista/Windows 7 installation/recovery disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:

```
chkdsk /f/r
```

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by sikander3786 on 2010-12-15
> is windows 7 repair disk from neosmart is legal?

We don't talk about piracy on the forums. It is prohibited here ;-)

I hope chkdsk /f/r will fix your issue. Lets see.

---

### Post by 7thDrea on 2010-12-15
**theasprint**,I think there is..
**wilee-nilee, ****sikander3786,  **thanks for all. trying to download Repair disk and then use[B] chkdsk
[/B]

---

### Post by garvinrick4 on 2010-12-15
It seems to be rather obvious from bootscript that more than 
just trying to install Ubuntu side by side with Windows 7 has happened. 
If OP would state exactly the things that were tried to install or 
fixes tried using would make this thread a lot easier to handle.

---

### Post by wilee-nilee on 2010-12-15
> **garvinrick4 said:**
> It seems to be rather obvious from bootscript that more than 
just trying to install Ubuntu side by side with Windows 7 has happened. 
If OP would state exactly the things that were tried to install or 
fixes tried using would make this thread a lot easier to handle.

Your are correct I had missed the boot order good eye.;) we had posted within minutes of each other.

---

### Post by 7thDrea on 2010-12-17
Sorry for late reporting

Using StartUp-Manager changed default booting OS to Windows
reboot 
Windows offered me to repair windows again reboot and i am able to login to Windows.
I don't have administrator privileges so i can't use chkdsk /f/r
Using Knoppix USB stick copied from my co-worker grub.cfg and replaced it with /boot/grub/grub.cfg
and now i have on startup grub - can choose which OS to boot

However, in Ubuntu still Windows folder(where Windows is installed) is empy - can't see files.

---

