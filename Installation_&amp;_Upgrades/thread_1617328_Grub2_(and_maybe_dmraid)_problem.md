---
title: "Grub2 (and maybe dmraid) problem"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by Yankee14 on 2010-11-09
Greetings, folks!  It's sad to be meeting you all under my current circumstances; I've been fighting to get the latest Ubuntu 10.10 x86  installed and working correctly on my computer for about 36 hours now, but I refuse to give up! And so I must come to the forums for help.

I'm not sure exactly how to ask help for the problems I am having, because I am so new to linux.  Please allow me to describe what I've done so far to get where I am, and hopefully a possible solution to my problem will stand out to someone.

Feel free to skip around my post.  I have a tendency to ramble, but I prefer to be thorough in the hopes that it will prevent any misunderstandings.

I am primarily a Windows user; I have been using it since I was 12.  But, for various reasons I would like to start using Ubuntu in addition to Windows.  I have successfully set up a dualboot system before, and so I have some sort of clue as to how to partition drives and things of that nature.  I had so much trouble with all this, I decided to screw the concept of dualbooting Windows and Ubuntu for the time being, and just run Ubuntu (but still leaving space for a Windows installation later). 

I was having a problem getting Ubuntu to install, now I'm having trouble getting it to boot (and it may be that I haven't installed it correctly).

So here's what happened:

I have 3 SATA hard drives.  Here's how it was configured.

   1. 160GB - 1 Primary NTFS Partition - Windows XP Professional x64 Edition (obviously the boot sector is on this hard drive).
   2. 500GB - 1 Primary NTFS Partition - Just for storage.
   3. 1TB - 1 Primary NTFS Partition - Again, just for storage.

The latter 2 drives are important, stay tuned for more at 11.

I wanted to dualboot XP and Ubuntu.  Here's what I did:

I defragged XP a few times to make sure I didn't crush any data that may have been dangling towards the end of the partition.  After doing so, I popped in my lovely GParted livecd, resized the NTFS partition to approximately 120GB, leaving 40 or so unallocated GB for my Ubuntu installation.  Please note that GParted successfully recognised and displayed all my hard drives and all partitions on those drives.

After resizing, I booted into XP just to make sure it worked.  I let it have it's normal little temper tantrum about index verification, Kilroy was here; everything checked out alright, and Windows booted and worked just fine.

And now it was time to install Ubuntu--finally!  Threw in the livecd, slammed the tray shut, booted into the wonderful livecd architecture, and I was given a choice.  Try Ubuntu or Install.  Of course, I had already tried it out, so I picked Install.  Got through the first few menus and arrived at the "Allocate drive space" menu.  After selecting "Specify partitions manually" (because I didn't want to install it alongside XP, I wanted it to have it's own partition(s)), Ubuntu gave me the list of the hard drives it could detect.

This is where the excrement impacted the air distribution oscillator, so to speak.  Ubuntu listed my 2 storage drives, and nothing else.

And so began my extended late-night jaunt with Google, something with which I am sure we are all very familiar.  After much trial and error for many hours, including research yielding possible solutions such as:

   1. Updating my BIOS to several different revisions
   2. Experimenting with changing SATA/AHCI configurations on each BIOS revision I flashed
   3. Physically changing the SATA ports that the drives were plugged into
   4. Making sure everything was receiving power
   5. Even making sure the data cables weren't too close to the power cables to minimize any EMI
   6. Got back on GParted several times to make sure everything was still OK (which it seemed to be).
   7. I also tried formatting the unallocated space I left for Ubuntu to several different filesystems, including ext2, 3, and 4, reiserfs, and NTFS.

I did all this, and much more that I can't remember.  I've slept since then.  I just remember the particularly aggravating parts.  I probably reduced the longevity of my hard drive by several years in doing some of those things repeatedly, but meh.

Anyhow.  I booted the livecd and tried to see if any of the changes I made affected Ubuntu's ability to read my mysterious hard drive.  I tried again and again, booting into the livecd after changing just one variable at a time.

Finally, I found a solution that enabled Ubuntu to see the hard drive.  I had to uninstall and completely remove a program in the Synaptic Package Manager called "dmraid", which, from my understanding, is a tool which Ubuntu uses to map SATA configurations.  What a paradox!  Getting rid of the tool which Ubuntu uses to see SATA hard drives allowed Ubuntu to see my SATA hard drive!

(Some of you may be saying, "well, that nodmraid is also an optional flag which can be added by pressing F6 as the Ubuntu livecd begins to boot."  If I remember correctly, I tried that and to no avail.  I'm not sure.  I'll reboot and try it after I finish typing this post, but I think I tried it and it didn't do anything.)

Ok, so I had found the temporary fix to the hard drive problem, and it had to do with disabling dmraid.  As soon as I get rid of that package, the Ubuntu ubiquity installer can see my hard drive.  So, naturally, I began partitioning my hard drive as such (the following is the output of fdisk):

```
ubuntu@ubuntu:~/Desktop$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfe9c19cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0fa61992

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e2c68ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4462    35840953    5  Extended
/dev/sdc2            4463       19457   120447337+   7  HPFS/NTFS
/dev/sdc5   *           1          64      514017   83  Linux
/dev/sdc6              65        1339    10241406   83  Linux
/dev/sdc7            1340        1849     4096543+  82  Linux swap / Solaris
/dev/sdc8            1850        4462    20988891   83  Linux
ubuntu@ubuntu:~/Desktop$ 
```sdc1 is the extended partition.  Inside this partition, I created several other logical partitions according to my experiences with installing another linux distro a very long time ago called Backtrack.  I also learned that some people like to separate their /root ( / ) from /home by partitioning, and also that it is possible to put the /boot on its own partition as well.  Separating / from /home, and also /boot, regardless of your opinions and/or the reasons why, should nevertheless be possible, right?  This is what I want to do.

A more readable hierarchy looks like this:

sdc1 - extended partition

    sdc5 - 500MB ext4 for /boot
    sdc6 - 10GB ext4 for /
    sdc7 - 4GB of swap
    sdc8 - 20 or so ext4 for /home

sdc2 - NTFS filling the rest of the hard drive.  Nothing on it at the moment, I wiped Windows out as a last ditch effort to make this work.  It's just gonna sit there for now until I reinstall Windows (and yes, I know that installing Windows after Ubuntu will most likely complicate things again, as Windows will want to use its own bootloader.  I'll deal with that later.  I just want to get this working.)

So, I partitioned it as such, pointed Ubuntu to install /boot to sdc5, / to sdc6, and /home to sdc8.  This is where I may have gone wrong.  Knowing me, doing that probably wasn't quite right, but I've had a hard time finding anything on this sort of configuration.  Am I on the right track?  I know I did something very similar with installing Backtrack.

After getting all this done, I shut down the livecd, remove the cd, and try to boot up.  BIOS tells me it wasn't able to find a boot record or whatever the hell you want to call it, "insert boot disk and press return", blah blah.  Tried to do some research on how grub2 works, and it's all greek to me.  I remember having to mess with grub when I installed Backtrack on my laptop a year or so back, and it was really simple and straightforward to configure and troubleshoot, for me.  Grub2, as it's called, isn't proving to be that easy.  I tried commands I found on the Ubuntu wiki thing, including ```
sudo grub-probe -t device /boot/grub
```.  This particular command, which I think is supposed to locate grub installations on any device, keeps returning this error:

"grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?)."

I think it's mounted.  Is it mounted?  What does that mean?  I mounted every partition on that hard drive and it still didn't find anything.  What can I do to fix this?  Is dmraid still causing the problem somehow, or did I not configure the partitions correctly/install the right parts of Ubuntu to each partition?  Or is it something else?  I'm sorry if this exact question has already been asked, but I really really did try to find it.

Thanks,
Yankee14

P.S. - Info regarding my rig, and other outputs you may find useful in assisting me:

```
                Boot Info Script 0.55    dated February 15th, 2010                   

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:  

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc5 and
                       looks at sector 545374 of the same hard drive for
                       core.img, but core.img can not be found at this
                       location.
    Operating System: 
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System: 
    Boot files/dirs:  

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 124    71,682,029    71,681,906   5 Extended
/dev/sdc5    *            126     1,028,159     1,028,034  83 Linux
/dev/sdc6           1,028,223    21,511,034    20,482,812  83 Linux
/dev/sdc7          21,511,098    29,704,184     8,193,087  82 Linux swap / Solaris
/dev/sdc8          29,704,248    71,682,029    41,977,782  83 Linux
/dev/sdc2          71,682,030   312,576,704   240,894,675   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                        

/dev/loop0                                              squashfs                                
/dev/sda1        60049AC5049A9D9A                       ntfs       570r4g3                      
/dev/sda: PTTYPE="dos"
/dev/sdb1        C29CB83F9CB83031                       ntfs       Pepperoncini                 
/dev/sdb: PTTYPE="dos"
/dev/sdc1: PTTYPE="dos"
/dev/sdc2        6498A065267463F2                       ntfs       Windows XP Pro x64           
/dev/sdc5        4c568e0b-e6c6-4638-ba2e-d226cce933ce   ext4                                    
/dev/sdc6        9837b70d-4f90-4ab4-8d23-22ddf7d99c05   ext4                                    
/dev/sdc7        dd896b71-7fb5-4317-ae01-467ae76c7212   swap                                    
/dev/sdc8        cd12c18e-62c2-4206-814c-7f0229fd5746   ext4                                    
/dev/sdc                                                promise_fasttrack_raid_member                              

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc5        /media/4c568e0b-e6c6-4638-ba2e-d226cce933ce ext4       (rw,nosuid,nodev,uhelper=udisks)


============================= sdc5/grub/grub.cfg: =============================

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
set root='(hd2,msdos6)'
search --no-floppy --fs-uuid --set 9837b70d-4f90-4ab4-8d23-22ddf7d99c05
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set 4c568e0b-e6c6-4638-ba2e-d226cce933ce
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 4c568e0b-e6c6-4638-ba2e-d226cce933ce
    linux    /vmlinuz-2.6.35-22-generic-pae root=UUID=9837b70d-4f90-4ab4-8d23-22ddf7d99c05 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 4c568e0b-e6c6-4638-ba2e-d226cce933ce
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /vmlinuz-2.6.35-22-generic-pae root=UUID=9837b70d-4f90-4ab4-8d23-22ddf7d99c05 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 4c568e0b-e6c6-4638-ba2e-d226cce933ce
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 4c568e0b-e6c6-4638-ba2e-d226cce933ce
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sdc5: Location of files loaded by Grub: ===================


    .2GB: grub/core.img
    .2GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic-pae
    .0GB: vmlinuz-2.6.35-22-generic-pae

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=9837b70d-4f90-4ab4-8d23-22ddf7d99c05 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc5 during installation
UUID=4c568e0b-e6c6-4638-ba2e-d226cce933ce /boot           ext4    defaults        0       2
# /home was on /dev/sdc8 during installation
UUID=cd12c18e-62c2-4206-814c-7f0229fd5746 /home           ext4    defaults        0       2
# swap was on /dev/sdc7 during installation
UUID=dd896b71-7fb5-4317-ae01-467ae76c7212 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  00 00 00 05 12 00 00 00  00 10 18 00 ff 01 1f 00  |................|
00000010  01 02 00 00 00 00 00 05  20 00 00 00 20 02 00 00  |........ ... ...|
00000020  00 10 18 00 a9 00 12 00  01 02 00 00 00 00 00 05  |................|
00000030  20 00 00 00 21 02 00 00  00 10 18 00 ff 01 13 00  | ...!...........|
00000040  01 02 00 00 00 00 00 05  20 00 00 00 23 02 00 00  |........ ...#...|
00000050  00 10 14 00 a9 00 12 00  01 01 00 00 00 00 00 01  |................|
00000060  00 00 00 00 01 01 00 00  00 00 00 05 12 00 00 00  |................|
00000070  01 01 00 00 00 00 00 05  12 00 00 00 00 00 00 00  |................|
00000080  be 48 79 74 75 01 00 00  80 5a 00 00 00 00 00 00  |.Hytu....Z......|
00000090  8c 00 00 00 01 00 04 90  5c 00 00 00 6c 00 00 00  |........\...l...|
000000a0  00 00 00 00 14 00 00 00  02 00 48 00 03 00 00 00  |..........H.....|
000000b0  00 02 14 00 02 00 10 00  01 01 00 00 00 00 00 01  |................|
000000c0  00 00 00 00 00 03 18 00  ff 01 1f 00 01 02 00 00  |................|
000000d0  00 00 00 05 20 00 00 00  20 02 00 00 00 03 14 00  |.... ... .......|
000000e0  ff 01 1f 00 01 01 00 00  00 00 00 05 12 00 00 00  |................|
000000f0  01 02 00 00 00 00 00 05  20 00 00 00 20 02 00 00  |........ ... ...|
00000100  01 01 00 00 00 00 00 05  12 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  8c 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  be 40 79 74 77 01 00 00  a0 5b 00 00 00 00 00 00  |.@ytw....[......|
000001b0  8c 00 00 00 01 00 04 90  5c 00 00 00 6c 00 80 02  |........\...l...|
000001c0  01 00 83 fe 3f 3f 02 00  00 00 c2 af 0f 00 00 00  |....??..........|
000001d0  01 40 05 fe ff ff c4 af  0f 00 3b 8b 38 01 00 00  |.@........;.8...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```Hmm, just noticed that last bit of gibberish at the end labelled "Unknown Bootloader on sdc1."

Aha! A clue, Sherlock!

Still, ak2djg4mny306u2jh! doesn't help me too much.  I'm stuck.

```
ubuntu@ubuntu:~/Desktop$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```

---

### Post by psusi on 2010-11-09
You used the drive in a fake raid at one point in the past and the raid signatures are still on the disk.  Assuming you are no longer using it in a raid configuration, you need to remove that signature.  Run sudo dmraid -E /dev/sdc.

---

### Post by dino99 on 2010-11-09
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by oldfred on 2010-11-09
psusi is on right track but you may need to run on sda & sdb also.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)


I do not like installing a /boot for standard desktops. The standard instructions posted for reinstalling grub often leave out the extra command to also mount the /boot partition or may have a footnote to also mount it. You really only need /boot if running a server or have an older system with the 137GB boot limit.

Since you have more than one drive, why not have each operating system on separate drives. Then each boot loader can be in the same drive as the system install. Less issues with MBR conflicts.

Some even go so far as to install an operating system on every drive.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

### Post by Yankee14 on 2010-11-09
Thank you for the replies!

**sudo dmraid -E -r /dev/sdc certainly fixed the problem with Ubuntu being unable to see the hard drive.**   As it turned out, the other two hard drives didn't need it.  Thank you  to psusi for explaining the situation, and oldfred for elaborating upon  his explanation.

However, I am now facing a problem with the  bootloader.  The help page which dino99 has provided was very useful in  getting me to where I am right now, but it doesn't seem to document  Grub2, though learning the principles of how bootloading works was a  great help.  Thanks.

As for oldfred's suggestion of installing  each operating system on a separate drive, I cannot do that.  Each of  these drives must remain as storage drives exclusively.  **For all intents and purposes, please let us continue with the understanding that the only drive I have is /dev/sdc.**

> I do not like installing a /boot for standard desktops. The standard  instructions posted for reinstalling grub often leave out the extra  command to also mount the /boot partition or may have a footnote to also  mount it. You really only need /boot if running a server or have an  older system with the 137GB boot limit.

Since you have more than one drive, why not have each operating system  on separate drives. Then each boot loader can be in the same drive as  the system install. Less issues with MBR conflicts.I  think I understand most of what you were saying, but now I'm having  trouble understanding the difference between the MBR and the  bootloader.  Gathering from your post, the MBR is a container for the  bootloader, and can contain any sort of bootloader I choose to install,  whether it be Grub, Grub2, or the one Windows usually installs.  Also,  to my understanding, the boot partition must be the first partition?

As  for your recommendation to not have a separate /boot partition, I did  not take this lightly.  I do plan on messing with certain server  applications, particularly steam's source dedicated server, but that's  beside the point.  

After reading your post several times, I  decided to do away with the idea of installing /boot to its own  partition in the interests of actually getting my computer to boot *something*.   I deleted all the logical partitions in the extended partition and  started from scratch.  I created one ext4 to hold /, one swap partition  for..well..swap, and one ext4 for /home.  When partitioning the hard  drives from Ubuntu's install GUI, it asks me where I want the bootloader  to go.  I pointed it at the first ext4 partition which holds /,  effectively doing away with the idea of having a separate boot partition  for /boot.  **That's correct, right?**

[B]After using the  above dmraid command, and thereby fixing ubuntu's drive recognition  problem, and also not using a /boot partition, I rebooted and my BIOS  returned this:
[/B]
```
BOOT DISK FAILURE. PLEASE INSERT BOOT CD/DVD
```I'm  still learning how all of this works, and so I take this to mean that  my BIOS was unable to locate any BOOT sector instructions on any of my  hard drives.  Either that, or it found one and it just wasn't configured  correctly.  "DISK BOOT FAILURE" doesn't exactly provide me with much  information on where I went wrong.  In the meantime of hoping and  waiting for responses to this post, I'll be reading this,

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

an  article I found just before beginning this response to your posts.  It  looks like this may give me some insight to what I'm doing wrong.

I've  learned a lot through all the troubles I'm having with this as a linux  newbie, and I feel as though I'm on the home stretch of getting this to  work.

Thanks again for the help you all have provided thus far,
Yankee14

Ok, so I did away with all ideas I had for installing linux the way I wanted it, and just chose the "Erase entire hard disk" option and let ubiquity do its own thing.  The drive now looks like this:

   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18663   149903360   83  Linux
/dev/sdc2           18663       19458     6384641    5  Extended
/dev/sdc5           18663       19458     6384640   82  Linux swap / Solaris
```For some reason, it put the bootloader on my 500GB drive, /dev/sda.  I...guess...I don't have a problem with this, but does it have to be this way?  Windows doesn't do this when it uses its own bootloader, does it?  O CHURL, DRUNK ALL AND LEFT NO FRIENDLY DROP TO HELP ME AFTER! I'm so lost.  Is it even possible to get linux installed the way I wanted it?  With separate partitions for /, /boot, and home?  I know I did something similar in the past, and it was not this complicated...  I think I had everything configured properly except for the bootloader stuff.  I have no idea where I went wrong.  Here's the new results of running boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   299,808,767   299,806,720  83 Linux
/dev/sdc2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sdc5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        60049AC5049A9D9A                       ntfs       570r4g3                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C29CB83F9CB83031                       ntfs       Pepperoncini                  
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        f673e90f-5de4-46bf-8947-c328e0fa6827   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        f4e57b97-b246-4795-afff-15394407a5e3   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set f673e90f-5de4-46bf-8947-c328e0fa6827
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set f673e90f-5de4-46bf-8947-c328e0fa6827
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set f673e90f-5de4-46bf-8947-c328e0fa6827
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=f673e90f-5de4-46bf-8947-c328e0fa6827 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set f673e90f-5de4-46bf-8947-c328e0fa6827
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=f673e90f-5de4-46bf-8947-c328e0fa6827 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set f673e90f-5de4-46bf-8947-c328e0fa6827
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set f673e90f-5de4-46bf-8947-c328e0fa6827
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
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=f673e90f-5de4-46bf-8947-c328e0fa6827 /               ext4    errors=remount-ro 0       1
/dev/sdc5       none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


  94.6GB: boot/grub/core.img
  77.4GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-22-generic-pae
  94.6GB: boot/vmlinuz-2.6.35-22-generic-pae
   1.0GB: initrd.img
  94.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  f0 21 80 f1 00 a8 18 e0  79 01 ec 34 a0 e8 03 90  |.!......y..4....|
00000010  6d 05 b1 53 11 e1 8c 32  81 30 30 00 03 c0 60 80  |m..S...2.00...`.|
00000020  28 20 0d 0a 25 1a 03 40  99 69 65 da 94 64 11 10  |( ..%..@.ie..d..|
00000030  92 9f ef 21 ab 47 ff fc  e6 3c 94 a4 c8 64 27 78  |...!.G...<...d'x|
00000040  78 71 a4 a4 1a 39 54 09  04 5c 60 41 7b b1 0a 35  |xq...9T..\`A{..5|
00000050  40 17 cd df 91 b0 d7 e6  8c 06 03 d6 b1 ef 37 46  |@.............7F|
00000060  3d 2f 01 ed 63 0b 17 8c  3b 49 12 84 20 60 c1 1c  |=/..c...;I.. `..|
00000070  61 3c f9 4f 54 ab 22 4e  b0 11 54 7e c4 f0 3f b3  |a<.OT."N..T~..?.|
00000080  96 f1 51 58 46 47 fb fc  2e ba 81 02 7c 34 85 3d  |..QXFG......|4.=|
00000090  87 f6 8f e6 84 3f b8 c7  d0 10 9b 20 0e 40 08 2b  |.....?..... .@.+|
000000a0  68 d3 2c c7 2f 00 f8 87  95 50 8f 60 96 61 6c 22  |h.,./....P.`.al"|
000000b0  80 00 00 18 00 00 00 0a  01 00 30 01 c0 00 06 80  |..........0.....|
000000c0  0a 00 b0 0a 00 07 04 00  08 08 20 0c 00 18 05 10  |.......... .....|
000000d0  14 03 81 49 e1 38 40 4c  c7 37 e0 25 4c c8 c4 cd  |...I.8@L.7.%L...|
000000e0  e6 f0 61 03 14 32 17 8f  c0 84 93 5b f4 07 9b aa  |..a..2.....[....|
000000f0  c6 3b b0 0b dc 1a 31 05  17 8b f0 af 10 22 88 0b  |.;....1......"..|
00000100  4c e8 41 9f 64 7c bf 80  51 2c c6 15 e2 86 12 a2  |L.A.d|..Q,......|
00000110  98 82 22 10 6b 0e 29 8e  21 0c 87 b6 83 71 86 23  |..".k.).!....q.#|
00000120  88 54 51 4e 1d 61 e3 ab  11 52 c5 9f 31 44 53 65  |.TQN.a...R..1DSe|
00000130  c5 84 14 72 fe 6c 38 5a  1f 16 6c 45 14 51 44 96  |...r.l8Z..lE.QD.|
00000140  c8 64 c6 28 d1 30 e3 a8  a1 8e 2c 23 f3 7a 02 23  |.d.(.0....,#.z.#|
00000150  36 6c 16 21 8f 2e cc 62  0e 20 8a 88 81 08 3b 34  |6l.!...b. ....;4|
00000160  78 a6 f2 98 c4 66 c0 91  4b 30 31 88 b3 43 31 0c  |x....f..K01..C1.|
00000170  18 51 19 80 50 41 6b 12  85 00 4c 05 e4 e5 c6 eb  |.Q..PAk...L.....|
00000180  9f 38 58 5c b8 fa c1 f3  c1 b2 c7 8f 00 21 dd d9  |.8X\.........!..|
00000190  8f 42 b3 e0 21 8a 30 29  c5 9d 9e 00 c9 02 fd 57  |.B..!.0).......W|
000001a0  70 1e 02 64 01 6c 0a 50  92 04 d8 03 60 37 16 70  |p..d.l.P....`7.p|
000001b0  75 0e 10 45 22 e2 44 5a  02 40 74 00 0f 81 00 fe  |u..E".DZ.@t.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d8 c2 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Yankee14 on 2010-11-10
OK, ignore everything I've said above.  This is going to be straight and to the point.  I'm tired of reformatting and reformatting, and I've about had it with trying to understand how bootloading works in the context of the (in my opinion) vastly overcomplicated Grub2 bootloader.

**The issue I am having is dualbooting Microsoft Windows XP and Ubuntu 10.10 Desktop in the completely reasonable way that I want it to work.**

My current setup is:[INDENT]One 160GB SATA hard drive with
[/INDENT][INDENT][INDENT]One Primary 120GB NTFS partition with Windows XP installed.
[/INDENT][/INDENT][INDENT][INDENT][INDENT]Note: In the context of the problem I am having, I must make the obvious note that Windows has it's own bootloader, and has overwritten the MBR of the hard drive to point to its own bootloader.  Hopefully I'm understanding that correctly.
[/INDENT][/INDENT][/INDENT][INDENT]The remaining hard drive space is currently unallocated, and will remain so until I can understand exactly how this is going to work.
[/INDENT]The setup I have been going for over the last 3 days is:[INDENT]One 160GB SATA hard drive with
[/INDENT][INDENT][INDENT]One Primary 120GB NTFS partition with Windows XP installed.
[/INDENT][/INDENT][INDENT][INDENT]One Extended partition circumscribing the remaining hard drive space.
[/INDENT][/INDENT][INDENT][INDENT][INDENT]Note: This Extended partition will, of course, consist of several logical partitions housing my Ubuntu installation, a***nd will also include a separate partition for the Grub/Grub2 bootloader***.  It will look something like this:
[/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT]Logical Partition Number 1 (and yes, I know it will actually be /dev/sda5 or whatever)
[/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT][INDENT]This partition will be my bootloader partition. 
[/INDENT][/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT][INDENT]***I don't understand enough to know what exactly needs to go here.  Obviously, the bootloader does, but, does the /boot mount point go here in addition to installing the bootloader here?  I don't understand that question any more than you do.  Please see the image below for clarification.***
[/INDENT][/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT]Logical Partition Number 2
[/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT][INDENT]This partition will be the ( / ) root mount point, which to my understanding means that it will hold the linux kernel, any additional programs and packages I install, etc.
[/INDENT][/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT]Logical Partition Number 3
[/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT][INDENT]This partition will be the linux swap space area.  I understand swap space to be the linux equivalent of the Windows paging file.  Also, I have chosen to place it here, between the root mount point and the home mount point so that the heads don't have to travel very far over the platters to read and write data.  This may not be the most optimal configuration, but it seems the most logical to my tired eyes.  I hope that's right.  Whether or not it is optimal (I suppose) doesn't really matter at the moment, as it should, at the very least, *function*.  I can always go back and fix it later.  God knows how many times I've formatted; I can format a few more times later if needed after I actually get this to work.
[/INDENT][/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT]Logical Partition Number 4
[/INDENT][/INDENT][/INDENT][INDENT][INDENT][INDENT][INDENT]This partition will be the home mount point, which will, to my understanding, be home to any extra baggage I acquire during internet jaunts, i.e. mp3's, pdf's, etc.
[/INDENT][/INDENT][/INDENT][/INDENT]Here is the image I spoke of earlier.  Before viewing, please know that this is not the representation of my hard drive. It is merely a screencap of some random persons desired partition table which can clearly illustrate my question about bootloader-ing.

[IMG]http://img259.imageshack.us/img259/4301/ubuntu1010installationl.jpg[/IMG]

Now that I have hopefully made clear what it is I want to do, this image is an example of the problem I'm having with the bootloading.  As you can see, I've done a botched job in mspaint to highlight what the problem is, and what I'm not understanding.

Are /boot mount point AND the bootloader the same thing? 

Since Windows has overwritten the MBR to point at its own bootloader, obviously Ubuntu will need to overwrite what windows has written, placing a pointer in the MBR to the Grub/Grub2 bootloader on the logical partition.  I believe in Grub(1), the MBR code was called Grub Stage 1, and Stage 2 or (1.5 in some cases) would be the actual Grub menu I know and love, easily configurable by simply editing the menu.lst file.  Now, with Grub2, I don't know what the hell to make of any of it.  The documentation is too complicated for me to understand, and honestly has been very discouraging in trying out linux.  I swear on the life of my dummy, ***the most helpful documentation I found concerning how to install and configure Grub2 I found by typing "I hate grub2" into Google.***

So now, I don't really even know how to phrase the real question properly.  How do I get the bootloader installed and configured correctly in the context of installing it the way I want it to work, using the menu you see above, and possibly GParted to flag the boot partition as bootable?  Do I have to put /boot into the same partition that will house the Grub/Grub2 bootloader?  Do I not mess with setting a specific mount point for /boot and just install the bootloader into the partition?  Do I do the opposite, and use the partition for the /boot mount point and shove the bootloader up my ****?

Any help would be desperately appreciated.  I will love you long time, and give you 7,000,000,000 Scott Pilgrim brand internets as a reward for helping me defeat Gideon.  I just hope you picked bootloader proficiency back in the 5th grade.

Thanks,
Yankee14

---

### Post by psusi on 2010-11-10
The only thing you did wrong the first time was choosing to install grub to the partition, rather than the whole disk.  The MBR holds the partition table, and the very first part of the boot loader that the PC runs.  There are other parts to the boot loader, but that is the first.  When you chose to install grub to the partition, you left the MBR devoid of any boot code.

/boot is where your kernel(s) go(es), as well as grubs add on modules and config file.  There is no reason to give it its own partition, especially not one as large as 11 gb.  Your typical install only has 2 partitions: one for / and one for swap.

---

### Post by Yankee14 on 2010-11-10
Thanks for the quick response.  That helps to clarify my misunderstanding.

As for the image showing someone installing /boot to its own 11GB partition:

> Before viewing, please know that this is not the representation of my  hard drive. It is merely a screencap of some random persons desired  partition table which can clearly illustrate my question about  bootloader-ing.

I know not to put that on its own 11GB partition :D

Thanks for the response.  I think I may now know enough to give this a shot.

Regards,
Yankee

---

### Post by oldfred on 2010-11-10
PC's since IBM's original boot from a BIOS or the first screen you see on power up. The BIOS is just smart enough to know to jump to another device (then a floppy drive) to boot. When hard drives were added they allowed 4 and the only boot drive was the primary master's MBR. The MBR is before the first partition. Windows, lilo and only optionally with grub parts of the boot process can be installed to the partition boot sector which is the beginning of each partition. 
Newer systems are only a little smarter, BIOS will with SATA let you choose which drive to boot but still from MBR of that drive. Apple and some very new systems are conveting from BIOS to EFI or UEFi which has even more capability.

While showing only windows this explains the windows process in detail but the pictures are easy of review.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If you install grub2 to a partition you do not get the parts in /etc.

 GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

---

### Post by Yankee14 on 2010-11-11
Thanks for the help.  I appreciate it.

Regards,
Yankee14

---

### Post by oldfred on 2010-11-11
Your Disk BOOT error looks something more like a BIOS error. There are a few (mostly intel motherboards) BIOS that require a boot flag on a primary partition to let you boot. Grub does not use  a boot flag but windows does, so the BIOS was designed to only let windows boot. You can add a boot flag to any primary partition with gparted it that is the problem.

---

