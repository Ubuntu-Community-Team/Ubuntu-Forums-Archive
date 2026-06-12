---
title: "Stuck while installing Wubi"
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by Shurakai2000 on 2011-11-26
Hi all,

While following the instructions for installing Wubi, I have hit a problem and I can't work out what to do next.

I have downloaded the file and started the install. Then it asks to reboot the computer. I do that and select ubuntu from the OS selection screen. Then it more or less stops with this message.


> Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules: ls /dev)
ALERT! /dev/disk/by-uuid/df61-4f83 does not exist. Dropping to a shell!


BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _I'm a little lost with this message. I'm guessing that something is missing but I don't understand what or how I might go about fixing it.

Are there some logs somewhere that I should look at to get more information about what the problem is?


The PC: I'm attempting to install ubuntu on a Fujitsu notebook. The computer is a Japanese hardware version running English windows XP. There is about 10GB of free space left, 8 of which is used for this installation.

Me: This is my first time trying out ubuntu. I haven't used linux in about 10 years but before that I was a RedHat Linux administrator for 6 years.


Any help much appreciated.
Thanks
steve

---

### Post by Rubi1200 on 2011-11-26
Hi and welcome to the forums :)

You need to boot the computer with a LiveCD/USB and post the results of the boot info script so we can see what is going on.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by Shurakai2000 on 2011-11-26
Thanks for the response.

I take it that this liveCD/USB is another installation of ubuntu that I need to find, download and install.

Where can I download it from?


steve

---

### Post by Shurakai2000 on 2011-11-27
OK, I' figured out how to run a liveUSB install and then run the script. Here is the results.

Hope this helps.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 61492 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb1/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    15,794,175    15,794,113   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   234,436,544   234,436,482   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       d9eb6c23-1adf-3548-9664-da45acf5bf58   ext2       casper-rw
/dev/sda1        17F6-2459                              vfat       PENDRIVE
/dev/sdb1        CF61-4F83                              vfat       SYSTEM

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
 
--------------------------------------------------------------------------------

============================= sdb1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
--------------------------------------------------------------------------------

================= sdb1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/initrd.img-3.0.0-12-generic              40
               =                boot/vmlinuz-3.0.0-12-generic                 20
               =                vmlinuz                                       20

=============================== StdErr Messages: ===============================

./boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```


Thanks for helping
Steve

---

### Post by Rubi1200 on 2011-11-28
It looks like your fstab file was not configured or not configured properly. This is most likely the reason for the error.

Do the following from a LiveCD/USB again:
```

sudo mkdir /media/win  
sudo mount /dev/sdb1 /media/win 
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```
Once mounted, post the output of this command:

```
cat /etc/fstab
```

---

### Post by Shurakai2000 on 2011-11-28
Hi Rubi,

Thanks for helping.

I tried mounting the root.disk (third command) but it said no such file or directory.

So I had a look in /media/win and there was no ubuntu directory. I'm guessing this is bad.

Here is a listing of /media/win.
```
drwxr-xr-x 11 root root       2048 1970-01-01 00:00 .
drwxr-xr-x  1 root root       4096 2011-11-29 04:09 ..
-rwxr-xr-x  1 root root        143 2011-10-13 02:15 autorun.inf
drwxr-xr-x  3 root root       2048 2011-10-13 02:15 boot
drwxr-xr-x  2 root root       2048 2011-10-13 02:15 casper
-rwxr-xr-x  1 root root 4287627264 2011-11-29 04:23 casper-rw
drwxr-xr-x  2 root root       2048 2011-10-13 02:15 .disk
drwxr-xr-x  3 root root       2048 2011-10-13 02:15 dists
drwxr-xr-x  2 root root       2048 2011-10-13 02:15 install
-r-xr-xr-x  1 root root      32256 2011-11-27 16:27 ldlinux.sys
-rwxr-xr-x  1 root root       4418 2011-10-13 02:15 md5sum.txt
drwxr-xr-x  2 root root       2048 2011-10-13 02:15 pics
drwxr-xr-x  4 root root       2048 2011-10-13 02:15 pool
drwxr-xr-x  2 root root       2048 2011-10-13 02:15 preseed
-rwxr-xr-x  1 root root        225 2011-10-13 02:15 README.diskdefines
drwxr-xr-x  2 root root       6144 2011-10-13 02:15 syslinux
-rwxr-xr-x  1 root root      48961 2011-05-02 01:57 Uni-USB-Installer-Copying.txt
-rwxr-xr-x  1 root root       8633 2011-11-24 05:37 Uni-USB-Installer-Readme.txt
-rwxr-xr-x  1 root root    2491552 2011-10-13 02:15 wubi.exe
```

---

### Post by bcbc on 2011-11-29
Please post the log file: %TEMP%\wubi-11.10-rev245.log

You shouldn't have been able to install successfully on a VFAT partition due to this bug: [lpbug]882393[/lpbug]

---

### Post by Shurakai2000 on 2011-11-29
Just had a look at the bug and that sounds like my problem. Next question is how do I go about working around it or is it just not possible with a vfat file system.

Also the wubi-11.10-rev245.log, is it found on Windows or a liveUSB ubuntu? I can't seem to find it in either install. Although I'm a little confused with %TEMP% directory.

I'll keep looking for it though.


Thanks for the help all.
steve

---

### Post by Shurakai2000 on 2011-11-29
Found the log location. Here it is.

```
11-25 19:16 INFO   root: === wubi 11.10 rev245 ===
11-25 19:16 DEBUG  root: Logfile is c:\docume~1\stephe~1\locals~1\temp\wubi-11.10-rev245.log
11-25 19:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Stephen Parker\\My Documents\\Downloads\\wubi.exe"']
11-25 19:16 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\data
11-25 19:16 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\bin\7z.exe
11-25 19:16 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
11-25 19:16 DEBUG  CommonBackend: Fetching basic info...
11-25 19:16 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Stephen Parker\My Documents\Downloads\wubi.exe
11-25 19:16 DEBUG  CommonBackend: platform=win32
11-25 19:16 DEBUG  CommonBackend: osname=nt
11-25 19:16 DEBUG  CommonBackend: language=en_AU
11-25 19:16 DEBUG  CommonBackend: encoding=cp1252
11-25 19:16 DEBUG  WindowsBackend: arch=amd64
11-25 19:16 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\data\isolist.ini
11-25 19:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 19:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 19:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 19:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 19:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 19:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 19:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 19:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 19:16 DEBUG  WindowsBackend: Fetching host info...
11-25 19:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 19:16 DEBUG  WindowsBackend: windows version=xp
11-25 19:16 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-25 19:16 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-25 19:16 DEBUG  WindowsBackend: windows_build=2600
11-25 19:16 DEBUG  WindowsBackend: gmt=10
11-25 19:16 DEBUG  WindowsBackend: country=AU
11-25 19:16 DEBUG  WindowsBackend: timezone=Australia/Sydney
11-25 19:16 DEBUG  WindowsBackend: windows_username=Stephen Parker
11-25 19:16 DEBUG  WindowsBackend: user_full_name=Stephen Parker
11-25 19:16 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Stephen Parker
11-25 19:16 DEBUG  WindowsBackend: windows_language_code=1033
11-25 19:16 DEBUG  WindowsBackend: windows_language=English
11-25 19:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     L7100  @ 1.20GHz
11-25 19:16 DEBUG  WindowsBackend: bootloader=xp
11-25 19:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9415.8125 mb free fat32)
11-25 19:16 DEBUG  WindowsBackend: drive=Drive(C: hd 9415.8125 mb free fat32)
11-25 19:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-25 19:16 DEBUG  WindowsBackend: uninstaller_path=None
11-25 19:16 DEBUG  WindowsBackend: previous_target_dir=None
11-25 19:16 DEBUG  WindowsBackend: previous_distro_name=None
11-25 19:16 DEBUG  WindowsBackend: keyboard_id=-536804335
11-25 19:16 DEBUG  WindowsBackend: keyboard_layout=jp
11-25 19:16 DEBUG  WindowsBackend: keyboard_variant=
11-25 19:16 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
11-25 19:16 DEBUG  CommonBackend: locale=en_AU.UTF-8
11-25 19:16 DEBUG  WindowsBackend: total_memory_mb=2038.3515625
11-25 19:16 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 19:16 DEBUG  CommonBackend: Searching for local CDs
11-25 19:16 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp is a valid Ubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp is a valid Ubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp is a valid Kubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp is a valid Kubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp is a valid Xubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp is a valid Xubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp is a valid Mythbuntu CD
11-25 19:16 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp is a valid Mythbuntu CD
11-25 19:16 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 19:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 19:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 19:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:16 INFO   root: Running the installer...
11-25 19:16 DEBUG  WindowsFrontend: __init__...
11-25 19:16 DEBUG  WindowsFrontend: on_init...
11-25 19:16 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\translations, languages=['en_AU', 'en']
11-25 19:16 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC2.tmp\translations, languages=['en_AU', 'en']
11-25 19:16 INFO   WindowsFrontend: Operation cancelled
11-25 19:16 DEBUG  WindowsFrontend: frontend.quit
11-25 19:16 DEBUG  WindowsFrontend: frontend.on_quit
11-25 19:16 DEBUG  root: application.on_quit
11-25 19:16 INFO   root: sys.exit
11-25 19:17 INFO   root: === wubi 11.10 rev245 ===
11-25 19:17 DEBUG  root: Logfile is c:\docume~1\stephe~1\locals~1\temp\wubi-11.10-rev245.log
11-25 19:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Stephen Parker\\My Documents\\Downloads\\wubi.exe"']
11-25 19:17 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\data
11-25 19:17 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\bin\7z.exe
11-25 19:17 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
11-25 19:17 DEBUG  CommonBackend: Fetching basic info...
11-25 19:17 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Stephen Parker\My Documents\Downloads\wubi.exe
11-25 19:17 DEBUG  CommonBackend: platform=win32
11-25 19:17 DEBUG  CommonBackend: osname=nt
11-25 19:17 DEBUG  CommonBackend: language=en_AU
11-25 19:17 DEBUG  CommonBackend: encoding=cp1252
11-25 19:17 DEBUG  WindowsBackend: arch=amd64
11-25 19:17 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\data\isolist.ini
11-25 19:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 19:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 19:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 19:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 19:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 19:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 19:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 19:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 19:17 DEBUG  WindowsBackend: Fetching host info...
11-25 19:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 19:17 DEBUG  WindowsBackend: windows version=xp
11-25 19:17 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-25 19:17 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-25 19:17 DEBUG  WindowsBackend: windows_build=2600
11-25 19:17 DEBUG  WindowsBackend: gmt=10
11-25 19:17 DEBUG  WindowsBackend: country=AU
11-25 19:17 DEBUG  WindowsBackend: timezone=Australia/Sydney
11-25 19:17 DEBUG  WindowsBackend: windows_username=Stephen Parker
11-25 19:17 DEBUG  WindowsBackend: user_full_name=Stephen Parker
11-25 19:17 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Stephen Parker
11-25 19:17 DEBUG  WindowsBackend: windows_language_code=1033
11-25 19:17 DEBUG  WindowsBackend: windows_language=English
11-25 19:17 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     L7100  @ 1.20GHz
11-25 19:17 DEBUG  WindowsBackend: bootloader=xp
11-25 19:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 10945.40625 mb free fat32)
11-25 19:17 DEBUG  WindowsBackend: drive=Drive(C: hd 10945.40625 mb free fat32)
11-25 19:17 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-25 19:17 DEBUG  WindowsBackend: uninstaller_path=None
11-25 19:17 DEBUG  WindowsBackend: previous_target_dir=None
11-25 19:17 DEBUG  WindowsBackend: previous_distro_name=None
11-25 19:17 DEBUG  WindowsBackend: keyboard_id=-536804335
11-25 19:17 DEBUG  WindowsBackend: keyboard_layout=jp
11-25 19:17 DEBUG  WindowsBackend: keyboard_variant=
11-25 19:17 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
11-25 19:17 DEBUG  CommonBackend: locale=en_AU.UTF-8
11-25 19:17 DEBUG  WindowsBackend: total_memory_mb=2038.3515625
11-25 19:17 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 19:17 DEBUG  CommonBackend: Searching for local CDs
11-25 19:17 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp is a valid Ubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp is a valid Ubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp is a valid Kubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp is a valid Kubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp is a valid Xubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp is a valid Xubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp is a valid Mythbuntu CD
11-25 19:17 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp is a valid Mythbuntu CD
11-25 19:17 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:17 INFO   root: Running the installer...
11-25 19:17 DEBUG  WindowsFrontend: __init__...
11-25 19:17 DEBUG  WindowsFrontend: on_init...
11-25 19:17 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\translations, languages=['en_AU', 'en']
11-25 19:17 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\translations, languages=['en_AU', 'en']
11-25 19:17 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=7000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=stephenparker
11-25 19:17 INFO   root: Received settings
11-25 19:17 DEBUG  CommonBackend: Searching for local CD
11-25 19:17 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp is a valid Ubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
11-25 19:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:17 DEBUG  CommonBackend: Searching for local ISO
11-25 19:17 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC3.tmp\translations, languages=['en_US', 'en']
11-25 19:17 DEBUG  TaskList: # Running tasklist...
11-25 19:17 DEBUG  TaskList: ## Running select_target_dir...
11-25 19:17 INFO   WindowsBackend: Installing into C:\ubuntu
11-25 19:17 DEBUG  TaskList: ## Finished select_target_dir
11-25 19:17 DEBUG  TaskList: ## Running create_dir_structure...
11-25 19:17 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-25 19:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-25 19:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-25 19:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-25 19:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-25 19:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-25 19:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-25 19:17 DEBUG  TaskList: ## Finished create_dir_structure
11-25 19:17 DEBUG  TaskList: ## Running create_uninstaller...
11-25 19:17 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Stephen Parker\My Documents\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-25 19:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-25 19:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-25 19:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-25 19:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-25 19:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-25 19:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-25 19:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
11-25 19:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-25 19:17 DEBUG  TaskList: ## Finished create_uninstaller
11-25 19:17 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-25 19:17 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-25 19:17 DEBUG  TaskList: ## Running get_diskimage...
11-25 19:17 DEBUG  TaskList: New task download
11-25 19:17 DEBUG  TaskList: ### Running download...
11-25 19:17 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-25 19:17 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-25 19:33 DEBUG  WindowsFrontend: frontend.on_quit
11-25 19:33 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
11-25 19:33 DEBUG  TaskList: # Cancelling tasklist
11-25 19:33 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
11-25 19:33 DEBUG  root: application.on_quit
11-25 19:33 DEBUG  root: Forceful exit
11-25 19:33 INFO   root: sys.exit
11-25 19:34 INFO   root: === wubi 11.10 rev245 ===
11-25 19:34 DEBUG  root: Logfile is c:\docume~1\stephe~1\locals~1\temp\wubi-11.10-rev245.log
11-25 19:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Stephen Parker\\My Documents\\Downloads\\wubi.exe"']
11-25 19:34 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\data
11-25 19:34 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\bin\7z.exe
11-25 19:34 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
11-25 19:34 DEBUG  CommonBackend: Fetching basic info...
11-25 19:34 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Stephen Parker\My Documents\Downloads\wubi.exe
11-25 19:34 DEBUG  CommonBackend: platform=win32
11-25 19:34 DEBUG  CommonBackend: osname=nt
11-25 19:34 DEBUG  CommonBackend: language=en_AU
11-25 19:34 DEBUG  CommonBackend: encoding=cp1252
11-25 19:34 DEBUG  WindowsBackend: arch=amd64
11-25 19:34 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\data\isolist.ini
11-25 19:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 19:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 19:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 19:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 19:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 19:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 19:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 19:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 19:34 DEBUG  WindowsBackend: Fetching host info...
11-25 19:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 19:34 DEBUG  WindowsBackend: windows version=xp
11-25 19:34 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-25 19:34 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-25 19:34 DEBUG  WindowsBackend: windows_build=2600
11-25 19:34 DEBUG  WindowsBackend: gmt=10
11-25 19:34 DEBUG  WindowsBackend: country=AU
11-25 19:34 DEBUG  WindowsBackend: timezone=Australia/Sydney
11-25 19:34 DEBUG  WindowsBackend: windows_username=Stephen Parker
11-25 19:34 DEBUG  WindowsBackend: user_full_name=Stephen Parker
11-25 19:34 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Stephen Parker
11-25 19:34 DEBUG  WindowsBackend: windows_language_code=1033
11-25 19:34 DEBUG  WindowsBackend: windows_language=English
11-25 19:34 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     L7100  @ 1.20GHz
11-25 19:34 DEBUG  WindowsBackend: bootloader=xp
11-25 19:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 10672.125 mb free fat32)
11-25 19:34 DEBUG  WindowsBackend: drive=Drive(C: hd 10672.125 mb free fat32)
11-25 19:34 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-25 19:34 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-25 19:34 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-25 19:34 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-25 19:34 DEBUG  WindowsBackend: keyboard_id=-536804335
11-25 19:34 DEBUG  WindowsBackend: keyboard_layout=jp
11-25 19:34 DEBUG  WindowsBackend: keyboard_variant=
11-25 19:34 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
11-25 19:34 DEBUG  CommonBackend: locale=en_AU.UTF-8
11-25 19:34 DEBUG  WindowsBackend: total_memory_mb=2038.3515625
11-25 19:34 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 19:34 DEBUG  CommonBackend: Searching for local CDs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Ubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Ubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Kubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Kubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Xubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Xubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Mythbuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Mythbuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 INFO   root: Already installed, running the uninstaller...
11-25 19:34 INFO   root: Running the uninstaller...
11-25 19:34 INFO   CommonBackend: This is the uninstaller running
11-25 19:34 DEBUG  WindowsFrontend: __init__...
11-25 19:34 DEBUG  WindowsFrontend: on_init...
11-25 19:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\translations, languages=['en_AU', 'en']
11-25 19:34 INFO   root: Received settings
11-25 19:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\translations, languages=['en_AU', 'en']
11-25 19:34 DEBUG  TaskList: # Running tasklist...
11-25 19:34 DEBUG  TaskList: ## Running Remove bootloader entry...
11-25 19:34 ERROR  WindowsBackend: Cannot find bcdedit
11-25 19:34 DEBUG  WindowsBackend: undo_bootini C:
11-25 19:34 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 10672.125 mb free fat32)
11-25 19:34 DEBUG  TaskList: ## Finished Remove bootloader entry
11-25 19:34 DEBUG  TaskList: ## Running Remove target dir...
11-25 19:34 DEBUG  CommonBackend: Deleting C:\ubuntu
11-25 19:34 DEBUG  TaskList: ## Finished Remove target dir
11-25 19:34 DEBUG  TaskList: ## Running Remove registry key...
11-25 19:34 DEBUG  TaskList: ## Finished Remove registry key
11-25 19:34 DEBUG  TaskList: # Finished tasklist
11-25 19:34 INFO   root: Almost finished uninstalling
11-25 19:34 INFO   root: Finished uninstallation
11-25 19:34 DEBUG  CommonBackend: Fetching basic info...
11-25 19:34 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Stephen Parker\My Documents\Downloads\wubi.exe
11-25 19:34 DEBUG  CommonBackend: platform=win32
11-25 19:34 DEBUG  CommonBackend: osname=nt
11-25 19:34 DEBUG  WindowsBackend: arch=amd64
11-25 19:34 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\data\isolist.ini
11-25 19:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 19:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 19:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 19:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 19:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 19:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 19:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 19:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 19:34 DEBUG  WindowsBackend: Fetching host info...
11-25 19:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 19:34 DEBUG  WindowsBackend: windows version=xp
11-25 19:34 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-25 19:34 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-25 19:34 DEBUG  WindowsBackend: windows_build=2600
11-25 19:34 DEBUG  WindowsBackend: gmt=10
11-25 19:34 DEBUG  WindowsBackend: country=AU
11-25 19:34 DEBUG  WindowsBackend: timezone=Australia/Sydney
11-25 19:34 DEBUG  WindowsBackend: windows_username=Stephen Parker
11-25 19:34 DEBUG  WindowsBackend: user_full_name=Stephen Parker
11-25 19:34 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Stephen Parker
11-25 19:34 DEBUG  WindowsBackend: windows_language_code=1033
11-25 19:34 DEBUG  WindowsBackend: windows_language=English
11-25 19:34 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     L7100  @ 1.20GHz
11-25 19:34 DEBUG  WindowsBackend: bootloader=xp
11-25 19:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 10944.96875 mb free fat32)
11-25 19:34 DEBUG  WindowsBackend: drive=Drive(C: hd 10944.96875 mb free fat32)
11-25 19:34 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-25 19:34 DEBUG  WindowsBackend: uninstaller_path=None
11-25 19:34 DEBUG  WindowsBackend: previous_target_dir=None
11-25 19:34 DEBUG  WindowsBackend: previous_distro_name=None
11-25 19:34 DEBUG  WindowsBackend: keyboard_id=-536804335
11-25 19:34 DEBUG  WindowsBackend: keyboard_layout=jp
11-25 19:34 DEBUG  WindowsBackend: keyboard_variant=
11-25 19:34 DEBUG  WindowsBackend: total_memory_mb=2038.3515625
11-25 19:34 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 19:34 DEBUG  CommonBackend: Searching for local CDs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Ubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Ubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Kubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Kubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Xubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Xubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Mythbuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Mythbuntu CD
11-25 19:34 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 19:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:34 INFO   root: Running the installer...
11-25 19:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\translations, languages=['en_AU', 'en']
11-25 19:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\translations, languages=['en_AU', 'en']
11-25 19:35 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=8000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=stephenparker
11-25 19:35 INFO   root: Received settings
11-25 19:35 DEBUG  CommonBackend: Searching for local CD
11-25 19:35 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp is a valid Ubuntu CD
11-25 19:35 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\casper\filesystem.squashfs
11-25 19:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 19:35 DEBUG  CommonBackend: Searching for local ISO
11-25 19:35 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\translations, languages=['en_US', 'en']
11-25 19:35 DEBUG  TaskList: # Running tasklist...
11-25 19:35 DEBUG  TaskList: ## Running select_target_dir...
11-25 19:35 INFO   WindowsBackend: Installing into C:\ubuntu
11-25 19:35 DEBUG  TaskList: ## Finished select_target_dir
11-25 19:35 DEBUG  TaskList: ## Running create_dir_structure...
11-25 19:35 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-25 19:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-25 19:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-25 19:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-25 19:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-25 19:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-25 19:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-25 19:35 DEBUG  TaskList: ## Finished create_dir_structure
11-25 19:35 DEBUG  TaskList: ## Running create_uninstaller...
11-25 19:35 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Stephen Parker\My Documents\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-25 19:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-25 19:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-25 19:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-25 19:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-25 19:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-25 19:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-25 19:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
11-25 19:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-25 19:35 DEBUG  TaskList: ## Finished create_uninstaller
11-25 19:35 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-25 19:35 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-25 19:35 DEBUG  TaskList: ## Running get_diskimage...
11-25 19:35 DEBUG  TaskList: New task download
11-25 19:35 DEBUG  TaskList: ### Running download...
11-25 19:35 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-25 19:35 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-25 20:03 DEBUG  TaskList: ### Finished download
11-25 20:03 DEBUG  downloader: download finished (read 507143012 bytes)
11-25 20:03 DEBUG  TaskList: ## Finished get_diskimage
11-25 20:03 DEBUG  TaskList: ## Running extract_diskimage...
11-25 20:06 DEBUG  TaskList: ## Finished extract_diskimage
11-25 20:06 DEBUG  TaskList: ## Running choose_disk_sizes...
11-25 20:06 DEBUG  WindowsBackend: total size=8000
  root=3744
  swap=256
  home=0
  usr=4000
11-25 20:06 DEBUG  TaskList: ## Finished choose_disk_sizes
11-25 20:06 DEBUG  TaskList: ## Running expand_diskimage...
11-25 20:07 DEBUG  TaskList: ## Finished expand_diskimage
11-25 20:07 DEBUG  TaskList: ## Running create_swap_diskimage...
11-25 20:07 DEBUG  TaskList: ## Finished create_swap_diskimage
11-25 20:07 DEBUG  TaskList: ## Running modify_bootloader...
11-25 20:07 DEBUG  TaskList: New task modify_bootini
11-25 20:07 DEBUG  TaskList: ### Running modify_bootini...
11-25 20:07 DEBUG  WindowsBackend: modify_bootini C:
11-25 20:07 DEBUG  TaskList: ### Finished modify_bootini
11-25 20:07 DEBUG  TaskList: ## Finished modify_bootloader
11-25 20:07 DEBUG  TaskList: ## Running diskimage_bootloader...
11-25 20:07 DEBUG  WindowsBackend: Copying C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\winboot -> C:\ubuntu\winboot
11-25 20:07 DEBUG  TaskList: ## Finished diskimage_bootloader
11-25 20:07 DEBUG  TaskList: # Finished tasklist
11-25 20:07 INFO   root: Almost finished installing
11-25 20:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pylC4.tmp\translations, languages=['en_US', 'en']
11-25 20:20 INFO   root: Finished installation
11-25 20:20 INFO   root: Rebooting
11-25 20:20 DEBUG  TaskList: # Running tasklist...
11-25 20:20 DEBUG  TaskList: ## Running reboot...
11-25 20:20 DEBUG  TaskList: ## Finished reboot
11-25 20:20 DEBUG  TaskList: # Finished tasklist
11-25 20:20 DEBUG  root: application.quit
11-25 20:20 DEBUG  WindowsFrontend: frontend.quit
11-25 20:20 DEBUG  WindowsFrontend: frontend.on_quit
11-25 20:20 DEBUG  root: application.on_quit
11-25 20:20 INFO   root: sys.exit
11-25 20:36 INFO   root: === wubi 11.10 rev245 ===
11-25 20:36 DEBUG  root: Logfile is c:\docume~1\stephe~1\locals~1\temp\wubi-11.10-rev245.log
11-25 20:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Stephen Parker\\My Documents\\Downloads\\wubi.exe"']
11-25 20:36 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\data
11-25 20:36 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\bin\7z.exe
11-25 20:36 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
11-25 20:36 DEBUG  CommonBackend: Fetching basic info...
11-25 20:36 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Stephen Parker\My Documents\Downloads\wubi.exe
11-25 20:36 DEBUG  CommonBackend: platform=win32
11-25 20:36 DEBUG  CommonBackend: osname=nt
11-25 20:36 DEBUG  CommonBackend: language=en_AU
11-25 20:36 DEBUG  CommonBackend: encoding=cp1252
11-25 20:36 DEBUG  WindowsBackend: arch=amd64
11-25 20:36 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\data\isolist.ini
11-25 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 20:36 DEBUG  WindowsBackend: Fetching host info...
11-25 20:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 20:36 DEBUG  WindowsBackend: windows version=xp
11-25 20:36 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-25 20:36 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-25 20:36 DEBUG  WindowsBackend: windows_build=2600
11-25 20:36 DEBUG  WindowsBackend: gmt=10
11-25 20:36 DEBUG  WindowsBackend: country=AU
11-25 20:36 DEBUG  WindowsBackend: timezone=Australia/Sydney
11-25 20:36 DEBUG  WindowsBackend: windows_username=Stephen Parker
11-25 20:36 DEBUG  WindowsBackend: user_full_name=Stephen Parker
11-25 20:36 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Stephen Parker
11-25 20:36 DEBUG  WindowsBackend: windows_language_code=1033
11-25 20:36 DEBUG  WindowsBackend: windows_language=English
11-25 20:36 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     L7100  @ 1.20GHz
11-25 20:36 DEBUG  WindowsBackend: bootloader=xp
11-25 20:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6941.0 mb free fat32)
11-25 20:36 DEBUG  WindowsBackend: drive=Drive(C: hd 6941.0 mb free fat32)
11-25 20:36 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-25 20:36 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-25 20:36 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-25 20:36 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-25 20:36 DEBUG  WindowsBackend: keyboard_id=-536804335
11-25 20:36 DEBUG  WindowsBackend: keyboard_layout=jp
11-25 20:36 DEBUG  WindowsBackend: keyboard_variant=
11-25 20:36 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
11-25 20:36 DEBUG  CommonBackend: locale=en_AU.UTF-8
11-25 20:36 DEBUG  WindowsBackend: total_memory_mb=2038.3515625
11-25 20:36 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 20:36 DEBUG  CommonBackend: Searching for local CDs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 INFO   root: Already installed, running the uninstaller...
11-25 20:36 INFO   root: Running the uninstaller...
11-25 20:36 INFO   CommonBackend: This is the uninstaller running
11-25 20:36 DEBUG  WindowsFrontend: __init__...
11-25 20:36 DEBUG  WindowsFrontend: on_init...
11-25 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_AU', 'en']
11-25 20:36 INFO   root: Received settings
11-25 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_AU', 'en']
11-25 20:36 DEBUG  TaskList: # Running tasklist...
11-25 20:36 DEBUG  TaskList: ## Running Remove bootloader entry...
11-25 20:36 ERROR  WindowsBackend: Cannot find bcdedit
11-25 20:36 DEBUG  WindowsBackend: undo_bootini C:
11-25 20:36 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6941.0 mb free fat32)
11-25 20:36 DEBUG  TaskList: ## Finished Remove bootloader entry
11-25 20:36 DEBUG  TaskList: ## Running Remove target dir...
11-25 20:36 DEBUG  CommonBackend: Deleting C:\ubuntu
11-25 20:36 DEBUG  TaskList: ## Finished Remove target dir
11-25 20:36 DEBUG  TaskList: ## Running Remove registry key...
11-25 20:36 DEBUG  TaskList: ## Finished Remove registry key
11-25 20:36 DEBUG  TaskList: # Finished tasklist
11-25 20:36 INFO   root: Almost finished uninstalling
11-25 20:36 INFO   root: Finished uninstallation
11-25 20:36 DEBUG  CommonBackend: Fetching basic info...
11-25 20:36 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Stephen Parker\My Documents\Downloads\wubi.exe
11-25 20:36 DEBUG  CommonBackend: platform=win32
11-25 20:36 DEBUG  CommonBackend: osname=nt
11-25 20:36 DEBUG  WindowsBackend: arch=amd64
11-25 20:36 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\data\isolist.ini
11-25 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 20:36 DEBUG  WindowsBackend: Fetching host info...
11-25 20:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 20:36 DEBUG  WindowsBackend: windows version=xp
11-25 20:36 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-25 20:36 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-25 20:36 DEBUG  WindowsBackend: windows_build=2600
11-25 20:36 DEBUG  WindowsBackend: gmt=10
11-25 20:36 DEBUG  WindowsBackend: country=AU
11-25 20:36 DEBUG  WindowsBackend: timezone=Australia/Sydney
11-25 20:36 DEBUG  WindowsBackend: windows_username=Stephen Parker
11-25 20:36 DEBUG  WindowsBackend: user_full_name=Stephen Parker
11-25 20:36 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Stephen Parker
11-25 20:36 DEBUG  WindowsBackend: windows_language_code=1033
11-25 20:36 DEBUG  WindowsBackend: windows_language=English
11-25 20:36 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     L7100  @ 1.20GHz
11-25 20:36 DEBUG  WindowsBackend: bootloader=xp
11-25 20:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 10941.65625 mb free fat32)
11-25 20:36 DEBUG  WindowsBackend: drive=Drive(C: hd 10941.65625 mb free fat32)
11-25 20:36 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-25 20:36 DEBUG  WindowsBackend: uninstaller_path=None
11-25 20:36 DEBUG  WindowsBackend: previous_target_dir=None
11-25 20:36 DEBUG  WindowsBackend: previous_distro_name=None
11-25 20:36 DEBUG  WindowsBackend: keyboard_id=-536804335
11-25 20:36 DEBUG  WindowsBackend: keyboard_layout=jp
11-25 20:36 DEBUG  WindowsBackend: keyboard_variant=
11-25 20:36 DEBUG  WindowsBackend: total_memory_mb=2038.3515625
11-25 20:36 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 20:36 DEBUG  CommonBackend: Searching for local CDs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
11-25 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:36 INFO   root: Running the installer...
11-25 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_AU', 'en']
11-25 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_AU', 'en']
11-25 20:37 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=7000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=steve
11-25 20:37 INFO   root: Received settings
11-25 20:37 DEBUG  CommonBackend: Searching for local CD
11-25 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
11-25 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
11-25 20:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 20:37 DEBUG  CommonBackend: Searching for local ISO
11-25 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
11-25 20:37 DEBUG  TaskList: # Running tasklist...
11-25 20:37 DEBUG  TaskList: ## Running select_target_dir...
11-25 20:37 INFO   WindowsBackend: Installing into C:\ubuntu
11-25 20:37 DEBUG  TaskList: ## Finished select_target_dir
11-25 20:37 DEBUG  TaskList: ## Running create_dir_structure...
11-25 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-25 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-25 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-25 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-25 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-25 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-25 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-25 20:37 DEBUG  TaskList: ## Finished create_dir_structure
11-25 20:37 DEBUG  TaskList: ## Running create_uninstaller...
11-25 20:37 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Stephen Parker\My Documents\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-25 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-25 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-25 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-25 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-25 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-25 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-25 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
11-25 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-25 20:37 DEBUG  TaskList: ## Finished create_uninstaller
11-25 20:37 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-25 20:37 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-25 20:37 DEBUG  TaskList: ## Running get_diskimage...
11-25 20:37 DEBUG  TaskList: New task download
11-25 20:37 DEBUG  TaskList: ### Running download...
11-25 20:37 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-25 20:37 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-25 21:04 DEBUG  TaskList: ### Finished download
11-25 21:04 DEBUG  downloader: download finished (read 507143012 bytes)
11-25 21:04 DEBUG  TaskList: ## Finished get_diskimage
11-25 21:04 DEBUG  TaskList: ## Running extract_diskimage...
11-25 21:07 DEBUG  TaskList: ## Finished extract_diskimage
11-25 21:07 DEBUG  TaskList: ## Running choose_disk_sizes...
11-25 21:07 DEBUG  WindowsBackend: total size=7000
  root=2744
  swap=256
  home=0
  usr=4000
11-25 21:07 DEBUG  TaskList: ## Finished choose_disk_sizes
11-25 21:07 DEBUG  TaskList: ## Running expand_diskimage...
11-25 21:07 DEBUG  TaskList: ## Finished expand_diskimage
11-25 21:07 DEBUG  TaskList: ## Running create_swap_diskimage...
11-25 21:07 DEBUG  TaskList: ## Finished create_swap_diskimage
11-25 21:07 DEBUG  TaskList: ## Running modify_bootloader...
11-25 21:07 DEBUG  TaskList: New task modify_bootini
11-25 21:07 DEBUG  TaskList: ### Running modify_bootini...
11-25 21:07 DEBUG  WindowsBackend: modify_bootini C:
11-25 21:07 DEBUG  TaskList: ### Finished modify_bootini
11-25 21:07 DEBUG  TaskList: ## Finished modify_bootloader
11-25 21:07 DEBUG  TaskList: ## Running diskimage_bootloader...
11-25 21:07 DEBUG  WindowsBackend: Copying C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\winboot -> C:\ubuntu\winboot
11-25 21:07 DEBUG  TaskList: ## Finished diskimage_bootloader
11-25 21:07 DEBUG  TaskList: # Finished tasklist
11-25 21:07 INFO   root: Almost finished installing
11-25 21:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\STEPHE~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
11-25 21:47 INFO   root: Finished installation
11-25 21:47 INFO   root: Rebooting
11-25 21:47 DEBUG  TaskList: # Running tasklist...
11-25 21:47 DEBUG  TaskList: ## Running reboot...
11-25 21:47 DEBUG  TaskList: ## Finished reboot
11-25 21:47 DEBUG  TaskList: # Finished tasklist
11-25 21:47 DEBUG  root: application.quit
11-25 21:47 DEBUG  WindowsFrontend: frontend.quit
11-25 21:47 DEBUG  WindowsFrontend: frontend.on_quit
11-25 21:47 DEBUG  root: application.on_quit
11-25 21:47 INFO   root: sys.exit

```

---

### Post by Mark Phelps on 2011-11-30
The VFAT file systems will not allow the creation of files larger than ~4GB.

In the bug text, it clearly states the following:

> Since oneiric introduced the 5GB minimum install size, and since the preinstalled image (one-stage install was introduced) it is no longer possible to install onto a FAT32 partition.

So no, you can't do an install of Wubi to that filesystem.

---

### Post by bcbc on 2011-11-30
The interesting thing is that you didn't get the error message - if you look at the log file I posted on the bug report there are numerous errors which were somehow bypassed in your case.

Since 11.10 was released there are two distinct methods of installing Wubi. One that downloads a preinstalled image (which you used) and the old way (from an Ubuntu CD, or with the Ubuntu desktop CD ISO in the same folder as wubi.exe). The old way will still work on a FAT32 partition. There is this minor issue but it still works: [lpbug]888281[/lpbug]

My recommendation is - if you want to try out Ubuntu - use the old way to install Wubi. If you decide to actually use it, you would be better off partitioning, rather than deal with the FAT32 limitations.

---

### Post by Shurakai2000 on 2011-11-30
Thanks Guys.

I looked through the log file too, but couldn't find anything that indicated a problem.

I was trying to install ubuntu without having to repartition my hard drive. Mostly because I don't want to have to reinstall Windows. Using a live USB proves that ubuntu can run with my hardware so that is good. Now I need to figure out how to repartition my hard drive to do a proper install without deleting windows.

Thanks again for your help.


steve

---

### Post by bcbc on 2011-11-30
I like this site - it's based on the 10.10 installer, but it's very detailed and a lot of work went into carefully covering every scenario. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

(Or you could just let the Ubuntu installer 'automagically' do it.)

---

