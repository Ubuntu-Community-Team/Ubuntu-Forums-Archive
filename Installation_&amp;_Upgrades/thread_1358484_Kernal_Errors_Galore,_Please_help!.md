---
title: "Kernal Errors Galore, Please help!"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by jremlap on 2009-12-18
I have a system running windows 7 RC, trying to get Ubuntu (9.01) to install. I have 3 SATA drives, I am not using RAID striping. I am fairly tech savvy, but I cannot figure out what is wrong with this installation. First, I have tried every different way of installing (I.E. Via windows installer, Via disk, etc.) and nothing has fixed this problem. I am trying to leave win 7 in tact until I confirm that I definitely want to convert to Ubuntu. I am brand new to the linux environment so bare with me if I am kinda dumb to some of this. 

First, I am getting this error after installing ubuntu and attempting to load it up for the first time:

[IMG]http://img.photobucket.com/albums/v616/Stryker_8/Error.jpg[/IMG]

I am running on a custom built PC here's the specs:

AMD Athlon 64 X2 Dual Core 3800+ 2.00GHz
4 GB RAM
Nvidia Nforce4 based A8N-SLI mobo
Dual Nvidia GeForce 9600GT's (one is 512, one is 1 GB SLI Fully functional in windows)
3 SATA HD's - 1x1TB, 2x200GB
1xDVDRW
1xCDRW

EDIT: I should mention Windows 7 is installed on one of the 200GB drives and I am attempting to install Ubuntu on the 1TB Drive

There is one thing I should mention. I am aware that with the SATA infrastructure of this motherboard, I cannot use the SATA1 connector to connect a boot drive (per manufacturers doc's) and so to be on the safe side, I swapped the 3rd and 1st plugs after another failed install. This would be of no help but a curious thing happened after this was done:

Instead of only seeing a boot menu that showed win 7 and Ubuntu options, I now see the GRUB menu. I had previously never seen this. I am trying to get this resolved as quickly as possible, please if you can be of any assistance, it would be GREATLY appreciated!

-JoE

---

### Post by darkod on 2009-12-18
Because I couldn't understand from the post can you specify what you have on your 3 hdds and what is their boot order in BIOS?

---

### Post by jremlap on 2009-12-18
Thank you for your quick response:

in BIOS The 1TB drive is the primary master, and the primary boot drive. The secondary boot drive is the 200GB that currently contains windows 7. The 1TB is where ubuntu is installed.

Thanks again!

---

### Post by darkod on 2009-12-18
Boot with the ubuntu cd, Try Ubuntu option. Download the script from my signature, move it on desktop for example, and execute it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with lots of info about your boot process. Copy the content here and please wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above).

---

### Post by jremlap on 2009-12-18
[CODE]============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM /wubildr.mbr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb6a2b6a2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   390,700,799   390,700,737   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x29932992

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,938,402,899 1,938,402,837  83 Linux
/dev/sdb2       1,938,402,900 1,953,520,064    15,117,165   5 Extended
/dev/sdb5       1,938,402,963 1,953,520,064    15,117,102  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12960804

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   390,700,799   390,700,737   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="DEC47393C4736CA1" TYPE="ntfs" 
/dev/sdb1: UUID="e82d04ae-eccd-423e-9ed8-b3a1eafb7f07" TYPE="ext4" 
/dev/sdb5: UUID="81a4cbaf-6288-4df0-b24c-e2f3555bade9" TYPE="swap" 
/dev/sdc1: UUID="EAF06231F06203E3" LABEL="200GB Storage" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)[CODE]

---

### Post by darkod on 2009-12-18
wubildr.mbr means that you either had or you still have wubi installed. And you also have full ubuntu installation on /dev/sdb1. Do you still use wubi? Because it doesn't seem completely removed.
There was more info in the results.txt file. It continues with the content of grub.cfg which helps to see if the grub2 configuration is correct.

---

### Post by jremlap on 2009-12-18
Sorry I missed that. Here is the rest of the file below. I think you are correct there, I see the Wubi and an uninstall option on my backup 200GB drive. Should I just merely run the uninstall and try and startup ubuntu? I appologise, I thought that I had removed that installation attempt before running the CD.

Remaining File:

```
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/e82d04ae-eccd-423e-9ed8-b3a1eafb7f07 type ext4 (rw,nosuid,nodev,uhelper=devkit)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set e82d04ae-eccd-423e-9ed8-b3a1eafb7f07
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
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e82d04ae-eccd-423e-9ed8-b3a1eafb7f07
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=e82d04ae-eccd-423e-9ed8-b3a1eafb7f07 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e82d04ae-eccd-423e-9ed8-b3a1eafb7f07
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=e82d04ae-eccd-423e-9ed8-b3a1eafb7f07 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
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
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set dec47393c4736ca1
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
```

---

### Post by darkod on 2009-12-18
If you installed wubi inside win7, the uninstall could work. You can also just go in add/remove programs in win7 and remove it like any windows app. There will be ubuntu entry in the programs list.
But I'm not sure it;s related with this problem. Anyway, it's better to remove wubi first, not to complicate with remains in the system.
Also you could try to check the filesystem of ubuntu. Just boot with the cd, Try Ubuntu option, and in terminal execute:
sudo fsck /dev/sdb1

That will check the ubuntu partition for any errors.

---

### Post by jremlap on 2009-12-18
I got back into windows, attempted to uninstall (both through the windows program remover and directly to the uninstall file) and I am getting the following error:

[IMG]http://img.photobucket.com/albums/v616/Stryker_8/12-18-20097-00-14PM.png[/IMG]

Then when I open the named .Log file, this is the contents:

```
11-30 18:23 INFO   root: === wubi 9.10ubuntu1 rev160 ===
11-30 18:23 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
11-30 18:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
11-30 18:23 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\data
11-30 18:23 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\bin\7z.exe
11-30 18:23 DEBUG  CommonBackend: Fetching basic info...
11-30 18:23 DEBUG  CommonBackend: original_exe=F:\wubi.exe
11-30 18:23 DEBUG  CommonBackend: platform=win32
11-30 18:23 DEBUG  CommonBackend: osname=nt
11-30 18:23 DEBUG  CommonBackend: language=en_US
11-30 18:23 DEBUG  CommonBackend: encoding=cp1252
11-30 18:23 DEBUG  WindowsBackend: arch=amd64
11-30 18:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\data\isolist.ini
11-30 18:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-30 18:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-30 18:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-30 18:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-30 18:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-30 18:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-30 18:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-30 18:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-30 18:23 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-30 18:23 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
11-30 18:23 DEBUG  WindowsBackend: Fetching host info...
11-30 18:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-30 18:23 DEBUG  WindowsBackend: windows version=vista
11-30 18:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-30 18:23 DEBUG  WindowsBackend: windows_sp=None
11-30 18:23 DEBUG  WindowsBackend: windows_build=7100
11-30 18:23 DEBUG  WindowsBackend: gmt=-5
11-30 18:23 DEBUG  WindowsBackend: country=US
11-30 18:23 DEBUG  WindowsBackend: timezone=America/New_York
11-30 18:23 DEBUG  WindowsBackend: windows_username=JOE
11-30 18:23 DEBUG  WindowsBackend: user_full_name=JOE
11-30 18:23 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
11-30 18:23 DEBUG  WindowsBackend: windows_language_code=1033
11-30 18:23 DEBUG  WindowsBackend: windows_language=English
11-30 18:23 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
11-30 18:23 DEBUG  WindowsBackend: bootloader=vista
11-30 18:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2985.1796875 mb free ntfs)
11-30 18:23 DEBUG  WindowsBackend: drive=Drive(C: hd 2985.1796875 mb free ntfs)
11-30 18:23 DEBUG  WindowsBackend: drive=Drive(D: hd 667440.484375 mb free ntfs)
11-30 18:23 DEBUG  WindowsBackend: drive=Drive(E: hd 28831.1679688 mb free ntfs)
11-30 18:23 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
11-30 18:23 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
11-30 18:23 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
11-30 18:23 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
11-30 18:23 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
11-30 18:23 DEBUG  WindowsBackend: drive=Drive(L: removable 0.0 mb free )
11-30 18:23 DEBUG  WindowsBackend: uninstaller_path=None
11-30 18:23 DEBUG  WindowsBackend: previous_target_dir=None
11-30 18:23 DEBUG  WindowsBackend: previous_distro_name=None
11-30 18:23 DEBUG  WindowsBackend: keyboard_id=67699721
11-30 18:23 DEBUG  WindowsBackend: keyboard_layout=us
11-30 18:23 DEBUG  WindowsBackend: keyboard_variant=
11-30 18:23 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-30 18:23 DEBUG  CommonBackend: locale=en_US.UTF-8
11-30 18:23 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-30 18:23 DEBUG  CommonBackend: Searching ISOs on USB devices
11-30 18:23 DEBUG  CommonBackend: Searching for local CDs
11-30 18:23 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp is a valid Ubuntu Netbook Remix CD
11-30 18:23 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp is a valid Kubuntu Netbook CD
11-30 18:23 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
11-30 18:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-30 18:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
11-30 18:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-30 18:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-30 18:23 ERROR  Distro: [Errno 13] Permission denied
11-30 18:23 DEBUG  Distro: could not get info None
11-30 18:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro: could not get info None
11-30 18:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
11-30 18:23 DEBUG  Distro: could not get info None
11-30 18:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro: could not get info None
11-30 18:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro: could not get info None
11-30 18:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
11-30 18:23 DEBUG  Distro: could not get info None
11-30 18:23 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro: could not get info None
11-30 18:23 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro: could not get info None
11-30 18:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro: could not get info None
11-30 18:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro: could not get info None
11-30 18:23 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
11-30 18:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-30 18:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook Remix CD
11-30 18:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
11-30 18:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook Remix CD
11-30 18:23 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
11-30 18:23 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook Remix CD
11-30 18:23 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu Netbook CD
11-30 18:23 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Netbook Remix CD
11-30 18:23 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu Netbook CD
11-30 18:23 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-30 18:23 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-30 18:23 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-30 18:23 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-30 18:23 INFO   root: Running the installer...
11-30 18:23 DEBUG  WindowsFrontend: __init__...
11-30 18:23 DEBUG  WindowsFrontend: on_init...
11-30 18:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\translations, languages=['en_US', 'en']
11-30 18:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl2CB0.tmp\translations, languages=['en_US', 'en']
11-30 18:24 INFO   WindowsFrontend: Operation cancelled
11-30 18:24 DEBUG  WindowsFrontend: frontend.quit
11-30 18:24 DEBUG  WindowsFrontend: frontend.on_quit
11-30 18:24 DEBUG  root: application.on_quit
11-30 18:24 INFO   root: sys.exit
12-17 13:19 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-17 13:19 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-17 13:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\JOE\\Documents\\Downloads\\wubi.exe"']
12-17 13:19 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\data
12-17 13:19 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\bin\7z.exe
12-17 13:19 DEBUG  CommonBackend: Fetching basic info...
12-17 13:19 DEBUG  CommonBackend: original_exe=C:\Users\JOE\Documents\Downloads\wubi.exe
12-17 13:19 DEBUG  CommonBackend: platform=win32
12-17 13:19 DEBUG  CommonBackend: osname=nt
12-17 13:19 DEBUG  CommonBackend: language=en_US
12-17 13:19 DEBUG  CommonBackend: encoding=cp1252
12-17 13:19 DEBUG  WindowsBackend: arch=amd64
12-17 13:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\data\isolist.ini
12-17 13:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 13:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 13:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 13:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 13:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 13:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 13:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 13:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 13:19 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-17 13:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-17 13:19 DEBUG  WindowsBackend: Fetching host info...
12-17 13:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 13:19 DEBUG  WindowsBackend: windows version=vista
12-17 13:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-17 13:19 DEBUG  WindowsBackend: windows_sp=None
12-17 13:19 DEBUG  WindowsBackend: windows_build=7100
12-17 13:19 DEBUG  WindowsBackend: gmt=-5
12-17 13:19 DEBUG  WindowsBackend: country=US
12-17 13:19 DEBUG  WindowsBackend: timezone=America/New_York
12-17 13:19 DEBUG  WindowsBackend: windows_username=JOE
12-17 13:19 DEBUG  WindowsBackend: user_full_name=JOE
12-17 13:19 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-17 13:19 DEBUG  WindowsBackend: windows_language_code=1033
12-17 13:19 DEBUG  WindowsBackend: windows_language=English
12-17 13:19 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-17 13:19 DEBUG  WindowsBackend: bootloader=vista
12-17 13:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2507.12109375 mb free ntfs)
12-17 13:19 DEBUG  WindowsBackend: drive=Drive(C: hd 2507.12109375 mb free ntfs)
12-17 13:19 DEBUG  WindowsBackend: drive=Drive(D: hd 650262.421875 mb free ntfs)
12-17 13:19 DEBUG  WindowsBackend: drive=Drive(E: hd 30519.578125 mb free ntfs)
12-17 13:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-17 13:19 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 13:19 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-17 13:19 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
12-17 13:19 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
12-17 13:19 DEBUG  WindowsBackend: drive=Drive(L: removable 0.0 mb free )
12-17 13:19 DEBUG  WindowsBackend: uninstaller_path=None
12-17 13:19 DEBUG  WindowsBackend: previous_target_dir=None
12-17 13:19 DEBUG  WindowsBackend: previous_distro_name=None
12-17 13:19 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 13:19 DEBUG  WindowsBackend: keyboard_layout=us
12-17 13:19 DEBUG  WindowsBackend: keyboard_variant=
12-17 13:19 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 13:19 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 13:19 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-17 13:19 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 13:19 DEBUG  CommonBackend: Searching for local CDs
12-17 13:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp is a valid Ubuntu Netbook Remix CD
12-17 13:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp is a valid Kubuntu Netbook CD
12-17 13:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylEF7E.tmp\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-17 13:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-17 13:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-17 13:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-17 13:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-17 13:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-17 13:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-17 13:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-17 13:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook Remix CD
12-17 13:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
12-17 13:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-17 13:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook Remix CD
12-17 13:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-17 13:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:19 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-17 13:20 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-17 13:20 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-17 13:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Downloads\\wubi.exe"']
12-17 13:20 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\data
12-17 13:20 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\bin\7z.exe
12-17 13:20 DEBUG  CommonBackend: Fetching basic info...
12-17 13:20 DEBUG  CommonBackend: original_exe=D:\Downloads\wubi.exe
12-17 13:20 DEBUG  CommonBackend: platform=win32
12-17 13:20 DEBUG  CommonBackend: osname=nt
12-17 13:20 DEBUG  CommonBackend: language=en_US
12-17 13:20 DEBUG  CommonBackend: encoding=cp1252
12-17 13:20 DEBUG  WindowsBackend: arch=amd64
12-17 13:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\data\isolist.ini
12-17 13:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 13:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 13:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 13:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 13:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 13:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 13:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 13:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 13:20 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-17 13:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-17 13:20 DEBUG  WindowsBackend: Fetching host info...
12-17 13:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 13:20 DEBUG  WindowsBackend: windows version=vista
12-17 13:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-17 13:20 DEBUG  WindowsBackend: windows_sp=None
12-17 13:20 DEBUG  WindowsBackend: windows_build=7100
12-17 13:20 DEBUG  WindowsBackend: gmt=-5
12-17 13:20 DEBUG  WindowsBackend: country=US
12-17 13:20 DEBUG  WindowsBackend: timezone=America/New_York
12-17 13:20 DEBUG  WindowsBackend: windows_username=JOE
12-17 13:20 DEBUG  WindowsBackend: user_full_name=JOE
12-17 13:20 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-17 13:20 DEBUG  WindowsBackend: windows_language_code=1033
12-17 13:20 DEBUG  WindowsBackend: windows_language=English
12-17 13:20 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-17 13:20 DEBUG  WindowsBackend: bootloader=vista
12-17 13:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2500.77734375 mb free ntfs)
12-17 13:20 DEBUG  WindowsBackend: drive=Drive(C: hd 2500.77734375 mb free ntfs)
12-17 13:20 DEBUG  WindowsBackend: drive=Drive(D: hd 650261.019531 mb free ntfs)
12-17 13:20 DEBUG  WindowsBackend: drive=Drive(E: hd 30519.578125 mb free ntfs)
12-17 13:20 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-17 13:20 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 13:21 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-17 13:21 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
12-17 13:21 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
12-17 13:21 DEBUG  WindowsBackend: drive=Drive(L: removable 0.0 mb free )
12-17 13:21 DEBUG  WindowsBackend: uninstaller_path=None
12-17 13:21 DEBUG  WindowsBackend: previous_target_dir=None
12-17 13:21 DEBUG  WindowsBackend: previous_distro_name=None
12-17 13:21 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 13:21 DEBUG  WindowsBackend: keyboard_layout=us
12-17 13:21 DEBUG  WindowsBackend: keyboard_variant=
12-17 13:21 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 13:21 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 13:21 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-17 13:21 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 13:21 DEBUG  CommonBackend: Searching for local CDs
12-17 13:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp is a valid Ubuntu Netbook Remix CD
12-17 13:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp is a valid Kubuntu Netbook CD
12-17 13:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-17 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-17 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-17 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-17 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-17 13:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-17 13:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-17 13:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-17 13:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook Remix CD
12-17 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
12-17 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook Remix CD
12-17 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
12-17 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook Remix CD
12-17 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu Netbook CD
12-17 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Netbook Remix CD
12-17 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu Netbook CD
12-17 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
12-17 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:21 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
12-17 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:21 INFO   root: Running the installer...
12-17 13:21 DEBUG  WindowsFrontend: __init__...
12-17 13:21 DEBUG  WindowsFrontend: on_init...
12-17 13:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\translations, languages=['en_US', 'en']
12-17 13:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\translations, languages=['en_US', 'en']
12-17 13:22 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=joe
12-17 13:22 INFO   root: Received settings
12-17 13:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\translations, languages=['en_US', 'en']
12-17 13:22 DEBUG  TaskList: # Running tasklist...
12-17 13:22 DEBUG  TaskList: ## Running select_target_dir...
12-17 13:22 INFO   WindowsBackend: Installing into D:\ubuntu
12-17 13:22 DEBUG  TaskList: ## Finished select_target_dir
12-17 13:22 DEBUG  TaskList: ## Running create_dir_structure...
12-17 13:22 DEBUG  CommonBackend: Creating dir D:\ubuntu
12-17 13:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
12-17 13:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
12-17 13:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
12-17 13:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
12-17 13:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
12-17 13:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
12-17 13:22 DEBUG  TaskList: ## Finished create_dir_structure
12-17 13:22 DEBUG  TaskList: ## Running uncompress_target_dir...
12-17 13:22 DEBUG  TaskList: ## Finished uncompress_target_dir
12-17 13:22 DEBUG  TaskList: ## Running create_uninstaller...
12-17 13:22 DEBUG  WindowsBackend: Copying uninstaller D:\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
12-17 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
12-17 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
12-17 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-17 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
12-17 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
12-17 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-17 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
12-17 13:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-17 13:22 DEBUG  TaskList: ## Finished create_uninstaller
12-17 13:22 DEBUG  TaskList: ## Running copy_installation_files...
12-17 13:22 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
12-17 13:22 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\winboot -> D:\ubuntu\winboot
12-17 13:22 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
12-17 13:22 DEBUG  TaskList: ## Finished copy_installation_files
12-17 13:22 DEBUG  TaskList: ## Running get_iso...
12-17 13:22 DEBUG  CommonBackend: Searching for local CD
12-17 13:22 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp is a valid Ubuntu CD
12-17 13:22 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl3F5E.tmp\casper\filesystem.squashfs
12-17 13:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 13:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 13:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 13:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 13:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:22 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-17 13:22 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:22 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-17 13:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:22 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
12-17 13:22 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:22 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
12-17 13:22 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:22 DEBUG  CommonBackend: Searching for local ISO
12-17 13:22 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-17 13:22 DEBUG  TaskList: New task get_metalink
12-17 13:22 DEBUG  TaskList: ### Running get_metalink...
12-17 13:22 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink > D:\ubuntu\install
12-17 13:22 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
12-17 13:22 DEBUG  downloader: download finished (read 26651 bytes)
12-17 13:22 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink > D:\ubuntu\install
12-17 13:22 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
12-17 13:22 DEBUG  downloader: download finished (read 562 bytes)
12-17 13:22 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg > D:\ubuntu\install
12-17 13:22 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
12-17 13:22 DEBUG  downloader: download finished (read 189 bytes)
12-17 13:22 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
12-17 13:22 INFO   saplog: Checking block bindings..
12-17 13:22 INFO   saplog: Key verified successfully.
12-17 13:22 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

12-17 13:22 DEBUG  TaskList: ### Finished get_metalink
12-17 13:22 DEBUG  TaskList: New task download
12-17 13:22 DEBUG  TaskList: ### Running download...
12-17 13:22 DEBUG  btdownloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent > D:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 13:27 INFO   WindowsFrontend: Operation cancelled
12-17 13:27 DEBUG  WindowsFrontend: frontend.quit
12-17 13:27 DEBUG  WindowsFrontend: frontend.on_quit
12-17 13:27 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-17 13:27 DEBUG  TaskList: # Cancelling tasklist
12-17 13:27 DEBUG  TaskList: ### Finished download
12-17 13:27 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-17 13:27 DEBUG  root: application.on_quit
12-17 13:27 DEBUG  root: Forceful exit
12-17 13:27 INFO   root: sys.exit
12-17 13:29 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-17 13:29 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-17 13:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Downloads\\wubi.exe"']
12-17 13:29 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\data
12-17 13:29 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\bin\7z.exe
12-17 13:29 DEBUG  CommonBackend: Fetching basic info...
12-17 13:29 DEBUG  CommonBackend: original_exe=D:\Downloads\wubi.exe
12-17 13:29 DEBUG  CommonBackend: platform=win32
12-17 13:29 DEBUG  CommonBackend: osname=nt
12-17 13:29 DEBUG  CommonBackend: language=en_US
12-17 13:29 DEBUG  CommonBackend: encoding=cp1252
12-17 13:29 DEBUG  WindowsBackend: arch=amd64
12-17 13:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\data\isolist.ini
12-17 13:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 13:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 13:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 13:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 13:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 13:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 13:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 13:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 13:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-17 13:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-17 13:29 DEBUG  WindowsBackend: Fetching host info...
12-17 13:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 13:29 DEBUG  WindowsBackend: windows version=vista
12-17 13:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-17 13:29 DEBUG  WindowsBackend: windows_sp=None
12-17 13:29 DEBUG  WindowsBackend: windows_build=7100
12-17 13:29 DEBUG  WindowsBackend: gmt=-5
12-17 13:29 DEBUG  WindowsBackend: country=US
12-17 13:29 DEBUG  WindowsBackend: timezone=America/New_York
12-17 13:29 DEBUG  WindowsBackend: windows_username=JOE
12-17 13:29 DEBUG  WindowsBackend: user_full_name=JOE
12-17 13:29 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-17 13:29 DEBUG  WindowsBackend: windows_language_code=1033
12-17 13:29 DEBUG  WindowsBackend: windows_language=English
12-17 13:29 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-17 13:29 DEBUG  WindowsBackend: bootloader=vista
12-17 13:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2535.5625 mb free ntfs)
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(C: hd 2535.5625 mb free ntfs)
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(D: hd 649936.957031 mb free ntfs)
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(E: hd 30519.578125 mb free ntfs)
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(L: removable 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
12-17 13:29 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
12-17 13:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-17 13:29 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 13:29 DEBUG  WindowsBackend: keyboard_layout=us
12-17 13:29 DEBUG  WindowsBackend: keyboard_variant=
12-17 13:29 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 13:29 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 13:29 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-17 13:29 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 13:29 DEBUG  CommonBackend: Searching for local CDs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:29 INFO   root: Already installed, running the uninstaller...
12-17 13:29 INFO   root: Running the uninstaller...
12-17 13:29 INFO   CommonBackend: This is the uninstaller running
12-17 13:29 DEBUG  WindowsFrontend: __init__...
12-17 13:29 DEBUG  WindowsFrontend: on_init...
12-17 13:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\translations, languages=['en_US', 'en']
12-17 13:29 INFO   root: Received settings
12-17 13:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\translations, languages=['en_US', 'en']
12-17 13:29 DEBUG  TaskList: # Running tasklist...
12-17 13:29 DEBUG  TaskList: ## Running Backup ISO...
12-17 13:29 DEBUG  TaskList: ## Finished Backup ISO
12-17 13:29 DEBUG  TaskList: ## Running Remove bootloader entry...
12-17 13:29 DEBUG  WindowsBackend: Could not find bcd id
12-17 13:29 DEBUG  WindowsBackend: undo_bootini C:
12-17 13:29 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 2535.5625 mb free ntfs)
12-17 13:29 DEBUG  WindowsBackend: undo_bootini D:
12-17 13:29 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 649936.957031 mb free ntfs)
12-17 13:29 DEBUG  WindowsBackend: undo_bootini E:
12-17 13:29 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 30519.578125 mb free ntfs)
12-17 13:29 DEBUG  WindowsBackend: undo_bootini I:
12-17 13:29 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: undo_bootini J:
12-17 13:29 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: undo_bootini K:
12-17 13:29 DEBUG  WindowsBackend: undo_configsys Drive(K: removable 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: undo_bootini L:
12-17 13:29 DEBUG  WindowsBackend: undo_configsys Drive(L: removable 0.0 mb free )
12-17 13:29 DEBUG  TaskList: ## Finished Remove bootloader entry
12-17 13:29 DEBUG  TaskList: ## Running Remove target dir...
12-17 13:29 DEBUG  CommonBackend: Deleting D:\ubuntu
12-17 13:29 DEBUG  TaskList: ## Finished Remove target dir
12-17 13:29 DEBUG  TaskList: ## Running Remove registry key...
12-17 13:29 DEBUG  TaskList: ## Finished Remove registry key
12-17 13:29 DEBUG  TaskList: # Finished tasklist
12-17 13:29 INFO   root: Almost finished uninstalling
12-17 13:29 INFO   root: Finished uninstallation
12-17 13:29 DEBUG  CommonBackend: Fetching basic info...
12-17 13:29 DEBUG  CommonBackend: original_exe=D:\Downloads\wubi.exe
12-17 13:29 DEBUG  CommonBackend: platform=win32
12-17 13:29 DEBUG  CommonBackend: osname=nt
12-17 13:29 DEBUG  WindowsBackend: arch=amd64
12-17 13:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\data\isolist.ini
12-17 13:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 13:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 13:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 13:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 13:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 13:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 13:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 13:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 13:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-17 13:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-17 13:29 DEBUG  WindowsBackend: Fetching host info...
12-17 13:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 13:29 DEBUG  WindowsBackend: windows version=vista
12-17 13:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-17 13:29 DEBUG  WindowsBackend: windows_sp=None
12-17 13:29 DEBUG  WindowsBackend: windows_build=7100
12-17 13:29 DEBUG  WindowsBackend: gmt=-5
12-17 13:29 DEBUG  WindowsBackend: country=US
12-17 13:29 DEBUG  WindowsBackend: timezone=America/New_York
12-17 13:29 DEBUG  WindowsBackend: windows_username=JOE
12-17 13:29 DEBUG  WindowsBackend: user_full_name=JOE
12-17 13:29 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-17 13:29 DEBUG  WindowsBackend: windows_language_code=1033
12-17 13:29 DEBUG  WindowsBackend: windows_language=English
12-17 13:29 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-17 13:29 DEBUG  WindowsBackend: bootloader=vista
12-17 13:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2535.484375 mb free ntfs)
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(C: hd 2535.484375 mb free ntfs)
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(D: hd 650261.019531 mb free ntfs)
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(E: hd 30519.578125 mb free ntfs)
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: drive=Drive(L: removable 0.0 mb free )
12-17 13:29 DEBUG  WindowsBackend: uninstaller_path=None
12-17 13:29 DEBUG  WindowsBackend: previous_target_dir=None
12-17 13:29 DEBUG  WindowsBackend: previous_distro_name=None
12-17 13:29 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 13:29 DEBUG  WindowsBackend: keyboard_layout=us
12-17 13:29 DEBUG  WindowsBackend: keyboard_variant=
12-17 13:29 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-17 13:29 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 13:29 DEBUG  CommonBackend: Searching for local CDs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 13:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 13:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-17 13:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-17 13:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 13:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 13:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook Remix CD
12-17 13:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
12-17 13:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-17 13:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-17 13:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook Remix CD
12-17 13:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
12-17 13:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-17 13:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-17 13:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook Remix CD
12-17 13:30 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu Netbook CD
12-17 13:30 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
12-17 13:30 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
12-17 13:30 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Netbook Remix CD
12-17 13:30 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu Netbook CD
12-17 13:30 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
12-17 13:30 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
12-17 13:30 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:30 INFO   root: Running the installer...
12-17 13:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\translations, languages=['en_US', 'en']
12-17 13:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\translations, languages=['en_US', 'en']
12-17 13:30 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=joe
12-17 13:30 INFO   root: Received settings
12-17 13:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\translations, languages=['en_US', 'en']
12-17 13:30 DEBUG  TaskList: # Running tasklist...
12-17 13:30 DEBUG  TaskList: ## Running select_target_dir...
12-17 13:30 INFO   WindowsBackend: Installing into D:\ubuntu
12-17 13:30 DEBUG  TaskList: ## Finished select_target_dir
12-17 13:30 DEBUG  TaskList: ## Running create_dir_structure...
12-17 13:30 DEBUG  CommonBackend: Creating dir D:\ubuntu
12-17 13:30 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
12-17 13:30 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
12-17 13:30 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
12-17 13:30 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
12-17 13:30 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
12-17 13:30 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
12-17 13:30 DEBUG  TaskList: ## Finished create_dir_structure
12-17 13:30 DEBUG  TaskList: ## Running uncompress_target_dir...
12-17 13:30 DEBUG  TaskList: ## Finished uncompress_target_dir
12-17 13:30 DEBUG  TaskList: ## Running create_uninstaller...
12-17 13:30 DEBUG  WindowsBackend: Copying uninstaller D:\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
12-17 13:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
12-17 13:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
12-17 13:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
12-17 13:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Kubuntu.ico
12-17 13:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
12-17 13:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
12-17 13:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.kubuntu.org
12-17 13:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-17 13:30 DEBUG  TaskList: ## Finished create_uninstaller
12-17 13:30 DEBUG  TaskList: ## Running copy_installation_files...
12-17 13:30 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
12-17 13:30 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\winboot -> D:\ubuntu\winboot
12-17 13:30 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\data\images\Kubuntu.ico -> D:\ubuntu\Kubuntu.ico
12-17 13:30 DEBUG  TaskList: ## Finished copy_installation_files
12-17 13:30 DEBUG  TaskList: ## Running get_iso...
12-17 13:30 DEBUG  CommonBackend: Searching for local CD
12-17 13:30 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 13:30 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
12-17 13:30 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 13:30 DEBUG  CommonBackend: Searching for local ISO
12-17 13:30 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-17 13:30 DEBUG  TaskList: New task get_metalink
12-17 13:30 DEBUG  TaskList: ### Running get_metalink...
12-17 13:30 DEBUG  downloader: downloading http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink > D:\ubuntu\install
12-17 13:30 DEBUG  downloader: Download start filename=D:\ubuntu\install\kubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink, basename=kubuntu-9.10-desktop-i386.metalink, length=28219, text=None
12-17 13:30 DEBUG  downloader: download finished (read 28219 bytes)
12-17 13:30 DEBUG  downloader: downloading http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink > D:\ubuntu\install
12-17 13:30 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=282, text=None
12-17 13:30 DEBUG  downloader: download finished (read 282 bytes)
12-17 13:30 DEBUG  downloader: downloading http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink.gpg > D:\ubuntu\install
12-17 13:30 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
12-17 13:30 DEBUG  downloader: download finished (read 189 bytes)
12-17 13:30 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
12-17 13:30 INFO   saplog: Checking block bindings..
12-17 13:30 INFO   saplog: Key verified successfully.
12-17 13:30 DEBUG  CommonBackend: metalink md5sums:
900cf707b1fd37ff8eb6f8e7c6518090  kubuntu-9.10-alternate-amd64.metalink
539eb2637eb1519f474b315af2b02fd2  kubuntu-9.10-alternate-i386.metalink
9fd91ccd34288d0f9e804eb3bd13d202  kubuntu-9.10-desktop-amd64.metalink
59f61e753d5b315befc131896d34145d  kubuntu-9.10-desktop-i386.metalink

12-17 13:30 DEBUG  TaskList: ### Finished get_metalink
12-17 13:30 DEBUG  TaskList: New task download
12-17 13:30 DEBUG  TaskList: ### Running download...
12-17 13:30 DEBUG  btdownloader: downloading http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.iso.torrent > D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 13:36 DEBUG  TaskList: ### Finished download
12-17 13:36 DEBUG  TaskList: New task check_iso
12-17 13:36 DEBUG  TaskList: ### Running check_iso...
12-17 13:36 DEBUG  CommonBackend: Checking D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 13:36 DEBUG  Distro:   checking Kubuntu ISO D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 13:36 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 13:36 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-17 13:36 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-17 13:36 INFO   Distro: Found a valid iso for Kubuntu: D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 13:36 DEBUG  CommonBackend: Using distro Kubuntu i386 instead of Kubuntu amd64
12-17 13:36 DEBUG  TaskList: New task get_metalink
12-17 13:36 DEBUG  TaskList: #### Running get_metalink...
12-17 13:36 DEBUG  downloader: downloading http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink > D:\ubuntu\install
12-17 13:36 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink err=[Errno 9] Requested Range Not Satisfiable
12-17 13:36 DEBUG  downloader: downloading http://cdimage.ubuntu.com/kubuntu/daily-live/current/karmic-desktop-i386.metalink > D:\ubuntu\install
12-17 13:36 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/kubuntu/daily-live/current/karmic-desktop-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
12-17 13:36 DEBUG  TaskList: #### Finished get_metalink
12-17 13:36 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso, ignoring
12-17 13:36 DEBUG  TaskList: ### Finished check_iso
12-17 13:36 DEBUG  TaskList: ## Finished get_iso
12-17 13:36 DEBUG  TaskList: ## Running extract_kernel...
12-17 13:36 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 13:36 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 13:36 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 13:36 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 13:36 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
12-17 13:36 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
12-17 13:36 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = 284af6e5e36cc3cd8c096b00ad4a3f96 == 284af6e5e36cc3cd8c096b00ad4a3f96
12-17 13:36 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
12-17 13:36 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = 8d71e87fedb1986bdd3197669f6f355c == 8d71e87fedb1986bdd3197669f6f355c
12-17 13:36 DEBUG  TaskList: ## Finished extract_kernel
12-17 13:36 DEBUG  TaskList: ## Running choose_disk_sizes...
12-17 13:36 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
12-17 13:36 DEBUG  TaskList: ## Finished choose_disk_sizes
12-17 13:36 DEBUG  TaskList: ## Running create_preseed...
12-17 13:36 DEBUG  TaskList: ## Finished create_preseed
12-17 13:36 DEBUG  TaskList: ## Running modify_bootloader...
12-17 13:36 DEBUG  TaskList: New task modify_bcd
12-17 13:36 DEBUG  TaskList: ### Running modify_bcd...
12-17 13:36 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 2535.484375 mb free ntfs)
12-17 13:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {a13c9ec4-8c15-11de-acfe-d38a66c0a5d6}
12-17 13:36 DEBUG  TaskList: ### Finished modify_bcd
12-17 13:36 DEBUG  TaskList: New task modify_bcd
12-17 13:36 DEBUG  TaskList: ### Running modify_bcd...
12-17 13:36 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 650261.019531 mb free ntfs)
12-17 13:36 DEBUG  WindowsBackend: BCD has already been modified
12-17 13:36 DEBUG  TaskList: ### Finished modify_bcd
12-17 13:36 DEBUG  TaskList: New task modify_bcd
12-17 13:36 DEBUG  TaskList: ### Running modify_bcd...
12-17 13:36 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 30519.578125 mb free ntfs)
12-17 13:36 DEBUG  WindowsBackend: BCD has already been modified
12-17 13:36 DEBUG  TaskList: ### Finished modify_bcd
12-17 13:36 DEBUG  TaskList: New task modify_bcd
12-17 13:36 DEBUG  TaskList: ### Running modify_bcd...
12-17 13:36 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
12-17 13:36 DEBUG  WindowsBackend: BCD has already been modified
12-17 13:36 DEBUG  TaskList: ### Finished modify_bcd
12-17 13:36 DEBUG  TaskList: New task modify_bcd
12-17 13:36 DEBUG  TaskList: ### Running modify_bcd...
12-17 13:36 DEBUG  WindowsBackend: modify_bcd Drive(J: removable 0.0 mb free )
12-17 13:36 DEBUG  WindowsBackend: BCD has already been modified
12-17 13:36 DEBUG  TaskList: ### Finished modify_bcd
12-17 13:36 DEBUG  TaskList: New task modify_bcd
12-17 13:36 DEBUG  TaskList: ### Running modify_bcd...
12-17 13:36 DEBUG  WindowsBackend: modify_bcd Drive(K: removable 0.0 mb free )
12-17 13:36 DEBUG  WindowsBackend: BCD has already been modified
12-17 13:36 DEBUG  TaskList: ### Finished modify_bcd
12-17 13:36 DEBUG  TaskList: New task modify_bcd
12-17 13:36 DEBUG  TaskList: ### Running modify_bcd...
12-17 13:36 DEBUG  WindowsBackend: modify_bcd Drive(L: removable 0.0 mb free )
12-17 13:36 DEBUG  WindowsBackend: BCD has already been modified
12-17 13:36 DEBUG  TaskList: ### Finished modify_bcd
12-17 13:36 DEBUG  TaskList: ## Finished modify_bootloader
12-17 13:36 DEBUG  TaskList: ## Running modify_grub_configuration...
12-17 13:36 DEBUG  TaskList: ## Finished modify_grub_configuration
12-17 13:36 DEBUG  TaskList: ## Running create_virtual_disks...
12-17 13:36 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\root.disk of 16744MB
12-17 13:36 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\swap.disk of 256MB
12-17 13:36 DEBUG  TaskList: ## Finished create_virtual_disks
12-17 13:36 DEBUG  TaskList: ## Running uncompress_files...
12-17 13:36 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot /U /A /F
12-17 13:36 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot\*.* /U /A /F
12-17 13:36 DEBUG  TaskList: ## Finished uncompress_files
12-17 13:36 DEBUG  TaskList: ## Running eject_cd...
12-17 13:36 DEBUG  TaskList: ## Finished eject_cd
12-17 13:36 DEBUG  TaskList: # Finished tasklist
12-17 13:36 INFO   root: Almost finished installing
12-17 13:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl79E.tmp\translations, languages=['en_US', 'en']
12-17 13:37 INFO   root: Finished installation
12-17 13:37 INFO   root: Rebooting
12-17 13:37 DEBUG  TaskList: # Running tasklist...
12-17 13:37 DEBUG  TaskList: ## Running reboot...
12-17 13:37 DEBUG  TaskList: ## Finished reboot
12-17 13:37 DEBUG  TaskList: # Finished tasklist
12-17 13:37 DEBUG  root: application.quit
12-17 13:37 DEBUG  WindowsFrontend: frontend.quit
12-17 13:37 DEBUG  WindowsFrontend: frontend.on_quit
12-17 13:37 DEBUG  root: application.on_quit
12-17 13:37 INFO   root: sys.exit
12-17 14:06 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-17 14:06 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-17 14:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
12-17 14:06 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\data
12-17 14:06 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\bin\7z.exe
12-17 14:06 DEBUG  CommonBackend: Fetching basic info...
12-17 14:06 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
12-17 14:06 DEBUG  CommonBackend: platform=win32
12-17 14:06 DEBUG  CommonBackend: osname=nt
12-17 14:06 DEBUG  CommonBackend: language=en_US
12-17 14:06 DEBUG  CommonBackend: encoding=cp1252
12-17 14:06 DEBUG  WindowsBackend: arch=amd64
12-17 14:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\data\isolist.ini
12-17 14:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 14:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 14:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 14:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 14:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 14:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 14:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 14:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 14:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-17 14:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-17 14:06 DEBUG  WindowsBackend: Fetching host info...
12-17 14:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 14:06 DEBUG  WindowsBackend: windows version=vista
12-17 14:06 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-17 14:06 DEBUG  WindowsBackend: windows_sp=None
12-17 14:06 DEBUG  WindowsBackend: windows_build=7100
12-17 14:06 DEBUG  WindowsBackend: gmt=-5
12-17 14:06 DEBUG  WindowsBackend: country=US
12-17 14:06 DEBUG  WindowsBackend: timezone=America/New_York
12-17 14:06 DEBUG  WindowsBackend: windows_username=JOE
12-17 14:06 DEBUG  WindowsBackend: user_full_name=JOE
12-17 14:06 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-17 14:06 DEBUG  WindowsBackend: windows_language_code=1033
12-17 14:06 DEBUG  WindowsBackend: windows_language=English
12-17 14:06 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-17 14:06 DEBUG  WindowsBackend: bootloader=vista
12-17 14:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2573.38671875 mb free ntfs)
12-17 14:06 DEBUG  WindowsBackend: drive=Drive(C: hd 2573.38671875 mb free ntfs)
12-17 14:06 DEBUG  WindowsBackend: drive=Drive(D: hd 632576.824219 mb free ntfs)
12-17 14:06 DEBUG  WindowsBackend: drive=Drive(E: hd 30519.578125 mb free ntfs)
12-17 14:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-17 14:06 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 14:06 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-17 14:06 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
12-17 14:06 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
12-17 14:06 DEBUG  WindowsBackend: drive=Drive(L: removable 0.0 mb free )
12-17 14:06 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
12-17 14:06 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
12-17 14:06 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
12-17 14:06 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 14:06 DEBUG  WindowsBackend: keyboard_layout=us
12-17 14:06 DEBUG  WindowsBackend: keyboard_variant=
12-17 14:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 14:06 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 14:06 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-17 14:06 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 14:06 DEBUG  CommonBackend: Searching for local CDs
12-17 14:06 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp is a valid Ubuntu Netbook Remix CD
12-17 14:06 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp is a valid Kubuntu Netbook CD
12-17 14:06 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-17 14:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-17 14:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-17 14:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-17 14:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-17 14:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-17 14:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-17 14:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-17 14:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook Remix CD
12-17 14:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
12-17 14:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook Remix CD
12-17 14:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
12-17 14:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook Remix CD
12-17 14:06 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu Netbook CD
12-17 14:06 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Netbook Remix CD
12-17 14:06 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu Netbook CD
12-17 14:06 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
12-17 14:06 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 14:06 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
12-17 14:06 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
12-17 14:06 INFO   root: Running the uninstaller...
12-17 14:06 INFO   CommonBackend: This is the uninstaller running
12-17 14:06 DEBUG  WindowsFrontend: __init__...
12-17 14:06 DEBUG  WindowsFrontend: on_init...
12-17 14:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\translations, languages=['en_US', 'en']
12-17 14:06 INFO   root: Received settings
12-17 14:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\translations, languages=['en_US', 'en']
12-17 14:06 DEBUG  TaskList: # Running tasklist...
12-17 14:06 DEBUG  TaskList: ## Running Backup ISO...
12-17 14:06 DEBUG  TaskList: ## Finished Backup ISO
12-17 14:06 DEBUG  TaskList: ## Running Remove bootloader entry...
12-17 14:06 DEBUG  WindowsBackend: Removing bcd entry {a13c9ec4-8c15-11de-acfe-d38a66c0a5d6}
12-17 14:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
12-17 14:06 DEBUG  WindowsBackend: undo_bootini C:
12-17 14:06 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 2573.38671875 mb free ntfs)
12-17 14:06 DEBUG  WindowsBackend: undo_bootini D:
12-17 14:06 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 632576.824219 mb free ntfs)
12-17 14:06 DEBUG  WindowsBackend: undo_bootini E:
12-17 14:06 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 30519.578125 mb free ntfs)
12-17 14:06 DEBUG  WindowsBackend: undo_bootini I:
12-17 14:06 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
12-17 14:06 DEBUG  WindowsBackend: undo_bootini J:
12-17 14:06 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
12-17 14:06 DEBUG  WindowsBackend: undo_bootini K:
12-17 14:06 DEBUG  WindowsBackend: undo_configsys Drive(K: removable 0.0 mb free )
12-17 14:06 DEBUG  WindowsBackend: undo_bootini L:
12-17 14:06 DEBUG  WindowsBackend: undo_configsys Drive(L: removable 0.0 mb free )
12-17 14:06 DEBUG  TaskList: ## Finished Remove bootloader entry
12-17 14:06 DEBUG  TaskList: ## Running Remove target dir...
12-17 14:06 DEBUG  CommonBackend: Deleting D:\ubuntu
12-17 14:06 DEBUG  TaskList: ## Finished Remove target dir
12-17 14:06 DEBUG  TaskList: ## Running Remove registry key...
12-17 14:06 DEBUG  TaskList: ## Finished Remove registry key
12-17 14:06 DEBUG  TaskList: # Finished tasklist
12-17 14:06 INFO   root: Almost finished uninstalling
12-17 14:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl49E5.tmp\translations, languages=['en_US', 'en']
12-17 14:06 INFO   root: Finished uninstallation
12-17 14:06 DEBUG  root: application.quit
12-17 14:06 DEBUG  WindowsFrontend: frontend.quit
12-17 14:06 DEBUG  WindowsFrontend: frontend.on_quit
12-17 14:06 DEBUG  root: application.on_quit
12-17 14:06 INFO   root: sys.exit
12-17 14:09 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-17 14:09 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-17 14:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Downloads\\wubi.exe"']
12-17 14:09 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\data
12-17 14:09 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\bin\7z.exe
12-17 14:09 DEBUG  CommonBackend: Fetching basic info...
12-17 14:09 DEBUG  CommonBackend: original_exe=D:\Downloads\wubi.exe
12-17 14:09 DEBUG  CommonBackend: platform=win32
12-17 14:09 DEBUG  CommonBackend: osname=nt
12-17 14:09 DEBUG  CommonBackend: language=en_US
12-17 14:09 DEBUG  CommonBackend: encoding=cp1252
12-17 14:09 DEBUG  WindowsBackend: arch=amd64
12-17 14:09 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\data\isolist.ini
12-17 14:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 14:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 14:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 14:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 14:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 14:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 14:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 14:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 14:09 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-17 14:09 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-17 14:09 DEBUG  WindowsBackend: Fetching host info...
12-17 14:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 14:09 DEBUG  WindowsBackend: windows version=vista
12-17 14:09 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-17 14:09 DEBUG  WindowsBackend: windows_sp=None
12-17 14:09 DEBUG  WindowsBackend: windows_build=7100
12-17 14:09 DEBUG  WindowsBackend: gmt=-5
12-17 14:09 DEBUG  WindowsBackend: country=US
12-17 14:09 DEBUG  WindowsBackend: timezone=America/New_York
12-17 14:09 DEBUG  WindowsBackend: windows_username=JOE
12-17 14:09 DEBUG  WindowsBackend: user_full_name=JOE
12-17 14:09 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-17 14:09 DEBUG  WindowsBackend: windows_language_code=1033
12-17 14:09 DEBUG  WindowsBackend: windows_language=English
12-17 14:09 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-17 14:09 DEBUG  WindowsBackend: bootloader=vista
12-17 14:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2572.57421875 mb free ntfs)
12-17 14:09 DEBUG  WindowsBackend: drive=Drive(C: hd 2572.57421875 mb free ntfs)
12-17 14:09 DEBUG  WindowsBackend: drive=Drive(D: hd 650251.519531 mb free ntfs)
12-17 14:09 DEBUG  WindowsBackend: drive=Drive(E: hd 30519.578125 mb free ntfs)
12-17 14:09 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-17 14:09 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 14:09 DEBUG  WindowsBackend: uninstaller_path=None
12-17 14:09 DEBUG  WindowsBackend: previous_target_dir=None
12-17 14:09 DEBUG  WindowsBackend: previous_distro_name=None
12-17 14:09 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 14:09 DEBUG  WindowsBackend: keyboard_layout=us
12-17 14:09 DEBUG  WindowsBackend: keyboard_variant=
12-17 14:09 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 14:09 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 14:09 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-17 14:09 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 14:09 DEBUG  CommonBackend: Searching for local CDs
12-17 14:09 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp is a valid Ubuntu Netbook Remix CD
12-17 14:09 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp is a valid Kubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp is a valid Kubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp is a valid Kubuntu Netbook CD
12-17 14:09 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp is a valid Xubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp is a valid Xubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp is a valid Mythbuntu CD
12-17 14:09 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp is a valid Mythbuntu CD
12-17 14:09 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-17 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-17 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-17 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-17 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-17 14:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-17 14:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 14:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 14:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-17 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-17 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:09 INFO   root: Running the installer...
12-17 14:09 DEBUG  WindowsFrontend: __init__...
12-17 14:09 DEBUG  WindowsFrontend: on_init...
12-17 14:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\translations, languages=['en_US', 'en']
12-17 14:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\translations, languages=['en_US', 'en']
12-17 14:09 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=joe
12-17 14:09 INFO   root: Received settings
12-17 14:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\translations, languages=['en_US', 'en']
12-17 14:09 DEBUG  TaskList: # Running tasklist...
12-17 14:09 DEBUG  TaskList: ## Running select_target_dir...
12-17 14:09 INFO   WindowsBackend: Installing into D:\ubuntu
12-17 14:09 DEBUG  TaskList: ## Finished select_target_dir
12-17 14:09 DEBUG  TaskList: ## Running create_dir_structure...
12-17 14:09 DEBUG  CommonBackend: Creating dir D:\ubuntu
12-17 14:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
12-17 14:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
12-17 14:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
12-17 14:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
12-17 14:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
12-17 14:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
12-17 14:09 DEBUG  TaskList: ## Finished create_dir_structure
12-17 14:09 DEBUG  TaskList: ## Running uncompress_target_dir...
12-17 14:09 DEBUG  TaskList: ## Finished uncompress_target_dir
12-17 14:09 DEBUG  TaskList: ## Running create_uninstaller...
12-17 14:09 DEBUG  WindowsBackend: Copying uninstaller D:\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
12-17 14:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
12-17 14:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
12-17 14:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-17 14:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
12-17 14:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
12-17 14:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-17 14:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
12-17 14:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-17 14:09 DEBUG  TaskList: ## Finished create_uninstaller
12-17 14:09 DEBUG  TaskList: ## Running copy_installation_files...
12-17 14:09 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
12-17 14:09 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\winboot -> D:\ubuntu\winboot
12-17 14:09 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
12-17 14:09 DEBUG  TaskList: ## Finished copy_installation_files
12-17 14:09 DEBUG  TaskList: ## Running get_iso...
12-17 14:09 DEBUG  CommonBackend: Searching for local CD
12-17 14:09 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:09 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:09 DEBUG  CommonBackend: Searching for local ISO
12-17 14:09 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-17 14:09 DEBUG  TaskList: New task get_metalink
12-17 14:09 DEBUG  TaskList: ### Running get_metalink...
12-17 14:09 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink > D:\ubuntu\install
12-17 14:09 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
12-17 14:09 DEBUG  downloader: download finished (read 26651 bytes)
12-17 14:09 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink > D:\ubuntu\install
12-17 14:09 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
12-17 14:09 DEBUG  downloader: download finished (read 562 bytes)
12-17 14:09 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg > D:\ubuntu\install
12-17 14:09 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
12-17 14:09 DEBUG  downloader: download finished (read 189 bytes)
12-17 14:09 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
12-17 14:09 INFO   saplog: Checking block bindings..
12-17 14:09 INFO   saplog: Key verified successfully.
12-17 14:09 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

12-17 14:09 DEBUG  TaskList: ### Finished get_metalink
12-17 14:09 DEBUG  TaskList: New task download
12-17 14:09 DEBUG  TaskList: ### Running download...
12-17 14:09 DEBUG  btdownloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent > D:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 14:15 DEBUG  TaskList: ### Finished download
12-17 14:15 DEBUG  TaskList: New task check_iso
12-17 14:15 DEBUG  TaskList: ### Running check_iso...
12-17 14:15 DEBUG  CommonBackend: Checking D:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 14:15 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 14:15 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 14:15 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
12-17 14:15 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
12-17 14:15 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 14:15 DEBUG  TaskList: New task get_file_md5
12-17 14:15 DEBUG  TaskList: #### Running get_file_md5...
12-17 14:15 DEBUG  TaskList: #### Finished get_file_md5
12-17 14:15 DEBUG  TaskList: ### Finished check_iso
12-17 14:15 DEBUG  TaskList: ## Finished get_iso
12-17 14:15 DEBUG  TaskList: ## Running extract_kernel...
12-17 14:15 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 14:15 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 14:15 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 14:15 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 14:15 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
12-17 14:15 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
12-17 14:15 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = f2bec09da1b46a21c0e6cc3192ca2e4f == f2bec09da1b46a21c0e6cc3192ca2e4f
12-17 14:15 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
12-17 14:15 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = e09f7d0e9500f67156730ad6093ce225 == e09f7d0e9500f67156730ad6093ce225
12-17 14:15 DEBUG  TaskList: ## Finished extract_kernel
12-17 14:15 DEBUG  TaskList: ## Running choose_disk_sizes...
12-17 14:15 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
12-17 14:15 DEBUG  TaskList: ## Finished choose_disk_sizes
12-17 14:15 DEBUG  TaskList: ## Running create_preseed...
12-17 14:15 DEBUG  TaskList: ## Finished create_preseed
12-17 14:15 DEBUG  TaskList: ## Running modify_bootloader...
12-17 14:15 DEBUG  TaskList: New task modify_bcd
12-17 14:15 DEBUG  TaskList: ### Running modify_bcd...
12-17 14:15 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 2572.57421875 mb free ntfs)
12-17 14:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {a13c9ec5-8c15-11de-acfe-d38a66c0a5d6}
12-17 14:15 DEBUG  TaskList: ### Finished modify_bcd
12-17 14:15 DEBUG  TaskList: New task modify_bcd
12-17 14:15 DEBUG  TaskList: ### Running modify_bcd...
12-17 14:15 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 650251.519531 mb free ntfs)
12-17 14:15 DEBUG  WindowsBackend: BCD has already been modified
12-17 14:15 DEBUG  TaskList: ### Finished modify_bcd
12-17 14:15 DEBUG  TaskList: New task modify_bcd
12-17 14:15 DEBUG  TaskList: ### Running modify_bcd...
12-17 14:15 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 30519.578125 mb free ntfs)
12-17 14:15 DEBUG  WindowsBackend: BCD has already been modified
12-17 14:15 DEBUG  TaskList: ### Finished modify_bcd
12-17 14:15 DEBUG  TaskList: ## Finished modify_bootloader
12-17 14:15 DEBUG  TaskList: ## Running modify_grub_configuration...
12-17 14:15 DEBUG  TaskList: ## Finished modify_grub_configuration
12-17 14:15 DEBUG  TaskList: ## Running create_virtual_disks...
12-17 14:15 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\root.disk of 16744MB
12-17 14:15 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\swap.disk of 256MB
12-17 14:15 DEBUG  TaskList: ## Finished create_virtual_disks
12-17 14:15 DEBUG  TaskList: ## Running uncompress_files...
12-17 14:15 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot /U /A /F
12-17 14:15 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot\*.* /U /A /F
12-17 14:15 DEBUG  TaskList: ## Finished uncompress_files
12-17 14:15 DEBUG  TaskList: ## Running eject_cd...
12-17 14:15 DEBUG  TaskList: ## Finished eject_cd
12-17 14:15 DEBUG  TaskList: # Finished tasklist
12-17 14:15 INFO   root: Almost finished installing
12-17 14:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylED1F.tmp\translations, languages=['en_US', 'en']
12-17 14:15 INFO   root: Finished installation
12-17 14:15 INFO   root: Rebooting
12-17 14:15 DEBUG  TaskList: # Running tasklist...
12-17 14:15 DEBUG  TaskList: ## Running reboot...
12-17 14:15 DEBUG  TaskList: ## Finished reboot
12-17 14:15 DEBUG  TaskList: # Finished tasklist
12-17 14:15 DEBUG  root: application.quit
12-17 14:15 DEBUG  WindowsFrontend: frontend.quit
12-17 14:15 DEBUG  WindowsFrontend: frontend.on_quit
12-17 14:15 DEBUG  root: application.on_quit
12-17 14:15 INFO   root: sys.exit
12-17 14:19 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-17 14:19 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-17 14:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
12-17 14:19 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\data
12-17 14:19 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\bin\7z.exe
12-17 14:19 DEBUG  CommonBackend: Fetching basic info...
12-17 14:19 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
12-17 14:19 DEBUG  CommonBackend: platform=win32
12-17 14:19 DEBUG  CommonBackend: osname=nt
12-17 14:19 DEBUG  CommonBackend: language=en_US
12-17 14:19 DEBUG  CommonBackend: encoding=cp1252
12-17 14:19 DEBUG  WindowsBackend: arch=amd64
12-17 14:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\data\isolist.ini
12-17 14:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 14:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 14:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 14:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 14:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 14:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 14:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 14:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 14:19 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-17 14:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-17 14:19 DEBUG  WindowsBackend: Fetching host info...
12-17 14:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 14:19 DEBUG  WindowsBackend: windows version=vista
12-17 14:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-17 14:19 DEBUG  WindowsBackend: windows_sp=None
12-17 14:19 DEBUG  WindowsBackend: windows_build=7100
12-17 14:19 DEBUG  WindowsBackend: gmt=-5
12-17 14:19 DEBUG  WindowsBackend: country=US
12-17 14:19 DEBUG  WindowsBackend: timezone=America/New_York
12-17 14:19 DEBUG  WindowsBackend: windows_username=JOE
12-17 14:19 DEBUG  WindowsBackend: user_full_name=JOE
12-17 14:19 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-17 14:19 DEBUG  WindowsBackend: windows_language_code=1033
12-17 14:19 DEBUG  WindowsBackend: windows_language=English
12-17 14:19 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-17 14:19 DEBUG  WindowsBackend: bootloader=vista
12-17 14:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2553.92578125 mb free ntfs)
12-17 14:19 DEBUG  WindowsBackend: drive=Drive(C: hd 2553.92578125 mb free ntfs)
12-17 14:19 DEBUG  WindowsBackend: drive=Drive(D: hd 632559.816406 mb free ntfs)
12-17 14:19 DEBUG  WindowsBackend: drive=Drive(E: hd 30519.578125 mb free ntfs)
12-17 14:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-17 14:19 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 14:19 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
12-17 14:19 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
12-17 14:19 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-17 14:19 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 14:19 DEBUG  WindowsBackend: keyboard_layout=us
12-17 14:19 DEBUG  WindowsBackend: keyboard_variant=
12-17 14:19 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 14:19 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 14:19 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-17 14:19 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 14:19 DEBUG  CommonBackend: Searching for local CDs
12-17 14:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp is a valid Ubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp is a valid Ubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp is a valid Ubuntu Netbook Remix CD
12-17 14:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp is a valid Kubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp is a valid Kubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp is a valid Kubuntu Netbook CD
12-17 14:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp is a valid Xubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp is a valid Xubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp is a valid Mythbuntu CD
12-17 14:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp is a valid Mythbuntu CD
12-17 14:19 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-17 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-17 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 14:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-17 14:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-17 14:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 14:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 14:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-17 14:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-17 14:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 14:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 14:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-17 14:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-17 14:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 14:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 14:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:19 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 14:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:19 INFO   root: Running the uninstaller...
12-17 14:19 INFO   CommonBackend: This is the uninstaller running
12-17 14:19 DEBUG  WindowsFrontend: __init__...
12-17 14:19 DEBUG  WindowsFrontend: on_init...
12-17 14:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\translations, languages=['en_US', 'en']
12-17 14:19 INFO   root: Received settings
12-17 14:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\translations, languages=['en_US', 'en']
12-17 14:19 DEBUG  TaskList: # Running tasklist...
12-17 14:19 DEBUG  TaskList: ## Running Backup ISO...
12-17 14:19 DEBUG  TaskList: ## Finished Backup ISO
12-17 14:19 DEBUG  TaskList: ## Running Remove bootloader entry...
12-17 14:19 DEBUG  WindowsBackend: Removing bcd entry {a13c9ec5-8c15-11de-acfe-d38a66c0a5d6}
12-17 14:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
12-17 14:19 DEBUG  WindowsBackend: undo_bootini C:
12-17 14:19 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 2553.92578125 mb free ntfs)
12-17 14:19 DEBUG  WindowsBackend: undo_bootini D:
12-17 14:19 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 632559.816406 mb free ntfs)
12-17 14:19 DEBUG  WindowsBackend: undo_bootini E:
12-17 14:19 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 30519.578125 mb free ntfs)
12-17 14:19 DEBUG  TaskList: ## Finished Remove bootloader entry
12-17 14:19 DEBUG  TaskList: ## Running Remove target dir...
12-17 14:19 DEBUG  CommonBackend: Deleting D:\ubuntu
12-17 14:19 DEBUG  TaskList: ## Finished Remove target dir
12-17 14:19 DEBUG  TaskList: ## Running Remove registry key...
12-17 14:19 DEBUG  TaskList: ## Finished Remove registry key
12-17 14:19 DEBUG  TaskList: # Finished tasklist
12-17 14:19 INFO   root: Almost finished uninstalling
12-17 14:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylDD9E.tmp\translations, languages=['en_US', 'en']
12-17 14:19 INFO   root: Finished uninstallation
12-17 14:19 DEBUG  root: application.quit
12-17 14:19 DEBUG  WindowsFrontend: frontend.quit
12-17 14:19 DEBUG  WindowsFrontend: frontend.on_quit
12-17 14:19 DEBUG  root: application.on_quit
12-17 14:19 INFO   root: sys.exit
12-17 14:21 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-17 14:21 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-17 14:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
12-17 14:21 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\data
12-17 14:21 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\bin\7z.exe
12-17 14:21 DEBUG  CommonBackend: Fetching basic info...
12-17 14:21 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-17 14:21 DEBUG  CommonBackend: platform=win32
12-17 14:21 DEBUG  CommonBackend: osname=nt
12-17 14:21 DEBUG  CommonBackend: language=en_US
12-17 14:21 DEBUG  CommonBackend: encoding=cp1252
12-17 14:21 DEBUG  WindowsBackend: arch=amd64
12-17 14:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\data\isolist.ini
12-17 14:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 14:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 14:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 14:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 14:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 14:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 14:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 14:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 14:21 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-17 14:21 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-17 14:21 DEBUG  WindowsBackend: Fetching host info...
12-17 14:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 14:21 DEBUG  WindowsBackend: windows version=vista
12-17 14:21 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-17 14:21 DEBUG  WindowsBackend: windows_sp=None
12-17 14:21 DEBUG  WindowsBackend: windows_build=7100
12-17 14:21 DEBUG  WindowsBackend: gmt=-5
12-17 14:21 DEBUG  WindowsBackend: country=US
12-17 14:21 DEBUG  WindowsBackend: timezone=America/New_York
12-17 14:21 DEBUG  WindowsBackend: windows_username=JOE
12-17 14:21 DEBUG  WindowsBackend: user_full_name=JOE
12-17 14:21 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-17 14:21 DEBUG  WindowsBackend: windows_language_code=1033
12-17 14:21 DEBUG  WindowsBackend: windows_language=English
12-17 14:21 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-17 14:21 DEBUG  WindowsBackend: bootloader=vista
12-17 14:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2550.64453125 mb free ntfs)
12-17 14:21 DEBUG  WindowsBackend: drive=Drive(C: hd 2550.64453125 mb free ntfs)
12-17 14:21 DEBUG  WindowsBackend: drive=Drive(D: hd 650261.519531 mb free ntfs)
12-17 14:21 DEBUG  WindowsBackend: drive=Drive(E: hd 30519.578125 mb free ntfs)
12-17 14:21 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-17 14:21 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 14:21 DEBUG  WindowsBackend: uninstaller_path=None
12-17 14:21 DEBUG  WindowsBackend: previous_target_dir=None
12-17 14:21 DEBUG  WindowsBackend: previous_distro_name=None
12-17 14:21 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 14:21 DEBUG  WindowsBackend: keyboard_layout=us
12-17 14:21 DEBUG  WindowsBackend: keyboard_variant=
12-17 14:21 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 14:21 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 14:21 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-17 14:21 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 14:21 DEBUG  CommonBackend: Searching for local CDs
12-17 14:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp is a valid Ubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp is a valid Ubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp is a valid Ubuntu Netbook Remix CD
12-17 14:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp is a valid Kubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp is a valid Kubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp is a valid Kubuntu Netbook CD
12-17 14:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp is a valid Xubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp is a valid Xubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp is a valid Mythbuntu CD
12-17 14:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp is a valid Mythbuntu CD
12-17 14:21 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-17 14:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-17 14:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 14:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 14:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-17 14:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-17 14:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 14:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 14:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-17 14:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-17 14:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 14:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 14:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-17 14:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-17 14:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 14:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 14:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:21 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 14:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:21 INFO   root: Running the installer...
12-17 14:21 DEBUG  WindowsFrontend: __init__...
12-17 14:21 DEBUG  WindowsFrontend: on_init...
12-17 14:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\translations, languages=['en_US', 'en']
12-17 14:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\translations, languages=['en_US', 'en']
12-17 14:22 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=joe
12-17 14:22 INFO   root: Received settings
12-17 14:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\translations, languages=['en_US', 'en']
12-17 14:22 DEBUG  TaskList: # Running tasklist...
12-17 14:22 DEBUG  TaskList: ## Running select_target_dir...
12-17 14:22 INFO   WindowsBackend: Installing into D:\ubuntu
12-17 14:22 DEBUG  TaskList: ## Finished select_target_dir
12-17 14:22 DEBUG  TaskList: ## Running create_dir_structure...
12-17 14:22 DEBUG  CommonBackend: Creating dir D:\ubuntu
12-17 14:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
12-17 14:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
12-17 14:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
12-17 14:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
12-17 14:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
12-17 14:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
12-17 14:22 DEBUG  TaskList: ## Finished create_dir_structure
12-17 14:22 DEBUG  TaskList: ## Running uncompress_target_dir...
12-17 14:22 DEBUG  TaskList: ## Finished uncompress_target_dir
12-17 14:22 DEBUG  TaskList: ## Running create_uninstaller...
12-17 14:22 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
12-17 14:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
12-17 14:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
12-17 14:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
12-17 14:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Kubuntu.ico
12-17 14:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
12-17 14:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
12-17 14:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.kubuntu.org
12-17 14:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-17 14:22 DEBUG  TaskList: ## Finished create_uninstaller
12-17 14:22 DEBUG  TaskList: ## Running copy_installation_files...
12-17 14:22 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
12-17 14:22 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\winboot -> D:\ubuntu\winboot
12-17 14:22 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\data\images\Kubuntu.ico -> D:\ubuntu\Kubuntu.ico
12-17 14:22 DEBUG  TaskList: ## Finished copy_installation_files
12-17 14:22 DEBUG  TaskList: ## Running get_iso...
12-17 14:22 DEBUG  CommonBackend: Searching for local CD
12-17 14:22 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp is a valid Kubuntu CD
12-17 14:22 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\casper\filesystem.squashfs
12-17 14:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 14:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 14:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 14:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 14:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 14:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 14:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 14:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 14:22 DEBUG  CommonBackend: Searching for local ISO
12-17 14:22 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-17 14:22 DEBUG  TaskList: New task get_metalink
12-17 14:22 DEBUG  TaskList: ### Running get_metalink...
12-17 14:22 DEBUG  downloader: downloading http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink > D:\ubuntu\install
12-17 14:22 DEBUG  downloader: Download start filename=D:\ubuntu\install\kubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink, basename=kubuntu-9.10-desktop-i386.metalink, length=28219, text=None
12-17 14:22 DEBUG  downloader: download finished (read 28219 bytes)
12-17 14:22 DEBUG  downloader: downloading http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink > D:\ubuntu\install
12-17 14:22 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=282, text=None
12-17 14:22 DEBUG  downloader: download finished (read 282 bytes)
12-17 14:22 DEBUG  downloader: downloading http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink.gpg > D:\ubuntu\install
12-17 14:22 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
12-17 14:22 DEBUG  downloader: download finished (read 189 bytes)
12-17 14:22 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
12-17 14:22 INFO   saplog: Checking block bindings..
12-17 14:22 INFO   saplog: Key verified successfully.
12-17 14:22 DEBUG  CommonBackend: metalink md5sums:
900cf707b1fd37ff8eb6f8e7c6518090  kubuntu-9.10-alternate-amd64.metalink
539eb2637eb1519f474b315af2b02fd2  kubuntu-9.10-alternate-i386.metalink
9fd91ccd34288d0f9e804eb3bd13d202  kubuntu-9.10-desktop-amd64.metalink
59f61e753d5b315befc131896d34145d  kubuntu-9.10-desktop-i386.metalink

12-17 14:22 DEBUG  TaskList: ### Finished get_metalink
12-17 14:22 DEBUG  TaskList: New task download
12-17 14:22 DEBUG  TaskList: ### Running download...
12-17 14:22 DEBUG  btdownloader: downloading http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.iso.torrent > D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 14:29 DEBUG  TaskList: ### Finished download
12-17 14:29 DEBUG  TaskList: New task check_iso
12-17 14:29 DEBUG  TaskList: ### Running check_iso...
12-17 14:29 DEBUG  CommonBackend: Checking D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 14:29 DEBUG  Distro:   checking Kubuntu ISO D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 14:29 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 14:29 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-17 14:29 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-17 14:29 INFO   Distro: Found a valid iso for Kubuntu: D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 14:29 DEBUG  CommonBackend: Using distro Kubuntu i386 instead of Kubuntu amd64
12-17 14:29 DEBUG  TaskList: New task get_metalink
12-17 14:29 DEBUG  TaskList: #### Running get_metalink...
12-17 14:29 DEBUG  downloader: downloading http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink > D:\ubuntu\install
12-17 14:29 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink err=[Errno 9] Requested Range Not Satisfiable
12-17 14:29 DEBUG  downloader: downloading http://cdimage.ubuntu.com/kubuntu/daily-live/current/karmic-desktop-i386.metalink > D:\ubuntu\install
12-17 14:29 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/kubuntu/daily-live/current/karmic-desktop-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
12-17 14:29 DEBUG  TaskList: #### Finished get_metalink
12-17 14:29 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso, ignoring
12-17 14:29 DEBUG  TaskList: ### Finished check_iso
12-17 14:29 DEBUG  TaskList: ## Finished get_iso
12-17 14:29 DEBUG  TaskList: ## Running extract_kernel...
12-17 14:29 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 14:29 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 14:29 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 14:29 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
12-17 14:29 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
12-17 14:29 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
12-17 14:29 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = 284af6e5e36cc3cd8c096b00ad4a3f96 == 284af6e5e36cc3cd8c096b00ad4a3f96
12-17 14:29 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
12-17 14:29 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = 8d71e87fedb1986bdd3197669f6f355c == 8d71e87fedb1986bdd3197669f6f355c
12-17 14:29 DEBUG  TaskList: ## Finished extract_kernel
12-17 14:29 DEBUG  TaskList: ## Running choose_disk_sizes...
12-17 14:29 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
12-17 14:29 DEBUG  TaskList: ## Finished choose_disk_sizes
12-17 14:29 DEBUG  TaskList: ## Running create_preseed...
12-17 14:29 DEBUG  TaskList: ## Finished create_preseed
12-17 14:29 DEBUG  TaskList: ## Running modify_bootloader...
12-17 14:29 DEBUG  TaskList: New task modify_bcd
12-17 14:29 DEBUG  TaskList: ### Running modify_bcd...
12-17 14:29 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 2550.64453125 mb free ntfs)
12-17 14:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {a13c9ec6-8c15-11de-acfe-d38a66c0a5d6}
12-17 14:29 DEBUG  TaskList: ### Finished modify_bcd
12-17 14:29 DEBUG  TaskList: New task modify_bcd
12-17 14:29 DEBUG  TaskList: ### Running modify_bcd...
12-17 14:29 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 650261.519531 mb free ntfs)
12-17 14:29 DEBUG  WindowsBackend: BCD has already been modified
12-17 14:29 DEBUG  TaskList: ### Finished modify_bcd
12-17 14:29 DEBUG  TaskList: New task modify_bcd
12-17 14:29 DEBUG  TaskList: ### Running modify_bcd...
12-17 14:29 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 30519.578125 mb free ntfs)
12-17 14:29 DEBUG  WindowsBackend: BCD has already been modified
12-17 14:29 DEBUG  TaskList: ### Finished modify_bcd
12-17 14:29 DEBUG  TaskList: ## Finished modify_bootloader
12-17 14:29 DEBUG  TaskList: ## Running modify_grub_configuration...
12-17 14:29 DEBUG  TaskList: ## Finished modify_grub_configuration
12-17 14:29 DEBUG  TaskList: ## Running create_virtual_disks...
12-17 14:29 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\root.disk of 16744MB
12-17 14:29 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\swap.disk of 256MB
12-17 14:29 DEBUG  TaskList: ## Finished create_virtual_disks
12-17 14:29 DEBUG  TaskList: ## Running uncompress_files...
12-17 14:29 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot /U /A /F
12-17 14:29 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot\*.* /U /A /F
12-17 14:29 DEBUG  TaskList: ## Finished uncompress_files
12-17 14:29 DEBUG  TaskList: ## Running eject_cd...
12-17 14:29 DEBUG  TaskList: ## Finished eject_cd
12-17 14:29 DEBUG  TaskList: # Finished tasklist
12-17 14:29 INFO   root: Almost finished installing
12-17 14:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl539F.tmp\translations, languages=['en_US', 'en']
12-17 14:30 INFO   root: Finished installation
12-17 14:30 INFO   root: Rebooting
12-17 14:30 DEBUG  TaskList: # Running tasklist...
12-17 14:30 DEBUG  TaskList: ## Running reboot...
12-17 14:30 DEBUG  TaskList: ## Finished reboot
12-17 14:30 DEBUG  TaskList: # Finished tasklist
12-17 14:30 DEBUG  root: application.quit
12-17 14:30 DEBUG  WindowsFrontend: frontend.quit
12-17 14:30 DEBUG  WindowsFrontend: frontend.on_quit
12-17 14:30 DEBUG  root: application.on_quit
12-17 14:30 INFO   root: sys.exit
12-17 15:03 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-17 15:03 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-17 15:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
12-17 15:03 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\data
12-17 15:03 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\bin\7z.exe
12-17 15:03 DEBUG  CommonBackend: Fetching basic info...
12-17 15:03 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
12-17 15:03 DEBUG  CommonBackend: platform=win32
12-17 15:03 DEBUG  CommonBackend: osname=nt
12-17 15:03 DEBUG  CommonBackend: language=en_US
12-17 15:03 DEBUG  CommonBackend: encoding=cp1252
12-17 15:03 DEBUG  WindowsBackend: arch=amd64
12-17 15:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\data\isolist.ini
12-17 15:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-17 15:03 DEBUG  WindowsBackend: Fetching host info...
12-17 15:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 15:03 DEBUG  WindowsBackend: windows version=vista
12-17 15:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-17 15:03 DEBUG  WindowsBackend: windows_sp=None
12-17 15:03 DEBUG  WindowsBackend: windows_build=7100
12-17 15:03 DEBUG  WindowsBackend: gmt=-5
12-17 15:03 DEBUG  WindowsBackend: country=US
12-17 15:03 DEBUG  WindowsBackend: timezone=America/New_York
12-17 15:03 DEBUG  WindowsBackend: windows_username=JOE
12-17 15:03 DEBUG  WindowsBackend: user_full_name=JOE
12-17 15:03 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-17 15:03 DEBUG  WindowsBackend: windows_language_code=1033
12-17 15:03 DEBUG  WindowsBackend: windows_language=English
12-17 15:03 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-17 15:03 DEBUG  WindowsBackend: bootloader=vista
12-17 15:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2576.12109375 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(C: hd 2576.12109375 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(D: hd 632577.320313 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(E: hd 30519.578125 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 15:03 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
12-17 15:03 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
12-17 15:03 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
12-17 15:03 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 15:03 DEBUG  WindowsBackend: keyboard_layout=us
12-17 15:03 DEBUG  WindowsBackend: keyboard_variant=
12-17 15:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 15:03 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 15:03 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-17 15:03 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 15:03 DEBUG  CommonBackend: Searching for local CDs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 INFO   root: Running the uninstaller...
12-17 15:03 INFO   CommonBackend: This is the uninstaller running
12-17 15:03 DEBUG  WindowsFrontend: __init__...
12-17 15:03 DEBUG  WindowsFrontend: on_init...
12-17 15:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylE7F9.tmp\translations, languages=['en_US', 'en']
12-17 15:03 INFO   WindowsFrontend: Operation cancelled
12-17 15:03 DEBUG  WindowsFrontend: frontend.quit
12-17 15:03 DEBUG  WindowsFrontend: frontend.on_quit
12-17 15:03 DEBUG  root: application.on_quit
12-17 15:03 INFO   root: sys.exit
12-17 15:03 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-17 15:03 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-17 15:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
12-17 15:03 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\data
12-17 15:03 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\bin\7z.exe
12-17 15:03 DEBUG  CommonBackend: Fetching basic info...
12-17 15:03 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
12-17 15:03 DEBUG  CommonBackend: platform=win32
12-17 15:03 DEBUG  CommonBackend: osname=nt
12-17 15:03 DEBUG  CommonBackend: language=en_US
12-17 15:03 DEBUG  CommonBackend: encoding=cp1252
12-17 15:03 DEBUG  WindowsBackend: arch=amd64
12-17 15:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\data\isolist.ini
12-17 15:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-17 15:03 DEBUG  WindowsBackend: Fetching host info...
12-17 15:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 15:03 DEBUG  WindowsBackend: windows version=vista
12-17 15:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-17 15:03 DEBUG  WindowsBackend: windows_sp=None
12-17 15:03 DEBUG  WindowsBackend: windows_build=7100
12-17 15:03 DEBUG  WindowsBackend: gmt=-5
12-17 15:03 DEBUG  WindowsBackend: country=US
12-17 15:03 DEBUG  WindowsBackend: timezone=America/New_York
12-17 15:03 DEBUG  WindowsBackend: windows_username=JOE
12-17 15:03 DEBUG  WindowsBackend: user_full_name=JOE
12-17 15:03 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-17 15:03 DEBUG  WindowsBackend: windows_language_code=1033
12-17 15:03 DEBUG  WindowsBackend: windows_language=English
12-17 15:03 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-17 15:03 DEBUG  WindowsBackend: bootloader=vista
12-17 15:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2575.96875 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(C: hd 2575.96875 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(D: hd 632577.320313 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(E: hd 30519.578125 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 15:03 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
12-17 15:03 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
12-17 15:03 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
12-17 15:03 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 15:03 DEBUG  WindowsBackend: keyboard_layout=us
12-17 15:03 DEBUG  WindowsBackend: keyboard_variant=
12-17 15:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 15:03 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 15:03 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-17 15:03 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 15:03 DEBUG  CommonBackend: Searching for local CDs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:03 INFO   root: Running the uninstaller...
12-17 15:03 INFO   CommonBackend: This is the uninstaller running
12-17 15:03 DEBUG  WindowsFrontend: __init__...
12-17 15:03 DEBUG  WindowsFrontend: on_init...
12-17 15:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\translations, languages=['en_US', 'en']
12-17 15:03 INFO   root: Received settings
12-17 15:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\translations, languages=['en_US', 'en']
12-17 15:03 DEBUG  TaskList: # Running tasklist...
12-17 15:03 DEBUG  TaskList: ## Running Backup ISO...
12-17 15:03 DEBUG  TaskList: ## Finished Backup ISO
12-17 15:03 DEBUG  TaskList: ## Running Remove bootloader entry...
12-17 15:03 DEBUG  WindowsBackend: Removing bcd entry {a13c9ec6-8c15-11de-acfe-d38a66c0a5d6}
12-17 15:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
12-17 15:03 DEBUG  WindowsBackend: undo_bootini C:
12-17 15:03 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 2575.96875 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: undo_bootini D:
12-17 15:03 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 632577.320313 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: undo_bootini E:
12-17 15:03 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 30519.578125 mb free ntfs)
12-17 15:03 DEBUG  TaskList: ## Finished Remove bootloader entry
12-17 15:03 DEBUG  TaskList: ## Running Remove target dir...
12-17 15:03 DEBUG  CommonBackend: Deleting D:\ubuntu
12-17 15:03 DEBUG  TaskList: ## Finished Remove target dir
12-17 15:03 DEBUG  TaskList: ## Running Remove registry key...
12-17 15:03 DEBUG  TaskList: ## Finished Remove registry key
12-17 15:03 DEBUG  TaskList: # Finished tasklist
12-17 15:03 INFO   root: Almost finished uninstalling
12-17 15:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl48E6.tmp\translations, languages=['en_US', 'en']
12-17 15:03 INFO   root: Finished uninstallation
12-17 15:03 DEBUG  root: application.quit
12-17 15:03 DEBUG  WindowsFrontend: frontend.quit
12-17 15:03 DEBUG  WindowsFrontend: frontend.on_quit
12-17 15:03 DEBUG  root: application.on_quit
12-17 15:03 INFO   root: sys.exit
12-17 15:03 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-17 15:03 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-17 15:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
12-17 15:03 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\data
12-17 15:03 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\bin\7z.exe
12-17 15:03 DEBUG  CommonBackend: Fetching basic info...
12-17 15:03 DEBUG  CommonBackend: original_exe=E:\wubi.exe
12-17 15:03 DEBUG  CommonBackend: platform=win32
12-17 15:03 DEBUG  CommonBackend: osname=nt
12-17 15:03 DEBUG  CommonBackend: language=en_US
12-17 15:03 DEBUG  CommonBackend: encoding=cp1252
12-17 15:03 DEBUG  WindowsBackend: arch=amd64
12-17 15:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\data\isolist.ini
12-17 15:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 15:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-17 15:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-17 15:03 DEBUG  WindowsBackend: Fetching host info...
12-17 15:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 15:03 DEBUG  WindowsBackend: windows version=vista
12-17 15:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-17 15:03 DEBUG  WindowsBackend: windows_sp=None
12-17 15:03 DEBUG  WindowsBackend: windows_build=7100
12-17 15:03 DEBUG  WindowsBackend: gmt=-5
12-17 15:03 DEBUG  WindowsBackend: country=US
12-17 15:03 DEBUG  WindowsBackend: timezone=America/New_York
12-17 15:03 DEBUG  WindowsBackend: windows_username=JOE
12-17 15:03 DEBUG  WindowsBackend: user_full_name=JOE
12-17 15:03 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-17 15:03 DEBUG  WindowsBackend: windows_language_code=1033
12-17 15:03 DEBUG  WindowsBackend: windows_language=English
12-17 15:03 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-17 15:03 DEBUG  WindowsBackend: bootloader=vista
12-17 15:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2574.92578125 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(C: hd 2574.92578125 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(D: hd 650261.515625 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(E: hd 30518.1757813 mb free ntfs)
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-17 15:03 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 15:03 DEBUG  WindowsBackend: uninstaller_path=None
12-17 15:03 DEBUG  WindowsBackend: previous_target_dir=None
12-17 15:03 DEBUG  WindowsBackend: previous_distro_name=None
12-17 15:03 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 15:03 DEBUG  WindowsBackend: keyboard_layout=us
12-17 15:03 DEBUG  WindowsBackend: keyboard_variant=
12-17 15:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 15:03 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 15:03 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-17 15:03 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 15:03 DEBUG  CommonBackend: Searching for local CDs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 15:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-17 15:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-17 15:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 15:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 15:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
12-17 15:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
12-17 15:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 15:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 15:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:04 INFO   root: Running the installer...
12-17 15:04 DEBUG  WindowsFrontend: __init__...
12-17 15:04 DEBUG  WindowsFrontend: on_init...
12-17 15:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\translations, languages=['en_US', 'en']
12-17 15:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\translations, languages=['en_US', 'en']
12-17 15:04 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=joe
12-17 15:04 INFO   root: Received settings
12-17 15:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\translations, languages=['en_US', 'en']
12-17 15:04 DEBUG  TaskList: # Running tasklist...
12-17 15:04 DEBUG  TaskList: ## Running select_target_dir...
12-17 15:04 INFO   WindowsBackend: Installing into E:\ubuntu
12-17 15:04 DEBUG  TaskList: ## Finished select_target_dir
12-17 15:04 DEBUG  TaskList: ## Running create_dir_structure...
12-17 15:04 DEBUG  CommonBackend: Creating dir E:\ubuntu
12-17 15:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
12-17 15:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
12-17 15:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
12-17 15:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
12-17 15:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
12-17 15:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
12-17 15:04 DEBUG  TaskList: ## Finished create_dir_structure
12-17 15:04 DEBUG  TaskList: ## Running uncompress_target_dir...
12-17 15:04 DEBUG  TaskList: ## Finished uncompress_target_dir
12-17 15:04 DEBUG  TaskList: ## Running create_uninstaller...
12-17 15:04 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
12-17 15:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
12-17 15:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
12-17 15:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-17 15:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
12-17 15:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
12-17 15:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-17 15:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
12-17 15:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-17 15:04 DEBUG  TaskList: ## Finished create_uninstaller
12-17 15:04 DEBUG  TaskList: ## Running copy_installation_files...
12-17 15:04 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
12-17 15:04 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\winboot -> E:\ubuntu\winboot
12-17 15:04 DEBUG  WindowsBackend: Copying C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
12-17 15:04 DEBUG  TaskList: ## Finished copy_installation_files
12-17 15:04 DEBUG  TaskList: ## Running get_iso...
12-17 15:04 DEBUG  CommonBackend: Searching for local CD
12-17 15:04 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp is a valid Ubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 15:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 15:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 15:04 DEBUG  CommonBackend: Searching for local ISO
12-17 15:04 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-17 15:04 DEBUG  TaskList: New task get_metalink
12-17 15:04 DEBUG  TaskList: ### Running get_metalink...
12-17 15:04 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink > E:\ubuntu\install
12-17 15:04 DEBUG  downloader: Download start filename=E:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
12-17 15:04 DEBUG  downloader: download finished (read 26651 bytes)
12-17 15:04 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink > E:\ubuntu\install
12-17 15:04 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
12-17 15:04 DEBUG  downloader: download finished (read 562 bytes)
12-17 15:04 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg > E:\ubuntu\install
12-17 15:04 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
12-17 15:04 DEBUG  downloader: download finished (read 189 bytes)
12-17 15:04 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
12-17 15:04 INFO   saplog: Checking block bindings..
12-17 15:04 INFO   saplog: Key verified successfully.
12-17 15:04 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

12-17 15:04 DEBUG  TaskList: ### Finished get_metalink
12-17 15:04 DEBUG  TaskList: New task download
12-17 15:04 DEBUG  TaskList: ### Running download...
12-17 15:04 DEBUG  btdownloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent > E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 15:12 DEBUG  TaskList: ### Finished download
12-17 15:12 DEBUG  TaskList: New task check_iso
12-17 15:12 DEBUG  TaskList: ### Running check_iso...
12-17 15:12 DEBUG  CommonBackend: Checking E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 15:12 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 15:12 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 15:12 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
12-17 15:12 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
12-17 15:12 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 15:12 DEBUG  TaskList: New task get_file_md5
12-17 15:12 DEBUG  TaskList: #### Running get_file_md5...
12-17 15:13 DEBUG  TaskList: #### Finished get_file_md5
12-17 15:13 DEBUG  TaskList: ### Finished check_iso
12-17 15:13 DEBUG  TaskList: ## Finished get_iso
12-17 15:13 DEBUG  TaskList: ## Running extract_kernel...
12-17 15:13 DEBUG  CommonBackend: Extracting files from ISO E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 15:13 DEBUG  WindowsBackend:   extracting md5sum.txt from E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 15:13 DEBUG  WindowsBackend:   extracting casper\vmlinuz from E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 15:13 DEBUG  WindowsBackend:   extracting casper\initrd.lz from E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-17 15:13 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
12-17 15:13 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\vmlinuz
12-17 15:13 DEBUG  CommonBackend:   E:\ubuntu\install\boot\vmlinuz md5 = f2bec09da1b46a21c0e6cc3192ca2e4f == f2bec09da1b46a21c0e6cc3192ca2e4f
12-17 15:13 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\initrd.lz
12-17 15:13 DEBUG  CommonBackend:   E:\ubuntu\install\boot\initrd.lz md5 = e09f7d0e9500f67156730ad6093ce225 == e09f7d0e9500f67156730ad6093ce225
12-17 15:13 DEBUG  TaskList: ## Finished extract_kernel
12-17 15:13 DEBUG  TaskList: ## Running choose_disk_sizes...
12-17 15:13 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
12-17 15:13 DEBUG  TaskList: ## Finished choose_disk_sizes
12-17 15:13 DEBUG  TaskList: ## Running create_preseed...
12-17 15:13 DEBUG  TaskList: ## Finished create_preseed
12-17 15:13 DEBUG  TaskList: ## Running modify_bootloader...
12-17 15:13 DEBUG  TaskList: New task modify_bcd
12-17 15:13 DEBUG  TaskList: ### Running modify_bcd...
12-17 15:13 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 2574.92578125 mb free ntfs)
12-17 15:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6}
12-17 15:13 DEBUG  TaskList: ### Finished modify_bcd
12-17 15:13 DEBUG  TaskList: New task modify_bcd
12-17 15:13 DEBUG  TaskList: ### Running modify_bcd...
12-17 15:13 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 650261.515625 mb free ntfs)
12-17 15:13 DEBUG  WindowsBackend: BCD has already been modified
12-17 15:13 DEBUG  TaskList: ### Finished modify_bcd
12-17 15:13 DEBUG  TaskList: New task modify_bcd
12-17 15:13 DEBUG  TaskList: ### Running modify_bcd...
12-17 15:13 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 30518.1757813 mb free ntfs)
12-17 15:13 DEBUG  WindowsBackend: BCD has already been modified
12-17 15:13 DEBUG  TaskList: ### Finished modify_bcd
12-17 15:13 DEBUG  TaskList: ## Finished modify_bootloader
12-17 15:13 DEBUG  TaskList: ## Running modify_grub_configuration...
12-17 15:13 DEBUG  TaskList: ## Finished modify_grub_configuration
12-17 15:13 DEBUG  TaskList: ## Running create_virtual_disks...
12-17 15:13 DEBUG  Virtualdisk:  Creating virtual disk E:\ubuntu\disks\root.disk of 16744MB
12-17 15:13 DEBUG  Virtualdisk:  Creating virtual disk E:\ubuntu\disks\swap.disk of 256MB
12-17 15:13 DEBUG  TaskList: ## Finished create_virtual_disks
12-17 15:13 DEBUG  TaskList: ## Running uncompress_files...
12-17 15:13 DEBUG  WindowsBackend: compact E:\ubuntu\install\boot /U /A /F
12-17 15:13 DEBUG  WindowsBackend: compact E:\ubuntu\install\boot\*.* /U /A /F
12-17 15:13 DEBUG  TaskList: ## Finished uncompress_files
12-17 15:13 DEBUG  TaskList: ## Running eject_cd...
12-17 15:13 DEBUG  TaskList: ## Finished eject_cd
12-17 15:13 DEBUG  TaskList: # Finished tasklist
12-17 15:13 INFO   root: Almost finished installing
12-17 15:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylA87B.tmp\translations, languages=['en_US', 'en']
12-17 15:13 INFO   root: Finished installation
12-17 15:13 INFO   root: Rebooting
12-17 15:13 DEBUG  TaskList: # Running tasklist...
12-17 15:13 DEBUG  TaskList: ## Running reboot...
12-17 15:13 DEBUG  TaskList: ## Finished reboot
12-17 15:13 DEBUG  TaskList: # Finished tasklist
12-17 15:13 DEBUG  root: application.quit
12-17 15:13 DEBUG  WindowsFrontend: frontend.quit
12-17 15:13 DEBUG  WindowsFrontend: frontend.on_quit
12-17 15:13 DEBUG  root: application.on_quit
12-17 15:13 INFO   root: sys.exit
12-18 18:58 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-18 18:58 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-18 18:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"']
12-18 18:58 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\data
12-18 18:58 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\bin\7z.exe
12-18 18:58 DEBUG  CommonBackend: Fetching basic info...
12-18 18:58 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
12-18 18:58 DEBUG  CommonBackend: platform=win32
12-18 18:58 DEBUG  CommonBackend: osname=nt
12-18 18:58 DEBUG  CommonBackend: language=en_US
12-18 18:58 DEBUG  CommonBackend: encoding=cp1252
12-18 18:58 DEBUG  WindowsBackend: arch=amd64
12-18 18:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\data\isolist.ini
12-18 18:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 18:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 18:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 18:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 18:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 18:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 18:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 18:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 18:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-18 18:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-18 18:58 DEBUG  WindowsBackend: Fetching host info...
12-18 18:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 18:58 DEBUG  WindowsBackend: windows version=vista
12-18 18:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-18 18:58 DEBUG  WindowsBackend: windows_sp=None
12-18 18:58 DEBUG  WindowsBackend: windows_build=7100
12-18 18:58 DEBUG  WindowsBackend: gmt=-5
12-18 18:58 DEBUG  WindowsBackend: country=US
12-18 18:58 DEBUG  WindowsBackend: timezone=America/New_York
12-18 18:58 DEBUG  WindowsBackend: windows_username=JOE
12-18 18:58 DEBUG  WindowsBackend: user_full_name=JOE
12-18 18:58 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-18 18:58 DEBUG  WindowsBackend: windows_language_code=1033
12-18 18:58 DEBUG  WindowsBackend: windows_language=English
12-18 18:58 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-18 18:58 DEBUG  WindowsBackend: bootloader=vista
12-18 18:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 1755.44921875 mb free ntfs)
12-18 18:58 DEBUG  WindowsBackend: drive=Drive(C: hd 1755.44921875 mb free ntfs)
12-18 18:58 DEBUG  WindowsBackend: drive=Drive(E: hd 10256.9179688 mb free ntfs)
12-18 18:58 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
12-18 18:58 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-18 18:58 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
12-18 18:58 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
12-18 18:58 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-18 18:58 DEBUG  WindowsBackend: keyboard_id=67699721
12-18 18:58 DEBUG  WindowsBackend: keyboard_layout=us
12-18 18:58 DEBUG  WindowsBackend: keyboard_variant=
12-18 18:58 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-18 18:58 DEBUG  CommonBackend: locale=en_US.UTF-8
12-18 18:58 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
12-18 18:58 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 18:58 DEBUG  CommonBackend: Searching for local CDs
12-18 18:58 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp is a valid Ubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp is a valid Ubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp is a valid Ubuntu Netbook Remix CD
12-18 18:58 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp is a valid Kubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp is a valid Kubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp is a valid Kubuntu Netbook CD
12-18 18:58 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp is a valid Xubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp is a valid Xubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp is a valid Mythbuntu CD
12-18 18:58 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp is a valid Mythbuntu CD
12-18 18:58 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-18 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-18 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 18:58 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-18 18:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-18 18:58 INFO   Distro: Found a valid CD for Ubuntu: F:\
12-18 18:58 INFO   root: Running the uninstaller...
12-18 18:58 INFO   CommonBackend: This is the uninstaller running
12-18 18:58 DEBUG  WindowsFrontend: __init__...
12-18 18:58 DEBUG  WindowsFrontend: on_init...
12-18 18:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\translations, languages=['en_US', 'en']
12-18 18:58 INFO   root: Received settings
12-18 18:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl86FD.tmp\translations, languages=['en_US', 'en']
12-18 18:58 DEBUG  TaskList: # Running tasklist...
12-18 18:58 DEBUG  TaskList: ## Running Backup ISO...
12-18 18:58 DEBUG  TaskList: ## Finished Backup ISO
12-18 18:58 DEBUG  TaskList: ## Running Remove bootloader entry...
12-18 18:58 DEBUG  WindowsBackend: Removing bcd entry {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6}
12-18 18:58 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
12-18 18:58 DEBUG  TaskList: # Cancelling tasklist
12-18 18:58 DEBUG  TaskList: # Finished tasklist
12-18 18:58 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
12-18 18:59 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-18 18:59 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-18 18:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"']
12-18 18:59 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\data
12-18 18:59 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\bin\7z.exe
12-18 18:59 DEBUG  CommonBackend: Fetching basic info...
12-18 18:59 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
12-18 18:59 DEBUG  CommonBackend: platform=win32
12-18 18:59 DEBUG  CommonBackend: osname=nt
12-18 18:59 DEBUG  CommonBackend: language=en_US
12-18 18:59 DEBUG  CommonBackend: encoding=cp1252
12-18 18:59 DEBUG  WindowsBackend: arch=amd64
12-18 18:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\data\isolist.ini
12-18 18:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 18:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 18:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 18:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 18:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 18:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 18:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 18:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 18:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-18 18:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-18 18:59 DEBUG  WindowsBackend: Fetching host info...
12-18 18:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 18:59 DEBUG  WindowsBackend: windows version=vista
12-18 18:59 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
12-18 18:59 DEBUG  WindowsBackend: windows_sp=None
12-18 18:59 DEBUG  WindowsBackend: windows_build=6000
12-18 18:59 DEBUG  WindowsBackend: gmt=-5
12-18 18:59 DEBUG  WindowsBackend: country=US
12-18 18:59 DEBUG  WindowsBackend: timezone=America/New_York
12-18 18:59 DEBUG  WindowsBackend: windows_username=JOE
12-18 18:59 DEBUG  WindowsBackend: user_full_name=JOE
12-18 18:59 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-18 18:59 DEBUG  WindowsBackend: windows_language_code=1033
12-18 18:59 DEBUG  WindowsBackend: windows_language=English
12-18 18:59 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-18 18:59 DEBUG  WindowsBackend: bootloader=vista
12-18 18:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 1753.015625 mb free ntfs)
12-18 18:59 DEBUG  WindowsBackend: drive=Drive(C: hd 1753.015625 mb free ntfs)
12-18 18:59 DEBUG  WindowsBackend: drive=Drive(E: hd 10256.9179688 mb free ntfs)
12-18 18:59 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
12-18 18:59 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-18 18:59 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
12-18 18:59 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
12-18 18:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-18 18:59 DEBUG  WindowsBackend: keyboard_id=67699721
12-18 18:59 DEBUG  WindowsBackend: keyboard_layout=us
12-18 18:59 DEBUG  WindowsBackend: keyboard_variant=
12-18 18:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-18 18:59 DEBUG  CommonBackend: locale=en_US.UTF-8
12-18 18:59 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
12-18 18:59 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 18:59 DEBUG  CommonBackend: Searching for local CDs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp is a valid Ubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp is a valid Ubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp is a valid Ubuntu Netbook Remix CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp is a valid Kubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp is a valid Kubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp is a valid Kubuntu Netbook CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp is a valid Xubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp is a valid Xubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp is a valid Mythbuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp is a valid Mythbuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 18:59 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-18 18:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-18 18:59 INFO   Distro: Found a valid CD for Ubuntu: F:\
12-18 18:59 INFO   root: Running the uninstaller...
12-18 18:59 INFO   CommonBackend: This is the uninstaller running
12-18 18:59 DEBUG  WindowsFrontend: __init__...
12-18 18:59 DEBUG  WindowsFrontend: on_init...
12-18 18:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\translations, languages=['en_US', 'en']
12-18 18:59 INFO   root: Received settings
12-18 18:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pylFD47.tmp\translations, languages=['en_US', 'en']
12-18 18:59 DEBUG  TaskList: # Running tasklist...
12-18 18:59 DEBUG  TaskList: ## Running Backup ISO...
12-18 18:59 DEBUG  TaskList: ## Finished Backup ISO
12-18 18:59 DEBUG  TaskList: ## Running Remove bootloader entry...
12-18 18:59 DEBUG  WindowsBackend: Removing bcd entry {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6}
12-18 18:59 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
12-18 18:59 DEBUG  TaskList: # Cancelling tasklist
12-18 18:59 DEBUG  TaskList: # Finished tasklist
12-18 18:59 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
12-18 18:59 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-18 18:59 DEBUG  root: Logfile is c:\users\joe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-18 18:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"']
12-18 18:59 DEBUG  CommonBackend: data_dir=C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\data
12-18 18:59 DEBUG  WindowsBackend: 7z=C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\bin\7z.exe
12-18 18:59 DEBUG  CommonBackend: Fetching basic info...
12-18 18:59 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
12-18 18:59 DEBUG  CommonBackend: platform=win32
12-18 18:59 DEBUG  CommonBackend: osname=nt
12-18 18:59 DEBUG  CommonBackend: language=en_US
12-18 18:59 DEBUG  CommonBackend: encoding=cp1252
12-18 18:59 DEBUG  WindowsBackend: arch=amd64
12-18 18:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\data\isolist.ini
12-18 18:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-18 18:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-18 18:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-18 18:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-18 18:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-18 18:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-18 18:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-18 18:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-18 18:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-18 18:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-18 18:59 DEBUG  WindowsBackend: Fetching host info...
12-18 18:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-18 18:59 DEBUG  WindowsBackend: windows version=vista
12-18 18:59 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
12-18 18:59 DEBUG  WindowsBackend: windows_sp=None
12-18 18:59 DEBUG  WindowsBackend: windows_build=6000
12-18 18:59 DEBUG  WindowsBackend: gmt=-5
12-18 18:59 DEBUG  WindowsBackend: country=US
12-18 18:59 DEBUG  WindowsBackend: timezone=America/New_York
12-18 18:59 DEBUG  WindowsBackend: windows_username=JOE
12-18 18:59 DEBUG  WindowsBackend: user_full_name=JOE
12-18 18:59 DEBUG  WindowsBackend: user_directory=C:\Users\JOE
12-18 18:59 DEBUG  WindowsBackend: windows_language_code=1033
12-18 18:59 DEBUG  WindowsBackend: windows_language=English
12-18 18:59 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-18 18:59 DEBUG  WindowsBackend: bootloader=vista
12-18 18:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 1752.9765625 mb free ntfs)
12-18 18:59 DEBUG  WindowsBackend: drive=Drive(C: hd 1752.9765625 mb free ntfs)
12-18 18:59 DEBUG  WindowsBackend: drive=Drive(E: hd 10256.9179688 mb free ntfs)
12-18 18:59 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
12-18 18:59 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-18 18:59 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
12-18 18:59 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
12-18 18:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-18 18:59 DEBUG  WindowsBackend: keyboard_id=67699721
12-18 18:59 DEBUG  WindowsBackend: keyboard_layout=us
12-18 18:59 DEBUG  WindowsBackend: keyboard_variant=
12-18 18:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-18 18:59 DEBUG  CommonBackend: locale=en_US.UTF-8
12-18 18:59 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
12-18 18:59 DEBUG  CommonBackend: Searching ISOs on USB devices
12-18 18:59 DEBUG  CommonBackend: Searching for local CDs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp is a valid Ubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp is a valid Ubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp is a valid Ubuntu Netbook Remix CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp is a valid Kubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp is a valid Kubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp is a valid Kubuntu Netbook CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp is a valid Xubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp is a valid Xubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp is a valid Mythbuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp is a valid Mythbuntu CD
12-18 18:59 DEBUG  Distro:     does not contain C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-18 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-18 18:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-18 18:59 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-18 18:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-18 18:59 INFO   Distro: Found a valid CD for Ubuntu: F:\
12-18 18:59 INFO   root: Running the uninstaller...
12-18 18:59 INFO   CommonBackend: This is the uninstaller running
12-18 18:59 DEBUG  WindowsFrontend: __init__...
12-18 18:59 DEBUG  WindowsFrontend: on_init...
12-18 18:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\translations, languages=['en_US', 'en']
12-18 18:59 INFO   root: Received settings
12-18 18:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOE\AppData\Local\Temp\pyl6B04.tmp\translations, languages=['en_US', 'en']
12-18 18:59 DEBUG  TaskList: # Running tasklist...
12-18 18:59 DEBUG  TaskList: ## Running Backup ISO...
12-18 18:59 DEBUG  TaskList: ## Finished Backup ISO
12-18 18:59 DEBUG  TaskList: ## Running Remove bootloader entry...
12-18 18:59 DEBUG  WindowsBackend: Removing bcd entry {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6}
12-18 18:59 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
12-18 18:59 DEBUG  TaskList: # Cancelling tasklist
12-18 18:59 DEBUG  TaskList: # Finished tasklist
12-18 18:59 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {a13c9ec7-8c15-11de-acfe-d38a66c0a5d6} /f
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
```


Any Thoughts?

---

### Post by darkod on 2009-12-18
Win7 with its usual problems not allowing to delete the ubuntu entry from windows bootloader. Not sure if this can help, I think they still don't have procedure for win7 included:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

That is just to remove the ubuntu entry from the win7 bootloader, even if it stays there for now, no big deal.
But the ubuntu folder should be gone from the partition where you installed wubi now.

---

### Post by jremlap on 2009-12-18
Okay, a couple of things. I removed everything I could that was listed (registry entry, folders on drive) but there is no Boot.Ini on C:. I restarted, and recevied this when trying to boot Ubuntu:
[IMG]http://img.photobucket.com/albums/v616/Stryker_8/img_3100.jpg[/IMG]

I went into the installer, and quit, and then it took me straight to Ubuntu, but I think it is running off the CD right now, as it will not allow me to open the drive. Are you familiar with this error?

Also, I ran a disk check from the CD, no errors detected. Same with your instructions above to run the disk check. I am at my wits end, and I am considering re-formatting the windows drive and the 1TB where i tried installing ubuntu; and then trying the install that way. Do you think that would rectify this situation?

---

### Post by darkod on 2009-12-18
The windows drive is probably fine, but it does look like you have a messed up ubuntu installation. Leave the 1TB as first boot choice, but boot with the ubuntu cd and select Install Ubuntu and at step 4 just tell it to use the whole 1TB drive. Note whether the drive is still called /dev/sdb. In the last screen, just before clicking Install, click on Advanced and check if grub will be installed on the same drive because you want it on the 1TB drive too.

---

### Post by jremlap on 2009-12-18
I have gotten completely fed up with microsoft doing their usual... Holding me back from using my PC to it's fullest and being operated...instead of an operator. I hate you microsoft and I hope bill gates himself gets to hear that.


Okay, enough ranting. I have deleted the partitions from the previous attempt on the 1TB Drive, and formatted the 200GB that had once housed windows 7. I attempted to run the Kbuntu 64-bit CD, and it gives me a ton of Kernal errors again? I am lost as to why this is. Anywho. I swapped the 1TB Drive to the first SATA postion where i am not supposed to plug in the drive running the OS. I am attempting to install Ubuntu 32-bit as we speak. My biggest concern is that the other 200GB does not get touched as this is where all my files are backed up at. I am trying to use the 1TB for storage only, so I want the install to run off the other 200GB drive (just so you know the method to my maddness ; ). 

For some reason, I cannot see the 1TB drive at all right now in Ubuntu's drive manager, I had planned to format it from within Ubuntu as well.

I will let you know how this one goes, should only be another 5-10 minutes. Also so you are aware I did use advanced settings to make sure the GRUB (I am assuming this is what it refers to as the boot loader in the install, as it never actually physically references GRUB) was being placed on the same 200 GB drive. 

Thank you again Darko for all of your help on this today, I will let you know if this works!

---

### Post by darkod on 2009-12-18
OK, hope it works. Just to add, could it be possible that that Kubuntu 64bit CD is bad? Maybe ISO corrupted during download, maybe badly burnt cd, etc.

---

### Post by jremlap on 2009-12-18
Well, I am at a loss. This issue has happened with the Kubuntu installation no matter how i run it. I have tried 2 CD's. At this point, I am just trying to get the 32 bit version of ubuntu to install. I have installed as listed above, and still, I am getting the same screen as the last screenshot I posted listing "bad page state in process Khelper...". 

My last attempt to make this work, here is my plan, let me know what you think:

I am going to unplug the 200GB that has my files stored on it, to make sure there is no room for error in formatting the wrong disk. Then, (which I will need your help on this part) I will format both of the drives using the ubuntu CD. I am going to attempt to use the 64-Bit Kubuntu CD to do so, as this is the version I would REALLY like to install. We'll see if that works. 

While I am unplugging the other drive, my question is this (if you think this is a good route to go with that is): How would I go about formatting the drives from the Kubuntu install menu? Is this even possible? And if so, what format is the best to use?

Thank you again!

-JoE

---

### Post by darkod on 2009-12-18
Well, if I understood you correctly, it's very easy to format a drive and install on it. You are right, disconnect your data drive just to be on the safe side.
Then there are two options:
1. You could just boot again with the Ubuntu/Kubuntu cd, select Install Ubuntu, and at step 4 use the Erase and use the entire disk option (look at attachment). Note that that option is not selected on this picture, it's just an example and you can see the option there. When you select that option it will activate the drop down list to select the drive you want erased and Ubuntu installed on it. This option will erase the whole drive which is the same as formatting it in advance.
2. If you still want to format the drive in advance, select Try Ubuntu when booting the cd and open Gparted (in System-Administration). That is excellent partition manager. Top right, select the drive. It will list and show all partitions on it. If in the list any partition has padlock (keys) symbol that means it's mounted and you can't delete it like that. Use right-click and Unmount or for swap Swapoff. The padlock should be gone. Then just delete all partitions one by one. You will see at the bottom that Gparted is only scheduling the operations, it will not execute them right away (to prevent destroying data with one wrong click). When you have deleted all partitions click the big green tick mark button in Gparted toolbar. That will execute all operations. After that do the same as in number 1 above.

That will definitely wipe your drive. I'm talking about the drive you want kubuntu on (200GB), don't worry about the 1TB right now. Once you have kubuntu running again you can open Gparted (this time hopefully from your hdd installation) and do as above to delete the 1TB drive.
You are burning the install CDs at low speed right? Not more than 8x, even better 4x. Because these days CD speed goes up to 50x some people think half of that is "slow". For OS install CD you really need to burn it slow to make sure you minimize errors.
I think you said you already used two CDs. Were they created from same ISO image? What if it was corrupted during download?

---

### Post by jremlap on 2009-12-18
Well, I think i inadvertantly lost my backup, but I can finally say that ubuntu is running on my hard drive. I removed the secondary video card, switched out of SLI mode, and unplugged all but the 1TB drive. How and or why this worked, I have no idea. I am going to systematically plug everything back in and see what causes a failure (I am hoping that nothing will, after all of this) I am hoping that the end result of this will be helping someone with the same issue to get it corrected. Thank you SOOOOOO much for all of your time and expertise today Darko. I will let you know as soon as I have figured out what the trigger was. I am going to start by re-installing the SLI video card as I have a feeling this is what my problem was this whole time. Thanks again my friend!

-JoE

---

### Post by jremlap on 2009-12-18
Well, that certainly was the problem. I am now running Kubuntu 64-Bit with no problems... Minus a video card that is. The more I thought about it, I recall having a very difficult time configuring windows XP to use the 2 video cards in SLI with different amounts of RAM. While it was possible it took quite some time. I am dissapointed with the way the Linux based system reacted to it with seemingly no work around absent removing one of the cards, but I am perfectly happy with a 1GB 9600GS and NO MICROSOFT! 

Solution at this point for those of you running into similar issues would be to suck it up and pull the additional card. I would LOVE to hear if anyone has found a way to pull this off, but until then, this works just fine. 

Thanks again Darko!

-JoE

---

