---
title: "Need help in installing ubuntu 9.10!"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by McYaballow on 2009-12-24
Ok first of all, I'm completely new to Unix-like OS so please try to keep explanations as simple as possible.

So I have a PC with an internal HDD which has Windows Vista Home Premium installed on it and I have an external HDD which has a ntfs partition ~900GB and ~100GB unallocated space. I burned the Ubuntu 9.10 live CD and my goal is to install Ubuntu on the unallocated space I have on the external HDD. The computer I'm using is a HP Pavilion p6140sc and from the BIOS I can choose the device I want to boot from with complete ease. Now the problem I encountered when I tried to install Ubuntu with the help of some online tutorials is that I get some GRUB-related problems when trying to boot. Now I was thinking that since I will be having Ubuntu and Windows on separate HDD devices, would there even be any need to have a multi boot system becase I can always select the boot device manually anyways at BIOS? So if I select the external from the BIOS, it would go automatically boot Ubuntu from it? So thinking this way I tried reinstalling Ubuntu and in the last step of the installation wizard, I choose Advanced and choose not to install the multiboot system (I assume this is the GRUB in question?). But even after this when I try to boot from the device, I get "GRUB loading." and nothing happens. I tried Google -searching for answers but I didn't find anything which would help or then they were too complicated for me to understand; again I'm very new to Ubuntu. The way I "reinstalled" was by deleting the partitions created during installation using Disk Utility (I'm using the Ubuntu Live CD) but I think I did before try to choose to install the multi boot so I don't that left the MBR in an unwanted state? How can I reset the MBR of my external drive and what is the proper way to to a clean reinstall of Ubuntu?

---

### Post by lindsay7 on 2009-12-24
One way to do this is to install Ubuntu to your external drive with the internal drive disconnected.  This will do the install thinking that the external drive is the only drive on the system and Grub will be installed to that drive only. You can then choose to start the system with Ubuntu on the external drive or your other os on the internal dirve using the bios options for the first startup drive.  If you do the Ubuntu installation with the internal drive connected, the installation will see both drives and both os's and want to set up grub for that situation.

---

### Post by McYaballow on 2009-12-25
But in my case, why does GRUB need to be installed in the first place? As I said, I will only be having one OS per device so I guess I don't need to have a multi boot system like GRUB? And in the installation wizard, if I choose in the last part Advanced and the multi boot device location as sdb, doesn't this only install it then on the external drive?

---

### Post by McYaballow on 2009-12-25
I just tried installing Ubuntu on the unallocated space and I chose to install the multi boot thingie in sdb, which is the external HDD. After install I restart and it says GRUB loading error: unknow filesystem grub rescue>

Now what's this all supposed to mean? I'm not going to disconnect my internal HDD because theres no way I have to do that because I have perfectly fuctioning HDDs at my use and if the Ubuntu OS installation can't deal with that then.. whatever seriously..

But to note this is a different kind of error because before I got just GRUB loading.. and nothing happened.

---

### Post by McYaballow on 2009-12-25
This is my output from sudo fdisk -l

```
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      108853   874361691    7  HPFS/NTFS
/dev/sdb2          108854      121601   102398310    5  Extended
/dev/sdb5          108854      121077    98189248+  83  Linux
/dev/sdb6          121078      121601     4208998+  82  Linux swap / Solaris
```

I also got bored and tried the disconnection of the internal HDD and installed the OS on the external drive but I still get the same error.

---

### Post by darkod on 2009-12-25
Boot with the ubuntu cd, Try Ubuntu option. Download the script in my signature, move it on desktop for example, and execute it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with detailed info about your boot process. Copy the content of the file here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above).

---

### Post by McYaballow on 2009-12-26
```
============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e8b026b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   941,789,183   941,789,121   7 HPFS/NTFS
/dev/sda2         941,789,184   976,769,023    34,979,840   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8900690

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,748,723,444 1,748,723,382   7 HPFS/NTFS
/dev/sdb2       1,748,723,445 1,953,520,064   204,796,620   5 Extended
/dev/sdb5       1,748,723,508 1,945,102,004   196,378,497  83 Linux
/dev/sdb6       1,945,102,068 1,953,520,064     8,417,997  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="E2B2AE6EB2AE46BF" LABEL="HP" TYPE="ntfs" 
/dev/sda2: UUID="7A10B1D010B1939B" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb1: UUID="0CC0CD4BC0CD3BA8" LABEL="Timo_HDD" TYPE="ntfs" 
/dev/sdb5: UUID="75b1ffe1-e2aa-4fe3-9600-c342535756e9" TYPE="ext4" 
/dev/sdb6: UUID="3f8bc3af-f8d7-41f3-96c9-21f53e5e5109" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
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
/dev/sdb5 on /media/75b1ffe1-e2aa-4fe3-9600-c342535756e9 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1 on /media/Timo_HDD type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set 75b1ffe1-e2aa-4fe3-9600-c342535756e9
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
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 75b1ffe1-e2aa-4fe3-9600-c342535756e9
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=75b1ffe1-e2aa-4fe3-9600-c342535756e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 75b1ffe1-e2aa-4fe3-9600-c342535756e9
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=75b1ffe1-e2aa-4fe3-9600-c342535756e9 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e2b2ae6eb2ae46bf
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 7a10b1d010b1939b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=75b1ffe1-e2aa-4fe3-9600-c342535756e9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=3f8bc3af-f8d7-41f3-96c9-21f53e5e5109 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 895.3GB: boot/grub/grub.cfg
 895.3GB: boot/initrd.img-2.6.31-16-generic-pae
 895.3GB: boot/vmlinuz-2.6.31-16-generic-pae
 895.3GB: initrd.img
 895.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by lindsay7 on 2009-12-26
Ok, this is what I would do.

First, clean up your windows mbr.  Look at the following, this will take out the grub file and you can boot to windows.

   1. Put the Windows Vista or Windows 7 installation disc in the disc drive, and then start the computer.
   2. Press a key when you are prompted.
   3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
   4. Click Repair your computer.
   5. Click the operating system that you want to repair, and then click Next.
   6. In the System Recovery Options dialog box, click Command Prompt.
   7. Type Bootrec.exe, and then press ENTER.

Note To start the computer from the Windows Vista or Windows 7 DVD, the computer must be configured to start from the DVD drive. For more information about how to configure the computer to start from the DVD drive, see the documentation that is included with the computer or contact the computer manufacturer.
Back to the top
Bootrec.exe options
The Bootrec.exe tool supports the following options. Use the option that is appropriate for your situation.

Note If rebuilding the BCD does not resolve the startup issue, you can export and delete the BCD, and then run this option again. By doing this, you make sure that the BCD is completely rebuilt. To do this, type the following commands at the Windows RE command prompt:

    * bcdedit /export C:\BCD_Backup
    * c:
    * cd boot
    * attrib bcd -s -h -r
    * ren c:\boot\bcd bcd.old
    * bootrec /RebuildBcd

/FixMbr
The /FixMbr option writes a Windows 7 or Windows Vista-compatible MBR to the system partition. This option does not overwrite the existing partition table. Use this option when you must resolve MBR corruption issues, or when you have to remove non-standard code from the MBR.
/FixBoot
The /FixBoot option writes a new boot sector to the system partition by using a boot sector that is compatible with Windows Vista or Windows 7. Use this option if one of the following conditions is true:

    * The boot sector has been replaced with a non-standard Windows Vista or Windows 7 boot sector.
    * The boot sector is damaged.
    * An earlier Windows operating system has been installed after Windows Vista or Windows 7 was installed. In this scenario, the computer starts by using Windows NT Loader (NTLDR) instead of Windows Boot Manager (Bootmgr.exe).

Second. Use the Ubuntu install disk and use Gparted to reformat the 100 gig partition of the external drive.

Third. If you want to boot to either system and not have a dual boot system, you should disconnect the internal hard dirve and just install Ubuntu to the 100gig partition. Grub has to be installed on any Linux system. With the internal drive disconnected grub will install on the external drive and not know that there is another dive installed as well a windows will not know that Ubuntu is installed on the external drive.  With this set up, you will need to start the computer with the bios set to start up on the internal dirve first to start window. You will need to tell the bios to start up on the external drive first to start up on Ubuntu.  There are other ways to do what this does, but from what you have said, this would seem to be what you want to do. and is will be clean as far as not having grub on the mbr of your windows setup.

---

### Post by darkod on 2009-12-26
First I would try reinstalling grub2. Yes, I know this was new install but it still might be messed up. Boot with ubuntu cd, Try ubuntu option and in terminal do:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

This will reinstall grub2 on the MBR of your ext hdd, as you want. And yes, you do need grub bootloader because it needs to boot ubuntu. Grub is not just for dual boot or when two OS are on same disk. You will have grub even if you only have ubuntu on your computer.
After doing the above restart without the cd, make sure you select the ext hdd to boot from and see whether the grub error is still there.
Now, relating to windows, there is some mess there too. You can see you have the boot files, /bootmgr and /boot/BCD in both /dev/sda1 and /dev/sda2. There should be only in one place as far as I know.
Hopefully the above commands will repair the ubuntu boot. To sort out the windows boot, repair the boot process by using the vista dvd and the Repair This Computer option. Or the manual commands already posted here. But before repairing windows boot there is one IMPORTANT THING!!!!! Make the internal hdd first in boot order in BIOS and save the BIOS settings. This is because when reinstalling grub2 with the command above you can choose where to install it (/dev/sdb) but with windows it just puts itself on the MBR of the first drive in boot order. That's why your internal 500GB hdd MUST be first in boot order BEFORE trying to repair windows bootloader.
There might be a problem with XP on /dev/sdb1 because there doesn't seem to be any boot files there. That is if you are using XP at all. But we'll worry about that after all of the above has been done. :)

PS. Personally I don't recommend unplugging anything. Not right now. If you unplug your internal hdd you can potentially create issues. For example, grub uses hd0, hd1, etc notation for the hdds. With the internal unplugged when you install ubuntu and grub the external will be hd0 (only drive) and grub will configure itself to look for ubuntu on hd0. By plugging back the internal hdd that becomes hd0 and suddenly you're wondering why grub can't boot ubuntu. Unplugging is the end of the troubleshooting process, not the beginning. My philosophy is: when installing any OS, windows or linux, let it know what hardware you've got, have your system connected the way you want it. In some situations you can create issues with having things disconnected.

---

### Post by McYaballow on 2009-12-27
Now to clarify, I never had Windows XP installed on the external nor internal HDD. I simply only formatted the external HDD on a Windows XP computer when I bought it.

I just did the GRUB reinstall and restarted and I get:

```
GRUB loading.
error: uknown filesystem
grub rescue>
```I'm now using the Live CD again and opened GParted and there's actually a warning on the main partition of my internal HDD. GParted advices me to do Chkdsk, which I will do as soon as I can but would this be a possible reason why I'm getting the GRUB error above?

Anyways it's intersting to hear that my Vista boot is also messed up now, although I'm not facing any problems when I try to boot from the internal HDD.

Now as stupid as this sounds, I don't have an installation disc for Vista. When I bought this PC 3 months ago I didn't get any disc, but only the option from Windows to burn recovery/restoration discs. From what I understand and remember, you can't access the command prompt from there. Are there any other alternative boot disk images online I can use to access Chkdsk and Bootrec?

---

### Post by McYaballow on 2009-12-27
Ok so I actually managed to run the Chkdsk without CDs since it ran it automatically when I started Windows. Now GParted doesn't say there are any errors anymore on the drive.

So then I tried booting from the external again, and now I get:
```
GRUB loading.
```And nothing happens.

I think I have done a mistake because when I did the GRUB reinstall, I had a USB stick connected to my PC which resulted in the external being sdc instead of sdb, so I replaced sdb -> sdc in the GRUB reinstallation code you posted. But NOW my external is sdb so I decided to try the GRUB reinstall again but I get the following error in the terminal:

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
grub-probe: error: Cannot find a GRUB drive for /dev/sdb5.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```Now about fixing the Windows MBR, it should be noted that I will be upgrading to Windows 7 in the near future and that my computer is going for repair tomorrow morning  (issues unrelated to this thread). They might format completely my internal HDD in the processs so will there be any need to start repairing the internal MBR manually?

---

### Post by darkod on 2009-12-27
> **McYaballow said:**
> 

[code]ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
grub-probe: error: Cannot find a GRUB drive for /dev/sdb5.  Check your device.map.



What is /dev/sdc now? It didn't exist in the results file. Check your drives/partitions with:
sudo fdisk -l

If your ubuntu (linux) partition is still /dev/sdb5 repeat the commands with slight modification:

sudo mount /dev/sdb5 /mnt
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb

If your ubuntu partition is no longer /dev/sdb5 modify the commands as necessary. The --recheck argument will generate new device.map that it was complaining about.

---

### Post by McYaballow on 2009-12-27
Yes it was sdc only that one time because I had a USB stick connected during boot and that stick was sdb at the time. Then I decided to replace sdb with sdc in the GRUB reinstall code because of the mixup. But now the external is sdb and I did the reinstall the way you asked and according to the terminal it was succesful. I tried booting from the external but still:

```
GRUB loading.
```And nothing happens.

---

### Post by darkod on 2009-12-27
Hmmm... I'm puzzled. Sorry. :(

---

### Post by McYaballow on 2009-12-27
> **darkod said:**
> Hmmm... I'm puzzled. Sorry. :(
Thanks anyways for trying!

---

### Post by McYaballow on 2009-12-29
Update: I took my HP p6140sc for repair so I decided to connect my external HDD to my older PC and to my surprise the Ubuntu boot was succesful. I'll update my status when I'll get my HP p6140sc back from repair and see if it would work.

---

