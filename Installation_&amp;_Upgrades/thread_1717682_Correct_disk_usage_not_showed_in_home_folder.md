---
title: "Correct disk usage not showed in home folder"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by chaoticist on 2011-03-30
I'm running Windows Vista, with Ubuntu installed after it, through Wubi.

The installation was fine, and everything went quite smoothly.

I have a smallish windows partition, about 25Gib, and a ~87Gib partition that I installed Ubuntu on, through, as I said, Wubi.

The problem I'm experiencing is this: GParted, DUA, and even the Windows Disk Manager (accessed by right-clicking on My Computer while in Vista) all say that I have more than 60Gib free.

However, when I open my Home folder, at the bottom, it says I only have 2.9Gib free space.

That's a rather large and alarming discrepancy. I've looked through at least 10 different posts, and have not found someone with my specific problem.

I am using a 120Gb 2.5 inch SATA laptop drive. Everything works fine, otherwise, and I'm using a 1TB external drive for storage, and have it formatted into NTFS so that both Windows and Ubuntu (running Maverick 32 bit) can access it for storage. I have both connected to the external storage for access to documents, downloads, music, pictures, and videos, which is working wonderfully.

Even Rhythmbox doesn't have a problem with the arrangement, seeing as the external is automatically mounted upon boot, before the startup command to start Rhythmbox at boot runs.

Even though I've run every cleaner I can think of (Including Computer Janitor, Ubuntu Tweak, and Synaptic to remove un-needed elements, packages, etc) the Home folder still shows that I have significantly less space than it should.

It did become a problem, as it told me when I was downloading packages to install, that I had less than x amount of MiB left.

Does anyone know what the problem is? I've run everything I can think of, and still that number does not change.

---

### Post by Dutch70 on 2011-03-30
To help out, please post a pic of Gparted & Nautilus showing the space you're referring to. 

Use the paper clip in the toolbar to post a thumbnail view.

---

### Post by chaoticist on 2011-03-30
[attach]187545[/attach]

[attach]187546[/attach]

---

### Post by Dutch70 on 2011-03-30
I forget, Wubi is just altogether different. Maybe the pics will help someone with more knowledge on Wubi, or maybe it's something very simple to begin with. 

Just so you know, in the future, you will get more hits by people with Wubi knowledge if it says Wubi in your title. 

If you haven't seen it already, you may be able to find some answers here...
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1639198[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by chaoticist on 2011-03-30
Thank you for trying. I looked at that page you linked, and didn't really see anything that might apply. The installation went perfectly. It's only the free space that I have trouble with. The right hand says I've got plenty, the left hand pokes me in the freakin' eye.

---

### Post by Rubi1200 on 2011-03-30
The only thing I can think of right now is that you installed Wubi with the default 17GB and that the space has run out quickly.

Have you installed a lot of software, saved a lot of files on the Wubi install?

What does this command in Ubuntu show?

```
df -H
```
Post the output here.

---

### Post by Frogs Hair on 2011-03-30
Look in the Ubuntu system monitor under file system and it will display the original partition size and free space . This may not apply , but if Ubuntu is improperly shutdown It will not display the correct free space and needs to be properly shutdown an restarted.

---

### Post by bcbc on 2011-03-30
when you have a dedicated partition that you want to install Ubuntu on, Wubi is not the right choice. Wubi is designed to try out Ubuntu without partitioning - and it creates a fixed virtual disk within the host partition (this allows it to install on an ntfs or fat32 file system).

So the question is - did you intend to use the whole 87 GiB for Ubuntu? If yes, you should not use Wubi.

If you want Windows to access the partition as well, then you can use Wubi - but you might want to manage it so your personal data is stored on the /host (host ntfs partition) not on the virtual disk. Then you can a) share the data between Windows, and b) not use up your wubi virtual disk space. It's also safer since data on the virtual disk is data stored on a virtual file system within a single file on another file system.

---

### Post by oldfred on 2011-03-30
Wubi is just a file inside a NTFS partition. Wubi also has limits on how large you can make that file. So wubi will not be the full size of the partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you want a larger install you may have to migrate to full partitions.
HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by chaoticist on 2011-03-30
Wow. Thank you to everyone for posting in such a short time.

The short answer is, I've had a full install of Ubuntu before, and really liked it.

I also needed a few windows programs, and they wouldn't run properly under Wine.

I tried to install Ubuntu alongside Vista, but I'm guessing that I did not do it right, because everything stopped working and I had to start over. Something about the mount point, I'm guessing. The basic Ubuntu install is much easier.

That's why I've used Wubi.

---

### Post by chaoticist on 2011-03-30
> **Rubi1200 said:**
> The only thing I can think of right now is that you installed Wubi with the default 17GB and that the space has run out quickly.

Have you installed a lot of software, saved a lot of files on the Wubi install?

What does this command in Ubuntu show?

```
df -H
```
Post the output here.

dante@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/loop0             6.0G   2.8G   2.9G  49% /
none                   2.2G   259k   2.2G   1% /dev
none                   2.2G   3.2M   2.2G   1% /dev/shm
none                   2.2G   107k   2.2G   1% /var/run
/dev/sda2               94G   7.2G    87G   8% /host
/dev/sdc1              1.1T   323G   679G  33% /media/Ext. Storage

---

### Post by Rubi1200 on 2011-03-31
> **chaoticist said:**
> dante@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/loop0             6.0G   2.8G   2.9G  49% /
none                   2.2G   259k   2.2G   1% /dev
none                   2.2G   3.2M   2.2G   1% /dev/shm
none                   2.2G   107k   2.2G   1% /var/run
/dev/sda2               94G   7.2G    87G   8% /host
/dev/sdc1              1.1T   323G   679G  33% /media/Ext. Storage
Thanks for the output.

The problem is you only created a 6GB Wubi install.
```
/dev/loop0             6.0G   2.8G   2.9G  49%

```
Obviously, space will run out fairly quickly.

You should consider either a new install with more space, a proper install to a dedicated partition, or resizing the root.disk.

---

### Post by chaoticist on 2011-03-31
> **Rubi1200 said:**
> Thanks for the output.

The problem is you only created a 6GB Wubi install.
```
/dev/loop0             6.0G   2.8G   2.9G  49%

```
Obviously, space will run out fairly quickly.

You should consider either a new install with more space, a proper install to a dedicated partition, or resizing the root.disk.

Do you know of a good guide I could use to install Ubuntu alongside windows in a dedicated partition, and still have both operating systems work?

Or barring that, how to resize the root.disk?

---

### Post by AndyCinDallas on 2011-03-31
Pretty good guide [here](http://ubuntuforums.org/showthread.php?t=1519354) on migrating Wubi to its own partition.

---

### Post by chaoticist on 2011-03-31
> **AndyCinDallas said:**
> Pretty good guide [here](http://ubuntuforums.org/showthread.php?t=1519354) on migrating Wubi to its own partition.

I think I saw that one...but I was hesitant. Would migrating Wubi to it's own partition still work like it did, meaning would I still be able to dual-boot windows and ubuntu like I have been?

---

### Post by Rubi1200 on 2011-03-31
The whole point of migrating the Wubi install is to allow a proper dual-boot installation. So, to answer your question, yes.

If you feel hesitant at this stage, try resizing the root.disk:
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by chaoticist on 2011-03-31
> **Rubi1200 said:**
> The whole point of migrating the Wubi install is to allow a proper dual-boot installation. So, to answer your question, yes.

If you feel hesitant at this stage, try resizing the root.disk:
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

I think that I'll try resizing, when I have the time, before I migrate. Thank you so much for all your help. :D

---

### Post by Dutch70 on 2011-03-31
> **chaoticist said:**
> I think I saw that one...but I was hesitant. Would migrating Wubi to it's own partition still work like it did, meaning **would I still be able to dual-boot windows and ubuntu like I have been?**

Yes you'd still be dual booting, but it would be a true dual boot. In other words, Ubuntu wouldn't be dependent on windows. 
The way you've got it now, if windows goes down, it's taking Ubuntu with it & you've got no computer til you get it fixed. 

If you migrate Wubi to it's own partition and windows crashes, gets full of virus', whatever it does. You'd still have a nice working computer with Ubuntu.

---

### Post by Rubi1200 on 2011-04-01
> **chaoticist said:**
> I think that I'll try resizing, when I have the time, before I migrate. Thank you so much for all your help. :D
No problem, you are more than welcome :-)

If you have more questions, feel free to ask.

---

### Post by chaoticist on 2011-04-01
You've all been wondrously helpful, and I take my hat off to you.

I have, though, decided to try to migrate, if I can fix up my partitions.

Edit: I migrated it, it went, as far as I can tell, perfectly. Now all that's left is to uninstall Wubi from inside Vista, and then I suppose delete the partition I created so I can add it to which partition the free space ends up beside.

Edit#2: The home folder and DUA both suggest that it did, indeed, go perfectly. I thank you all once more for all your assistance. It has been invaluable.

---

### Post by chaoticist on 2011-04-01
OKAY so...I definitely messed up.

I used a program in Windows to move my ubuntu partition (/dev/sda3) left one slot, and moved the unallocated space to the right, so that  Windows is /dev/sda1, and Ubuntu is /dev/sda2.

Now, I can't boot either from the hard drive. I read that I have to reinstall grub to either sda (where I installed it the first time, I think) or to /dev/sda2, now that dev/sda3 no longer exists. They suggested using a Live CD or LiveUSB to reinstall GRUB.

The problem is, when I do so, and follow the instructions, I can't get past the second step, which is (after you install grub to the LiveUSB and then go into the terminal and type sudo grub) find /boot/grub/stage1 or /find/grub/stage1.

I get a "file not found" error for both. How can I reinstall Grub?  When I try to boot, I get grub recovery or some such, but I don't know any of the commands.

Yes, I know, I ruined all our hard work. I'm sorry. :(

---

### Post by Rubi1200 on 2011-04-01
Okay, before you start jumping to conclusions, let's see the output of the boot info script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by chaoticist on 2011-04-01
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    92,162,047    92,160,000   7 HPFS/NTFS
/dev/sda2          92,164,905   160,601,804    68,436,900  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   625,139,711   625,137,664   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4012 MB, 4012900352 bytes
124 heads, 62 sectors/track, 1019 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62     7,834,071     7,834,010   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       a1d8da85-793e-9249-bff9-f7c60e06906b   ext2       casper-rw                     
/dev/sda1        C498DB5098DB3F9A                       ntfs       Windows                       
/dev/sda2        338fa599-6973-41b0-8968-55a3e649a862   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7561F5330596BF39                       ntfs       320 Storage                   
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        04F1-FEB3                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/338fa599-6973-41b0-8968-55a3e649a862 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 338fa599-6973-41b0-8968-55a3e649a862
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 338fa599-6973-41b0-8968-55a3e649a862
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=-1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 338fa599-6973-41b0-8968-55a3e649a862
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=338fa599-6973-41b0-8968-55a3e649a862 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 338fa599-6973-41b0-8968-55a3e649a862
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=338fa599-6973-41b0-8968-55a3e649a862 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 338fa599-6973-41b0-8968-55a3e649a862
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 338fa599-6973-41b0-8968-55a3e649a862
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c498db5098db3f9a
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc        proc  nodev,noexec,nosuid         0  0  

# root was on /dev/sda3 when migrated
UUID=338fa599-6973-41b0-8968-55a3e649a862    /    ext4    errors=remount-ro    0    1

=================== sda2: Location of files loaded by Grub: ===================


  51.6GB: boot/grub/core.img
  75.3GB: boot/grub/grub.cfg
  51.6GB: boot/grub/stage2
  48.2GB: boot/initrd.img-2.6.35-28-generic-pae
  51.6GB: boot/vmlinuz-2.6.35-28-generic-pae
  48.2GB: initrd.img
  51.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 5a 04  |.X.SYSLINUX...Z.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  9a 89 77 00 d3 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b3 fe f1 04 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 08  40 00 00 66 ba 00 00 00  |..E}.f..@..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

```

---

### Post by Rubi1200 on 2011-04-01
Okay, so the next procedure also requires the LiveCD and an Internet connection.

To avoid errors, copy/paste the commands I will now give you and Enter after each one separately.

What we will do is purge and reinstall GRUB to the MBR of sda.
```

sudo mkdir /mnt/temp
sudo mount /dev/sda2 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```This will bring you to a root prompt. Thereafter, no need to preface commands with sudo.

Now, these commands:
```
apt-get update
apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc
update-grub 
exit
```Finally, unmount:
```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```Reboot.

Let me know what happens and if there are errors at any point, stop and report them here please.

(thanks to drs305 for the method: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099))

---

### Post by chaoticist on 2011-04-01
Thank you for being so patient with me. I know you could probably be making better use of your time.

When I rebooted, it went right back into GRUB recovery, as it has been doing. Attached is the log I saved of the terminal output.

Edit: I just read through the log, and although I know I pasted and executed that last command to unmount, it doesn't show that I did. Odd. Should I go through and do it again?

---

### Post by Rubi1200 on 2011-04-01
When it came time to install the grub package did it offer you the option to install to the drive or the partition?

You need to tell it to install to the drive, in this case sda (may also be called hda).

Installing to the partition will result in those errors.

I suggest you try the procedure again and when the dialog screen comes tell grub to install to sda.

If you already tried that, then I need to contact someone to ask for help on this.

> I know you could probably be making better use of your time.You are not wasting my time. One of the reasons I use Ubuntu and joined this forum is to be able to help others as best I can.

edit: I need to go offline for a while. I will look back in on this in about an hour.

---

### Post by chaoticist on 2011-04-01
> **Rubi1200 said:**
> When it came time to install the grub package did it offer you the option to install to the drive or the partition?

You need to tell it to install to the drive, in this case sda (may also be called hda).

Installing to the partition will result in those errors.

I suggest you try the procedure again and when the dialog screen comes tell grub to install to sda.

If you already tried that, then I need to contact someone to ask for help on this.


You are not wasting my time. One of the reasons I use Ubuntu and joined this forum is to be able to help others as best I can.
Alright, I'll be back with the results. I don't remember which one I chose, but I'll do it again.
At any rate, thank you for your help. If this does not work, I'll start over, and do the partitions correctly this time.

---

### Post by oldfred on 2011-04-01
You have two MBRs, but the install history gives the warning about installing grub to a partition. Did you choose to install grub to sda2 not sda?

Before you did the update you had old grub legacy in sda and a grub2 that pointed to a wrong partition in sdb:
```
 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

```

Are you booting from sda and does it now have grub2 booting from sda2?

If not you may just need to install grub2 to sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda2 and want grub2 in drive sda's MBR:
#Find linux partition, change sda2 if not correct:
sudo fdisk -l
#confirm that linux is sda2
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

Note that the grub install line is to sda the drive not the partition sda2.

---

### Post by chaoticist on 2011-04-01
Rubi, you were correct, I had installed grub to sda2 rather than sda. That's my fault. I should have known that it couldn't go on the Ubuntu partition. Currently writing this from my Ubuntu partition, rather than the LiveUSB I was using.

Thank you so much, for your time, and for your help. I'm glad you were here. You have saved me at least 4 hours of reinstall time, and another 2 or 3 of customization time, to get both Windows and Ubuntu back the way I like them.

Without you, I would have had to reinstall windows, reinstall all my programs, and then install Ubuntu through Wubi again, then migrate Wubi to the correct partition, then customize Ubuntu and reinstall my themes, icons, and applications, all over again.

You have made my day, and I tip my hat at you.

@Oldfred: Thank you as well for taking the time to read through all of this, and to post suggestions.

People like you two are one of the main reasons I love Ubuntu. If you have problems with Windows, you are more or less on your own. It really makes me happy to know that people like you two are here if someone needs help.

Once again, thank you.

---

### Post by Rubi1200 on 2011-04-01
Excellent! I am really pleased this worked out for you. 

Plus, it is a valuable learning experience. You now know some of the steps that need to be taken when troubleshooting booting/installation issues.

Enjoy and don't forget to ask questions if/when you need help. There will always be someone willing to offer support.

---

### Post by chaoticist on 2011-04-01
Not to keep harping, but you saved my bacon. I have to get to sleep, I have to get ready for work in...7 hours. Yay! Thank you again for your help.

---

### Post by Rubi1200 on 2011-04-01
Sleep well and, again, you are more than welcome :-)

---

