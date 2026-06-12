---
title: "error: hd0 out of disk"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by pjgarde on 2012-02-03
Hi people!

I'm form Argentina and I'd like to fix a problem with my PC:

I bought a hard drive 3 weeks ago (Western Digital, 500 GB, SATA2).
First I installed Windows 7, then Ubuntu 11.10 and finally with a Grub Manager I put Windows 7 as default operating system.

Some days later when I was booting I noticed that Ubuntu was the default operating system. (I don't know how because this computer nobody except me uses it).

2 weeks later, I was using Windows 7 and I don't know why but the system was asking me to restart the computer. I do it. And when I was booting (before Grub Menu should appears). It appears this message:

[B]error: hd0 out of disk
grub rescue>[/B]

After that, I booted with a Live CD, I've downloaded a Boot Repair, but nothing has change.

If anybody could help me I'll be thanks to him/her :D

PD: Please, excuse my naughty English.

---

### Post by pjgarde on 2012-02-03
Maybe this can help... (I'm a noob on this :( )

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeed9eed9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   614405924   307202931    7  HPFS/NTFS/exFAT
/dev/sda2       614405986   819202544   102398279+   f  W95 Ext'd (LBA)
/dev/sda3       819204096   916858879    48827392   83  Linux
/dev/sda4       916858880   976771071    29956096   82  Linux swap / Solaris
/dev/sda5       614405988   819202544   102398278+   7  HPFS/NTFS/exFAT

---

### Post by Rubi1200 on 2012-02-03
Hi and welcome to the forums :-)

Please post the results of the boot info script so we can see what is going on.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by pjgarde on 2012-02-03
Here it is :D

---

### Post by Rubi1200 on 2012-02-03
For those concerned:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

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

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   614,405,924   614,405,862   7 NTFS / exFAT / HPFS
/dev/sda2         614,405,986   819,202,544   204,796,559   f W95 Extended (LBA)
/dev/sda5         614,405,988   819,202,544   204,796,557   7 NTFS / exFAT / HPFS
/dev/sda3         819,204,096   916,858,879    97,654,784  83 Linux
/dev/sda4         916,858,880   976,771,071    59,912,192  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F038C59938C55F6A                       ntfs       
/dev/sda3        9abca613-adc9-4488-af20-7293e8e1935b   ext4       
/dev/sda4        853be095-66c9-4e2d-8c55-38aef37b50b4   swap       
/dev/sda5        AA40D2F140D2C36D                       ntfs       DATOS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt/boot-sav/sda1       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /mnt/boot-sav/sda3       ext4       (rw)
/dev/sda5        /mnt/boot-sav/sda5       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=Windows /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 9abca613-adc9-4488-af20-7293e8e1935b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 9abca613-adc9-4488-af20-7293e8e1935b
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9abca613-adc9-4488-af20-7293e8e1935b
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=9abca613-adc9-4488-af20-7293e8e1935b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9abca613-adc9-4488-af20-7293e8e1935b
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=9abca613-adc9-4488-af20-7293e8e1935b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9abca613-adc9-4488-af20-7293e8e1935b
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=9abca613-adc9-4488-af20-7293e8e1935b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9abca613-adc9-4488-af20-7293e8e1935b
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=9abca613-adc9-4488-af20-7293e8e1935b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9abca613-adc9-4488-af20-7293e8e1935b
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=9abca613-adc9-4488-af20-7293e8e1935b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9abca613-adc9-4488-af20-7293e8e1935b
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=9abca613-adc9-4488-af20-7293e8e1935b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9abca613-adc9-4488-af20-7293e8e1935b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 9abca613-adc9-4488-af20-7293e8e1935b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=9abca613-adc9-4488-af20-7293e8e1935b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=853be095-66c9-4e2d-8c55-38aef37b50b4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 394.763805389 = 423.874408448  boot/grub/core.img                             1
 398.763511658 = 428.169060352  boot/grub/grub.cfg                             1
 392.038085938 = 420.947689472  boot/initrd.img-3.0.0-12-generic               1
 393.133144379 = 422.123499520  boot/initrd.img-3.0.0-14-generic               3
 393.442211151 = 422.455357440  boot/initrd.img-3.0.0-15-generic               2
 398.759418488 = 428.164665344  boot/vmlinuz-3.0.0-12-generic                  1
 391.873458862 = 420.770922496  boot/vmlinuz-3.0.0-14-generic                  2
 393.697681427 = 422.729666560  boot/vmlinuz-3.0.0-15-generic                  1
 393.697681427 = 422.729666560  vmlinuz                                        1
 391.873458862 = 420.770922496  vmlinuz.old                                    2

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by oldfred on 2012-02-03
I do not see anything wrong with boot script. You do have XP & Vista/7 boot files in your Windows partition. Grub.cfg does not show the boot stanza for Windows.

Boot-Repair normally reinstalls grub2's boot loader and gets your working again. But you can manually reinstall grub2's boot loader.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda3 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda3 if not correct:
sudo fdisk -l
#confirm that linux is sda3
sudo mount /dev/sda3 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by pjgarde on 2012-02-04
I was surfing the Internet and I found a solution:

When I turn on the PC and error message is on screen:

[B]error: hd0 out of disk
grub rescue>

[/B]I've to write this:

[B]grub rescue> set prefix=(hd0,msdos3)/boot/grub
[/B] [B]grub rescue> insmod normal
[/B][B]grub rescue> normal

[/B]And after that, Normal GRUB Menu appears.

But the problem is that I have to write this lines every time I turn on the computer.

How can I definitelly solve this problem?

Thanks for the help given!

---

### Post by dino99 on 2012-02-04
so when you are under ubuntu:

sudo apt-get install synaptic
sudo synaptic
         - search for "grub-pc" and purge then reinstall it on /dev/sda
sudo update-grub

---

### Post by pjgarde on 2012-02-04
> **dino99 said:**
> so when you are under ubuntu:

sudo apt-get install synaptic
sudo synaptic
         - search for "grub-pc" and purge then reinstall it on /dev/sda
sudo update-grub


I did it, and after that the computear appears to be perfect (I was using Ubuntu) but when I restart to load Windows this message appears:

[B]A disk read error ocurred
Press Ctrl+Alt+Del to restart[/B]

Then appears Grub Rescue again!!

And despite I did this:

[B]grub rescue> set prefix=(hd0,msdos3)/boot/grub
[/B] [B]grub rescue> insmod normal
[/B][B]grub rescue> normal

[/B]The computer didn't boot Ubuntu or Windows 

Now when I turn on the PC, GRUB Rescue appears and if I tried to boot Ubuntu this message appears:

[B]error: couldn't read file
error: you need to load the kernel first
press any key to continue[/B]

This is terrible :(

What happen?
What I have to do?

---

### Post by oldfred on 2012-02-04
Try reinstalling grub again.

Are you running any Windows software with DRM that uses flexnet or other DRM software that may write into the area after the MBR where grub also writes. That sometimes has caused a conflict.

---

### Post by pjgarde on 2012-02-04
I've booted from Live CD.
Reinstall GRUB 2, and when I turn on the PC normal GRUB Menu appears.

I can start Ubuntu but apparently if I tried to boot Windows 7 the next time** hd0 error message** will be on screnn.

Does Windows 7 write on MBR?

What I have to do to solve this?

---

### Post by oldfred on 2012-02-04
Is this a Dell or HP. Are you running any DRM software in Windows? Or some agressive anti-virus software in Windows. The flexnet issue has mostly been fixed by a work around in grub.

Writes to MBR area-----------------------------------
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)
In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

### Post by pjgarde on 2012-02-05
I don't have any  Windows 7 DataSafe, HP ProtectTools or Dell Recovery.

How can I know who is writing on my MBR?

---

### Post by oldfred on 2012-02-05
What proprietary software have you installed, like 
Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others 
 see google search on others with same issue: flexnet site:ubuntuforums.org
Sector 32 is already in use by FlexNet


I do not know EasyBCD, but some that use Windows 7 and have issues report it works. I think you have to install grub2's boot loader to the Linix partitions and EasyBCD chain loads to it. Grub2 in a partition is less reliable and you need to be prepared to reinstall it to the PBR on any updates to grub2. Other updates should not make any difference.
[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

