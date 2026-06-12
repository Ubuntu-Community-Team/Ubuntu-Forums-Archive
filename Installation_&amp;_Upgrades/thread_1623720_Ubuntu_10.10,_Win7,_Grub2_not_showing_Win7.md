---
title: "Ubuntu 10.10, Win7, Grub2 not showing Win7"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by matthewaveryusa on 2010-11-16
I read other posts and each answer seems individual.
I know for sure that the Win7 is installed on sda as follows:

sda1 == ??
sda2 == 20GB allocated to Win7
sda3 == data

sdb == linux

sdc == data

I'm a real noob, this is my 3rd attempt at switching to linux for good, but I still need win7 for Starcraft2 ;)

Can you walk me through this one?

Thanks,
Matt

```
m@m-lnx:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x607e1fef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848    83888127    41840640    7  HPFS/NTFS
/dev/sda3        83888128  1953519615   934815744    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b435ac6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953521663   976759808    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b199

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1929752575   964875264   83  Linux
/dev/sdb2      1929754622  1953523711    11884545    5  Extended
/dev/sdb5      1929754624  1953523711    11884544   82  Linux swap / Solaris

Disk /dev/dm-0: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b435ac6

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1            2048  1953521663   976759808    7  HPFS/NTFS

```

Edit:

I ran the bootinfo script. The results are very confusing for me (when I googled dev/mapper I got a lot of hits on RAID-group topics. These drives aren't in a RAID group although I did play around with the idea before installing the current non-RAID win7 ). Here is the Result.txt content:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/mapper/pdc_ebbijibef

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_ebbijibef1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    83,888,127    83,681,280   7 HPFS/NTFS
/dev/sda3          83,888,128 1,953,519,615 1,869,631,488   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,929,752,575 1,929,750,528  83 Linux
/dev/sdb2       1,929,754,622 1,953,523,711    23,769,090   5 Extended
/dev/sdb5       1,929,754,624 1,953,523,711    23,769,088  82 Linux swap / Solaris


Drive: pdc_ebbijibef ___________________ _____________________________________________________

Disk /dev/mapper/pdc_ebbijibef: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_ebbijibef1              2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS

/dev/mapper/pdc_ebbijibef1 ends after the last sector of /dev/mapper/pdc_ebbijibef

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/pdc_ebbijibef: PTTYPE="dos" 
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        3f9325e9-107a-4165-a72e-2964245be870   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ef89d4ef-ae37-4715-b989-b7cf5bc53c5b   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc                                                promise_fasttrack_raid_member                               
error: /dev/mapper/pdc_ebbijibef1: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_ebbijibef

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 3f9325e9-107a-4165-a72e-2964245be870
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 3f9325e9-107a-4165-a72e-2964245be870
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3f9325e9-107a-4165-a72e-2964245be870
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3f9325e9-107a-4165-a72e-2964245be870 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3f9325e9-107a-4165-a72e-2964245be870
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3f9325e9-107a-4165-a72e-2964245be870 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,2)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3f9325e9-107a-4165-a72e-2964245be870
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3f9325e9-107a-4165-a72e-2964245be870
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=3f9325e9-107a-4165-a72e-2964245be870 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=ef89d4ef-ae37-4715-b989-b7cf5bc53c5b none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


 749.6GB: boot/grub/core.img
   4.5GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.35-22-generic
 749.6GB: boot/vmlinuz-2.6.35-22-generic
   1.1GB: initrd.img
 749.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on pdc_ebbijibef1



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/mapper/pdc_ebbijibef1: No such file or directory
hexdump: /dev/mapper/pdc_ebbijibef1: No such file or directory

```

---

### Post by Innigo on 2010-11-17
I've just been through all this and might be able to point you in the right direction, although I'm no expert. 

re. boot_info_script: some stuff it get's right but not all. I had that "According to ... " stuff about sector start also but I think you can ignore that. 

What's up with partition #1  on sda? (, msdos/boot/grub) doesn't sound good to me. Grub looks to be installed on sda on the Windows disk. Grub tripped me up also by defaulting to sda rather than where I thought it'd go. Personally, I'd put it with Linux on sdb. Then try to get it to install itself so that one of the menu entries points to Windows on sda.

oldfred helped me out with this little recipe:

sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Note: the dpkg-reconfigure brought up an old style blue window that asked first for a Linux command line - I left it blank
Then it asked for a Linux cmd line param - I left it as "quiet-splash"
Then I got the option to select with the space bar.
[ ]   sda  
[ ]   sdb  
[ ]   sdc




[FONT=monospace][/FONT]

---

### Post by ronparent on 2010-11-17
Presuming that sda is boot, then the boot loader should be looking in the sdb 1st partition for /bbot/grub. A simple grub reinstall from a live cd should fix this up. 

Boot to a live cd and open a terminal window. Enter:

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

This will fix the problem in most cases. Good luck.

---

### Post by oldfred on 2010-11-17
If you are for sure not using the promise RAID controller any more the drive retains metadata that confuses things.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

As posted before you should install grub2 to sdb. You may want to reinstall your windows boot loader or the lilo boot loader so sda can directly boot windows. It should not be required but I like to have the bootloader in the MBR of the drive with the system.

---

### Post by matthewaveryusa on 2010-11-18
My objective was to have windows on 1 HD with its boot record, and ubuntu on the other with Grub. I disconnected all but the windows drive and restored the master boot record using (I got to the win7 cmd by booting from a recovery I downloaded here [http://neosmart.net/blog/2009/windows-7-system-repair-discs/ ](http://neosmart.net/blog/2009/windows-7-system-repair-discs/ )):

```
bootrec.exe /FixMbr
bootrec.exe /FixBoot
bootrec.exe /RebuildBcd
```

I then removed the Windows HD and connected the ubuntu HD so I could re-install it. 

I then re-arranged the hard-drive boot sequence to have the windows HD boot first.

Now I auto-boot into Windows, and press F8 at boot-time to load the ubuntu HD when I want to play around with it.

Thanks,
Matt

---

### Post by oldfred on 2010-11-19
If you run this grub's osprober will find the windows install and let you boot it. If you want to default to windows you can install SUM and make windows the default. But then you can always boot the Ubuntu/grub drive without having to switch in BIOS.

sudo update-grub

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---

### Post by bellylint on 2011-03-03
Not sure if this was mentioned earlier but...

An easy way to have Grub2 redetect your missing Windows XP or Windows 7 partitions is by installing and running startupmanager.

1. From a terminal window enter: 
**sudo apt-get install startupmanager**

2. After installation completes, you can now run the program from the terminal by entering: 
**sudo startupmanager**

3. A GUI will appear, from the drop-down menu you can see the other OS's on your machine. You can change the default boot-up OS or leave it alone. Click the CLOSE button and your done!

Now when you reboot...tadaaaa, you will see your missing Windows partitions listed under Grub!

---

