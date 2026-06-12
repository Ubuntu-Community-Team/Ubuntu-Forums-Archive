---
title: "Unknown filesystem, grub rescue mode. Win7, then Ubuntu were installed"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by noigan on 2010-10-02
Hi guys!

A few days ago I decided to try a linux OS for the first time. I created a ~80gb partition (on a 320 gb sata disk) for Win7 and installed it. Then I installed Ubuntu 10.04, chose to make partitions manually, created a primary ext4-partition (right after the one with Win7) for / and a 1024mb swap partition.

After the installation the boot loader failed to load any system, giving the error from the topic title. I tried several ways to reinstall/repair/reconfigure grub in the live-CD mode. Some of them didn't change anything, others were not completed because of an update-grub error ("cannot find a device for / (is /dev mounted?)"). 

Grub version is 1.98b. The disk with Win7 and Ubuntu is treated as hd0 in grub and sdd in Ubuntu. I also tried reinstallung the boot loader to different partitions/disks - that made no good as well. Right now the loader is at the sdd-disk. And here are the results of bootscriptinfo:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdd2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   130,255,019   130,254,957   7 HPFS/NTFS
/dev/sdb2         130,255,020   260,493,974   130,238,955   7 HPFS/NTFS
/dev/sdb3         260,493,975   390,716,864   130,222,890   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   143,362,047   143,360,000   7 HPFS/NTFS
/dev/sdd2         143,362,048   159,571,967    16,209,920  83 Linux
/dev/sdd3         159,571,968   161,572,863     2,000,896  82 Linux swap / Solaris
/dev/sdd4         161,572,864   625,137,663   463,564,800   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        64240B3A240B0F2C                       ntfs       Highwind                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A26828AF6828845F                       ntfs       &#1042;&#1089;&#1105; &#1087;&#1086;&#1076;&#1088;&#1103;&#1076;           
/dev/sdb2        9268DB2D68DB0EBB                       ntfs       &#1052;&#1091;&#1079;&#1099;&#1082;&#1072;&#8482;               
/dev/sdb3        266CB0E26CB0AE45                       ntfs       &#1115;                            
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01C962FF831761E0                       ntfs       Millenium Falcon              
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        5A24520C2451EB8F                       ntfs                                     
/dev/sdd2        5778dd13-eca0-4866-a833-65be71c4abc5   ext4                                     
/dev/sdd3        063fc3d4-6dd5-46a2-9be0-d73eeb9647ac   swap                                     
/dev/sdd4        62580F2B580EFE13                       ntfs       China's                       
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/&#1042;&#1089;&#1105; &#1087;&#1086;&#1076;&#1088;&#1103;&#1076; fuseblk    (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)
/dev/sdb1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=512)


=========================== sdd2/boot/grub/grub.cfg: ===========================

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
set root='(hd3,2)'
search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
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
set root='(hd3,2)'
search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5778dd13-eca0-4866-a833-65be71c4abc5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5778dd13-eca0-4866-a833-65be71c4abc5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd3,2)'
    search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdd1)" {
    insmod ntfs
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 5a24520c2451eb8f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd2 during installation
UUID=5778dd13-eca0-4866-a833-65be71c4abc5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd3 during installation
UUID=063fc3d4-6dd5-46a2-9be0-d73eeb9647ac none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd2: Location of files loaded by Grub: ===================


  77.9GB: boot/grub/core.img
  78.8GB: boot/grub/grub.cfg
  78.5GB: boot/initrd.img-2.6.32-21-generic
  79.0GB: boot/vmlinuz-2.6.32-21-generic
  78.5GB: initrd.img
  79.0GB: vmlinuz

```Would be much appreciated if someone helps me :)

Best regards,
Aleksey
--------------
**Note**: even though the thread is marked as Solved, the issue is actually not. I have managed to dual-boot Win7 and Ubuntu, but with partition configuration changes. And I'll still be glad if someone hints me at the solution (even though I will probably not be testing it anymore:) ).

---

### Post by ronparent on 2010-10-02
Which drive is the bios set to boot on? The sda boot loader appears to be linux but doesn't appear to have a boot target. The sdd boot loader appears to be correct for sdd set as boot in bios. Since Ubuntu didn't come up after installation I would suspect that the boot loader was not installed on the boot drive. It can be probably be fixed either by setting the disk identified as sdd as boot in bios or by reinstalling grub to boot from your boot disk - your preference. Good move posting the results of the boot script.

---

### Post by noigan on 2010-10-03
**ronparent**, sdd is the first boot device in BIOS. 

And I am a bit confused by Syslinux in the sda MBR myself. What does it mean anyway?

---

### Post by ronparent on 2010-10-03
You do appear to have done everything right. You are probably also following the methods given in this reference: > [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

Why don't you try reinstalling grub 2 from a live cd one more time with the following commands:
> sudo mount /dev/sdd2 /mnt

sudo grub-install --root-directory=/mnt/ /dev/sdd 

If you get the same results and it still won't boot, then we might have to conclude that some oddity in the bios is blocking grub from performing properly. What are your hardware specs by the way? Is your bios up to date?

---

### Post by noigan on 2010-10-05
```
sudo mount /dev/sdd2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdd
```I already tried this, with the same result.

Here is my hardware: CPU Athlon x2 3800+, MB [Gigabyte GA-M51GM-S2G]("http://ee.giga-byte.com/products/mb/bios/ga-m51gm-s2g_10.html"), RAM DDR2 667 1024 MB, GPU GF7600GT. A couple of hours ago I updated the bios from f6 to f15 - no progress so far.

---

### Post by ronparent on 2010-10-05
How is the port the sdd is plugged into set in bios?

---

### Post by drs305 on 2010-10-05
Are you left at the grub prompt? (If at the Grub menu, press "c" to get to the Grub2  prompt.)

If so, try typing "set" to see what the prefix and root settings are.

Then try finding the Linux files. First type "ls" to see the partitions, then run the following with (hd3,2), then (hd0,2), (hd1,2), (hd2,2) until you find your Ubuntu boot files:
```
ls (hd3,2)/boot
```
See if it finds your Ubuntu files. The first file listed will probably be *System.map....* but there should also be a "vmlinuz..." and "initrd.img..." file.

Once you find the files, does the (hdXY) match the values shown in "set"?

---

### Post by noigan on 2010-10-06
**ronparent**, it is Extended IDE Drive (and sata2 physically), if that's what you meant. 
[B]
drs305[/B], the diskwith Win7 and Ubuntu (and grub2 in the mbr) is defined as hd0 in grub rescue prompt. Even so, ls (hd0,2)/boot gives the "unknown filesystem" error... just as ls (anything else listed by single ls)/boot. And in grub.cfg ubuntu root is (hd3,2) %)

The strange thing is that sometimes th disks under live-cd mode are defined differently. For example, during the last live-cd boot the win7+ubuntu device was sbd instead of the usual sdd.

---

### Post by drs305 on 2010-10-06
Can you boot into Windows at all?

Can you change your BIOS boot order so that the drive with your Ubuntu and Windows install boots first? This appears to be the only drive on which the Windows and Ubuntu boot files are located in their respective partitions.

The first thing I would try would be to change the boot order so that on boot the drive with Ubuntu (sdd) is looked at first. The grub2 files appear intact and Grub2 is installed in that MBR. 

If that doesn't work and you can't currently boot either OS, I would try to get Windows back. You can do that using your Windows disks to repair the MBR of sdd. This should remove the Grub2 MBR info and restore the Windows MBR. If you can't do it with a Windows disk, you can boot an Ubuntu LiveCD, install lilo, and fix the MBR from the the LiveCD.

```
sudo apt-get install lilo  # It will issue some warnings which you can disregard. Do not fully install lilo.
sudo lilo -M /dev/sd**X** mbr
```

Use "sudo fdisk -l" and "df -Th" to help determine which drive the LiveCD thinks your Ubuntu and Windows drives are on.

---

### Post by noigan on 2010-10-06
**drs305**, I mentioned above that the hdd with Win7 and Ubuntu is the first in BIOS disk boot priority section.

I am able to restore Windows MBR (and are doing so after unsuccessful attempts to repait Grub2). But I still want to get Ubuntu working.

BTW, the Ubuntu .iso was downloaded from a local tracker, and its md5 sum is equal to the one from [here]("https://help.ubuntu.com/community/UbuntuHashes").

---

### Post by drs305 on 2010-10-06
> **noigan said:**
> **drs305**I am able to restore Windows MBR (and are doing so after unsuccessful attempts to repait Grub2). But I still want to get Ubuntu working.[/URL].

Yes, we just have to take one thing at a time. Since your partitions were not showing properly, I wanted to confirm the problem was with Ubuntu and not your hard drive or the partition table. Once we are sure Windows works (and thus the drive is healthy), then we can work on getting Grub and Ubuntu working properly.

When Windows is working correctly, then I'd like you to boot a LiveCD and follow the instructions in the following guide, which I wrote this week:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

You can start by trying to just reinstall Grub2. If that doesn't work, use the full "chroot" procedure. 

Verify your Ubuntu install is on sdd2 before running the commands. When you are done, you will want to have BIOS boot to sdd first.

---

### Post by psusi on 2010-10-06
Hrm... it looks like grub is installed just fine.  This is a SATA disk?  Is your bios set to IDE emulation or AHCI mode?

---

### Post by noigan on 2010-10-08
**drs305**, the chroot method seemed to have worked smoothly, even update-grub worked with no errors. Yet, the rescue mode is still there.

**psusi**, yes, the disk is a sata-2 one. But my MB seem to not support AHCI, and I can only enable sata-RAID mode. The integrated peripherials and SATA config screens look like this:
[[IMG]http://i10.fastpic.ru/thumb/2010/1009/96/8a986efb2b06f172e5b5e97acb4c2596.jpeg[/IMG]]("http://fastpic.ru/view/10/2010/1009/8a986efb2b06f172e5b5e97acb4c2596.png.html")[[IMG]http://i10.fastpic.ru/thumb/2010/1009/9b/f74e941526741e7eb7c064560bd44a9b.jpeg[/IMG]]("http://fastpic.ru/view/10/2010/1009/f74e941526741e7eb7c064560bd44a9b.png.html")
Upgrading to f15 bios added a couple of options having nothing to do with AHCI.

---

### Post by drs305 on 2010-10-08
> **noigan said:**
> **drs305**, the chroot method seemed to have worked smoothly, even update-grub worked with no errors. Yet, the rescue mode is still there.

**psusi**, yes, the disk is a sata-2 one. But my MB seem to not support AHCI, and I can only enable sata-RAID mode. The integrated peripherials and SATA config screens look like this:
[[IMG]http://i10.fastpic.ru/thumb/2010/1009/96/8a986efb2b06f172e5b5e97acb4c2596.jpeg[/IMG]]("http://fastpic.ru/view/10/2010/1009/8a986efb2b06f172e5b5e97acb4c2596.png.html")[[IMG]http://i10.fastpic.ru/thumb/2010/1009/9b/f74e941526741e7eb7c064560bd44a9b.jpeg[/IMG]]("http://fastpic.ru/view/10/2010/1009/f74e941526741e7eb7c064560bd44a9b.png.html")
Upgrading to f15 bios added a couple of options having nothing to do with AHCI.


I'm afraid I don't know a lot about Grub2 and RAID; posting a new RESULTS.txt will probably help those who do.

---

### Post by noigan on 2010-10-09
**drs305**, yeah, sorry. Here it is:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdd2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   130,255,019   130,254,957   7 HPFS/NTFS
/dev/sdb2         130,255,020   260,493,974   130,238,955   7 HPFS/NTFS
/dev/sdb3         260,493,975   390,716,864   130,222,890   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   143,362,047   143,360,000   7 HPFS/NTFS
/dev/sdd2         143,362,048   159,571,967    16,209,920  83 Linux
/dev/sdd3         159,571,968   161,572,863     2,000,896  82 Linux swap / Solaris
/dev/sdd4         161,572,864   625,137,663   463,564,800   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        64240B3A240B0F2C                       ntfs       Highwind                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A26828AF6828845F                       ntfs       &#1042;&#1089;&#1105; &#1087;&#1086;&#1076;&#1088;&#1103;&#1076;           
/dev/sdb2        9268DB2D68DB0EBB                       ntfs       &#1052;&#1091;&#1079;&#1099;&#1082;&#1072;™               
/dev/sdb3        266CB0E26CB0AE45                       ntfs       &#1115;                            
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01C962FF831761E0                       ntfs       Millenium Falcon              
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        5A24520C2451EB8F                       ntfs                                     
/dev/sdd2        5778dd13-eca0-4866-a833-65be71c4abc5   ext4                                     
/dev/sdd3        063fc3d4-6dd5-46a2-9be0-d73eeb9647ac   swap                                     
/dev/sdd4        62580F2B580EFE13                       ntfs       China's                       
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=512)


=========================== sdd2/boot/grub/grub.cfg: ===========================

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
set root='(hd3,2)'
search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
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
set root='(hd3,2)'
search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd3,2)'
	search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=5778dd13-eca0-4866-a833-65be71c4abc5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd3,2)'
	search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=5778dd13-eca0-4866-a833-65be71c4abc5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd3,2)'
	search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd3,2)'
	search --no-floppy --fs-uuid --set 5778dd13-eca0-4866-a833-65be71c4abc5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdd1)" {
	insmod ntfs
	set root='(hd3,1)'
	search --no-floppy --fs-uuid --set 5a24520c2451eb8f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd2 during installation
UUID=5778dd13-eca0-4866-a833-65be71c4abc5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd3 during installation
UUID=063fc3d4-6dd5-46a2-9be0-d73eeb9647ac none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd2: Location of files loaded by Grub: ===================


  77.9GB: boot/grub/core.img
  78.4GB: boot/grub/grub.cfg
  78.4GB: boot/grub/stage2
  78.5GB: boot/initrd.img-2.6.32-21-generic
  79.0GB: boot/vmlinuz-2.6.32-21-generic
  78.5GB: initrd.img
  79.0GB: vmlinuz
```

And here is the output of the chroot'ing, if it may clear anything else:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9b6d9b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3425ed8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8108    65127478+   7  HPFS/NTFS
/dev/sdb2            8109       16215    65119477+   7  HPFS/NTFS
/dev/sdb3           16216       24321    65111445    7  HPFS/NTFS

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x38275393

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdb195afb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           3      142225    71680000    7  HPFS/NTFS
/dev/sdd2          142225      158306     8104960   83  Linux
/dev/sdd3          158306      160291     1000448   82  Linux swap / Solaris
/dev/sdd4          160291      620177   231782400    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sdd2 /mnt/temp && sudo mount -B /dev /mnt/temp/dev && sudo mount -B /proc /mnt/temp/proc && sudo mount -B /sys /mnt/temp/sys && sudo mount -B /dev/pts /mnt/temp/dev/pts && sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf && sudo chroot /mnt/temp
root@ubuntu:/# apt-get update
Hit http://ru.archive.ubuntu.com lucid Release.gpg                          
Ign http://ru.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US       
Ign http://ru.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://ru.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://ru.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://ru.archive.ubuntu.com lucid-updates Release.gpg
Ign http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://ru.archive.ubuntu.com lucid Release
Hit http://ru.archive.ubuntu.com lucid-updates Release                         
Hit http://ru.archive.ubuntu.com lucid/main Packages                           
Hit http://ru.archive.ubuntu.com lucid/restricted Packages                     
Hit http://ru.archive.ubuntu.com lucid/main Sources
Hit http://ru.archive.ubuntu.com lucid/restricted Sources
Hit http://ru.archive.ubuntu.com lucid/universe Packages
Hit http://ru.archive.ubuntu.com lucid/universe Sources
Hit http://ru.archive.ubuntu.com lucid/multiverse Packages   
Hit http://ru.archive.ubuntu.com lucid/multiverse Sources    
Hit http://ru.archive.ubuntu.com lucid-updates/main Packages
Hit http://ru.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release     
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://ru.archive.ubuntu.com lucid-updates/main Sources
Hit http://ru.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://ru.archive.ubuntu.com lucid-updates/universe Packages
Hit http://ru.archive.ubuntu.com lucid-updates/universe Sources
Hit http://ru.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://ru.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 306 not upgraded.
After this operation, 6,603kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122713 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 306 not upgraded.
Need to get 0B/2,112kB of archives.
After this operation, 6,603kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 122438 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98-1ubuntu7_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98-1ubuntu7_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.98-1ubuntu7) ...
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------

Setting up grub-pc (1.98-1ubuntu7) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdd1
done

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdd1
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/temp/dev/pts && sudo umount /mnt/temp/sys && sudo umount /mnt/temp/proc && sudo umount /mnt/temp/dev && sudo umount /dev/sdd2
ubuntu@ubuntu:~$ 
```

---

### Post by drs305 on 2010-10-09
Just a couple of random thoughts.

If you aren't using RAID now, did you have RAID set up at one time? (Sorry, I couldn't view your attachments). There are cases where Grub2 still hangs if remnants of an old RAID setup are present. They can be removed with:
```

sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
etc....
# Also check BIOS for raid settings

```

Also, you mentioned your motherboard and updating the BIOS. There once was an 8.3GB limitation on the boot location. I don't know old the BIOS would have to be for that restriction to apply.

Finally, could you tell us at what point the boot fails? I'm assuming you are booting sdd first. 

If you get a Grub menu, press "c" to get to the grub prompt. Then type "ls (hd3,2)/boot" and see if it lists your Ubuntu boot files (including vmlinuz... and initrd.img...). You can also type "set" to see what the "prefix" and "root" settings are.

---

### Post by psusi on 2010-10-09
You also might try swapping sda and sdd so that you are booting from the first drive.  Also try fscking the filesystem.  Run sudo e2fsck -f /dev/sdd2.

---

### Post by noigan on 2010-10-11
**drs305**, I have never had raid enabled.

On the boot the rescue prompt appears right after the "Grub loading" line, so I don' get the menu. I tried using ls and set commands, it gave me only [this]("http://ubuntuforums.org/showpost.php?p=9931443&postcount=8").

**psusi**, e2fsck gave some summary as an output, and no errors. I retried installing grub2 to the MBR after this - no result.

---

### Post by oldfred on 2010-10-12
You mention that it is an IDE drive but SATA, so are you using a converter? Older IDE drives/BIOS would only boot from primary master and had to have the jumpers set correctly or be cable select. 

I would just try installing grub to sda b & C and try booting each. Perhap BIOS and the converter do not play well together??

You also have /grldr in windows. Is that an left over grob4dos folder. Sometimes that causes issues with grub booting windows. (When we get that far).

---

### Post by noigan on 2010-10-12
**oldfred**, the drive is sata, Extended IDE is the mode the BIOS uses to work with it. Besides, Win7 on its first partition loads without any problems.

As for placing grub to the other disk's MBR - I did, to /dev/sda (the 80 GB IDE disk). This let the boot go a bit further - the grub prompt (not the Rescue one) appeared. There I tried to use ls and set commands - Grub doesn't recognize sdd2 (ubuntu),sdd3 (ubuntu swap) and sdd4 (ntfs) filesystems, but **does** give a file lists for sdb2 (ntfs, 66 gb from the sdb start) and sdb3 (ntfs, 133 gb from the sdb start) and sdd1 (Win7) as well. 

Does that really mean Grub will never load an OS on the second partition of a SATA drive, if the BIOS doesn't support AHCI?

---

### Post by oldfred on 2010-10-12
I am not sure why it would not see sdd? We have seen drive numbering issues with mixed IDE and SATA drives where the drive order seems to change which confuses things. Can you unplug the IDE drive and see if it makes a difference. Not sure if there is some BIOS setting beyond what you have done.

---

### Post by noigan on 2010-10-12
**oldfred**, sorry if I made it vague. Grub does see sdd itself and all its partitions. But while sdd1 filesystem is distinguished as ntfs and files of sdd1 can be listed, ls with sdd2, sdd3 and sdd4 gives the "unknown filesystem" error.

---

### Post by oldfred on 2010-10-12
I just noticed:

16 heads, 63 sectors/track, 620181 cylinders

16 heads is not correct for LBA which all new drives should be using. If you look at your other drives they are all the correct 255 heads. Not sure if LBA not set in BIOS or something in drive is not set correctly and needs correction. Check BIOS then I would try the testdisk and see what it says.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by noigan on 2010-10-14
**oldfred**, Victoria says my 200 gb IDE (the one having all three partitions distinguished by Grub) and 80 gb IDE have 16 heads al well, and only the 750 gb sata drive has 255 heads. Plus, [here]("http://support.dell.com/support/edocs/storage/p123806/specs.htm") it's said 16 logical heads go in ST3320620AS (which is the *problem* disk) by default. Do I misunderstand something?

Yet, TestDisk supposes 16 heads to be incorrect and suggests to change the number (in the geometry section) to 128. I changed it to 255 and tried Analyze - the program found two instances of the Win7 partition and about 5-6 of the Ubuntu partition. It drove me dizzy completely %)

---

### Post by oldfred on 2010-10-14
With LBA you actually do not use CHS (cylinders, heads, sectors) as drives have become too large. Do you have LBA set on your BIOS? Some let you set it by drive or groups of drives.

---

### Post by noigan on 2010-10-15
**oldfred**, sata drives in my bios have only two modes - Large and Auto. They are set up to Auto, and the OSs themselves see all their partitions and sizes correctly.

---

### Post by oldfred on 2010-10-15
My BIOS also have large & auto, but it also allows the old CHS settings. Never tried it so I do not know how that works as I have not had to set CHS values for years. 

What does BIOS see on your drive? Do you have IDE compatibility set?

---

### Post by psusi on 2010-10-15
It sounds like your bios does not understand the sata controller's native AHCI mode.  If that is the case, then it likely can not see beyond a few gb into the disk, which would cause the symptoms you report.  The only way to resolve this is to install using a dedicated /boot partition near the start of the disk, where the bios can access it.

---

### Post by noigan on 2010-10-15
**oldfred**, it sees 65535 cylinders, 65534 for landing, 16 heads, 255 sectors and 0 for precomp. It's the same for both sata drives, the 320 gb with OSes and the 750 gb. 

I don't see a IDE compat. setting. There disks' settings include only Auto-Detection, IDE (Extended for sata) Device setup (None, Auto and UDE-only Manual) and the Access Mode. In Integrated Peripherials there are IDE config, which allows to turn IDE channels on|off and Sata RAID.

**psusi**, but is that possible to do so without ruining the Win7 installation?

---

### Post by psusi on 2010-10-15
> **noigan said:**
> **oldfred**, it sees 65535 cylinders, 65534 for landing, 16 heads, 255 sectors and 0 for precomp. It's the same for both sata drives, the 320 gb with OSes and the 750 gb. 

I don't see a IDE compat. setting. There disks' settings include only Auto-Detection, IDE (Extended for sata) Device setup (None, Auto and UDE-only Manual) and the Access Mode. In Integrated Peripherials there are IDE config, which allows to turn IDE channels on|off and Sata RAID.

**psusi**, but is that possible to do so without ruining the Win7 installation?

Using that geometry you can only address 127 gb.  Usually there is one knob that you can turn between raid, achi, and ide.  Get it set to ahci so it can access the whole disk, or you might try setting it to raid, which is ahci with a different pci id.  That will make windows not boot though if it does not have the raid driver installed.

If Windows is already on a partition using up the first 127 gb, then you will need to either reinstall it, or try to move the partition with gparted ( which will take AGES ).

---

### Post by noigan on 2010-10-15
The case is the partition with Win7 is only 80 gb.

---

### Post by drs305 on 2010-10-15
Here's the Seagate page on the issue:
[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=127_GB_-_137_GB_Limitation&vgnextoid=186b5b1142aec010VgnVCM100000dd04090aRCRD]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=127_GB_-_137_GB_Limitation&vgnextoid=186b5b1142aec010VgnVCM100000dd04090aRCRD")

---

### Post by noigan on 2010-10-15
**drs305**, it is different - the whole large disks's space is visible both in bios and in the OSes.

---

### Post by psusi on 2010-10-15
Then when you install Ubuntu, create a /boot partition right after the windows partition so it is under the 128 gb mark.  200mb should be enough.

---

### Post by noigan on 2010-10-16
I decided to move win7 partition 8 gb to the right (I took about 2,5 hours, yeah) and create a partition for Ubuntu at the beginning of the disk. A couple of manipulations with Win7 restore via the installation disk - and both OSes load and work.

Thanks everyone for help!

---

### Post by drs305 on 2010-10-16
:-) 

Congratulations. I'll have to go through this thread one more time from the beginning just to piece it together.

Anyway, would you please mark this SOLVED if you don't have any more issues? You do this via the 'Thread Tools' link near the top right of the first post. It will help others looking for solutions, and I'm sure there will be posters to this thread that will be happy to see it marked so.

And it's reversible if necessary...  ;-)

---

### Post by noigan on 2010-10-18
**drs305**, thanks! At last I can start studying Ubuntu. I could have done this re-partitioning long ago though :) Yet I still would like to figure out if this Grub-sata issue can be solved.

---

### Post by peter b on 2010-10-19
gone

---

### Post by oldfred on 2010-10-19
peter b

This thread is solved and only those looking for solutions to similar issues will be looking at it. You need to start your own thread.

Post this in your new thread:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Also review this:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by peter b on 2010-10-19
@oldfred,

you got the answer; satisfied ? hope through your v honest effort, as above, 'it just works' slogan will come to pass.

---

### Post by PerroGrande on 2010-10-21
I know the original poster solved his issue.  I had a strikingly similar issue which I was able to solve, but my method was different and substantially faster than moving the Win7 partition 8gb "up" with gparted...

My symptoms were all but identical to the OP.  I had a 1TB drive with the "low" 700 GB used for a Win7 partition and the upper 250GB (or so) left as unpartitioned space for holding 10.10.  Regardless of how I messed with the "upper" partitions, grub would drop into rescue mode with the "unknown filesystem" error.

The issue is obviously related to LBA48/Drive Geometry as this thread indicates.

My motherboard (Gigabyte GA-M61P-S3) was autodetecting the drives with their proper capacity (or so it seemed) and Windows had no issue seeing/using them with full capacity.

When drilling-down with the BIOS, however, the SATA controllers had two configuration options for each drive on the system:  AUTO and LARGE.  The default was set to AUTO and the "geometry" detected was the "16-head" variant the O.P. mentioned.  

Realizing that this geometry was bogus (and undoubtedly related to the issue), on a lark I tried manually selecting LARGE for the 1TB boot drive (I did the same for the 1TB data volume that is also in the system).  When I did this, the geometry changed to something that looked much more like what one would expect for an LBA48 drive... 240 heads, etc, etc.  

Once I did this, I tried one more time to install 10.10 in the "upper" area (partitions for /boot, /, /home, and swap -- fairly normal setup.)  Upon reboot, grub loads perfectly and booting to 10.10 and Win7 works flawlessly.  


Obviously, your mileage may vary and BIOSes are different.  Hope this helps someone!

---

### Post by drs305 on 2010-10-21
PerroGrande,

Welcome to the Ubuntu forums and thanks for sharing that information.

When you installed Ubuntu everything installed normally as far as you could tell? And then the first time you tried to boot into it you got the "unknown filesystem" message?

I'd just like to know so we know how to troubleshoot user problems. I would assume the above is how it happened, since if it booted once with a large drive it should continue to do so.

---

### Post by PerroGrande on 2010-10-21
Yes -- the original install (prior to changing the BIOS settings) looked perfectly normal.

The subsequent re-boot, however, produced the "unknown file system" error and dropped to grub rescue mode. 

With the "wrong" bios settings, this condition was largely unrecoverable.  The LiveCD could not read the ext4 filesystems I had created during the original install.  (I tried this because I thought perhaps grub.conf was messed up and some simple editing could correct it... no such luck!)

In order to get Windows to boot again (prior to fixing the BIOS settings), I had to use the Win7 DVD in repair mode, open a console and use:

fixboot.exe /FixMbr
fixboot.exe /FixBoot


***EDIT***

What I did *not* try was installing Ubuntu with the "Wrong" settings (BIOS set to "Auto") and then changing the BIOS settings to 'Large" and rebooting.  I effectively wiped and re-installed.

It also occurred to me that I have no idea where on my drive the Ubuntu installer wrote its data when the "wrong" BIOS settings were present...

---

