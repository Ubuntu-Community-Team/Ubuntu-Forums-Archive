---
title: "Dual boot failed - user needs reboot"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by yuler on 2010-11-03
My plan is to dual-boot Ubuntu 10.10 and XP, but I must have done something wrong when manually installing Ubuntu into pre-defined partitions made with Gparted.  The Ubuntu text boot screen displays a few lines, then the system halts.  No software reboot can occur.

I'd read that Windows is easiest installed first, and a dedicated boot partition was best to avoid OS lockout, so I created these partitions:

sda1 XP (2gb)
sda2 bootloader (11mb)
sda5 ubuntu
sda6 winapps
sda7 audio
sda8 general data
sda9 secure
sda10 unallocated

My plan was to put the Linux swap on sda9 for the moment, then point it to sdb1 (yet to be installed) after it's running.

During the Ubuntu install procedure, I chose sda2 as /boot - which I assumed is the bootloader and would auto detect XP on sda1.  I'm not sure if I assumed right, as the bootloader shows Ubuntu and XP, but as already stated, Ubuntu fails after a few lines of boot text.

Using the LiveCD, my hope was to find a log file of the boot process to help debug, but I was unable to find one in /var/log.   Rather than pester the forums for specific help, I trotted around to find clues.  In the process, I discovered [boot_info_script]("http://bootinfoscript.sourceforge.net/") and managed to run it.  I was baffled to see Linux swap on sda6 AND sda11 (which I didn't think was assigned).

I also read that Ubuntu parts could be stored in several places.  I'd like my (one user) data to be stored on sda8 (general data).  I assume I missed that on the manual partition installation.

Is this easiest repaired or should I wipe the partitions and start over?

I'd love to repair it so I can learn how and why the Linux OS works.  I've read the online Wiki, scoured the forums, read the PDF manual, but I'm either brain dense or there is information missing.  Any one care to suggest a remedy, aside from a user reboot?

 ```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

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

/dev/sda1    *         24,576     4,218,879     4,194,304   7 HPFS/NTFS
/dev/sda2               2,048        24,575        22,528  83 Linux
/dev/sda3           4,220,926   976,773,119   972,552,194   5 Extended
/dev/sda5           4,220,928    67,135,487    62,914,560  83 Linux
/dev/sda6          67,137,536   119,566,335    52,428,800  82 Linux swap / Solaris
/dev/sda7         119,568,384   329,283,583   209,715,200   7 HPFS/NTFS
/dev/sda8         329,285,632   434,143,231   104,857,600   7 HPFS/NTFS
/dev/sda9         434,145,280   643,860,479   209,715,200   7 HPFS/NTFS
/dev/sda10        643,862,528   767,057,919   123,195,392  82 Linux swap / Solaris
/dev/sda11        767,059,968   976,773,119   209,713,152   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       ef1abebf-8af9-4642-acc8-502286785770   swap                                     
/dev/sda11       372BEC693358883C                       ntfs       backup                        
/dev/sda1        A8D4B8BCD4B88E56                       ntfs       xp                            
/dev/sda2        9dd2845c-04c4-43df-a99f-088edf6bc2c1   ext4       boot                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        22672a0a-841e-4f93-bb46-eecda829da30   ext4       ubuntu                        
/dev/sda6        6169D9721131CAB2                       ntfs       winapps                       
/dev/sda7        474FFAF25A21D641                       ntfs       audio                         
/dev/sda8        5AE3AB3457AE7051                       ntfs       general                       
/dev/sda9        77A0E81F12D7963B                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda9        /media/77A0E81F12D7963B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/apt               iso9660    (ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

============================= sda2/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 22672a0a-841e-4f93-bb46-eecda829da30
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a8d4b8bcd4b88e56
    drivemap -s (hd0) ${root}
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

=================== sda2: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=22672a0a-841e-4f93-bb46-eecda829da30 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=9dd2845c-04c4-43df-a99f-088edf6bc2c1 /boot           ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=ef1abebf-8af9-4642-acc8-502286785770 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   4.4GB: boot/initrd.img-2.6.35-22-generic.new
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
000001b0  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 00 bc  |................|
000001c0  77 06 83 fe ff ff 02 00  00 00 00 00 c0 03 00 fe  |w...............|
000001d0  ff ff 05 fe ff ff 95 00  c0 03 6d 07 20 03 00 00  |..........m. ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Quackers on 2010-11-03
That's a very complicated set up for a first try.
According to the boot script 2 of your Ubuntu boot files are in sda2, but the 3rd one (etc/fstab) is in sda5, which is designated as your Ubuntu root (/) partition. I don't know whether that can work or not. I haven't seen it done. 
Did Windows boot? Not sure if it will now without fixing the mbr.
I would have one Windows partition and for Ubuntu a root (/) partition and a /home partition and try again. You could leave spaces in the partition table for the creation of other partitions later.
Also the Windows partition needs to be a primary partition whereas the Ubuntu partitions can be logical.
These are just my own views, you understand :-)

BTW welcome to Ubuntu :-)

---

### Post by oldfred on 2010-11-04
Please post result.txt in code tags (#), not quotes.

I do not recommend /boot partitions for standard desktops. Servers, RAID, LVM partitions may have need for a separate /boot.

Any grub2 reinstall instructions your find may not include the additional mount of the /boot. Some have a footnote saying you also have to mount the /boot partition when reinstalling grub2. 

Your /boot is not complete and you seem to have part of it in your root?
Your are missing vmlinuz -xx and the two link files that refer to the most recent kernel & vmlinuz.

Did you use manual install? That is where you choose which partitions to use & what format. It autofinds swap. If you use any of the other installs it shrinks a partition and creates new / & swap. It does not give a option to mount the data partition(s), but you can do that afterwards.

I now see Quackers beat me to it. I tend to like to repair, but we sometimes spend days fixing things and a new install is only about an hour. So if you have no data to recover a new install may be best. Are partitions still set up the way you want. If not adjust before installing & use manual install.

---

### Post by Quackers on 2010-11-04
Forget what I said :-) Listen to oldfred. He has forgotten more about partitioning than I'll ever know!

---

### Post by oldfred on 2010-11-04
Thanks, but I only admit I have forgotten it all. Any help at this point is appreciated.

But a link to show manual install with some partitioning. I still like to use gparted in advance of the install. But I have also chosen the wrong partition when I installed a new drive. I had create a lot of partitions and put my install in my planned data partition. I had not copied data, so I just had to go back and relabel and tweak sizes. (I now keep manual notes on which partition is which, or hard copy printouts of fstab or blkid)

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

---

### Post by yuler on 2010-11-05
Thanks for the replies.  I'm familiar with partitioning, cluster size,  and platter location strategies, so it was not a stretch to extend it to  Linux.  This was my intended partition strategy:

 sda1 XP (2gb)
  sda2 bootloader (11mb)
  sda5 ubuntu
  sda6 winapps
  sda7 audio
  sda8 general data
  sda9 secure
  sda10 unallocated
swap on sda9, until OS is running and sdb is installed.

The problem is that I'm unfamiliar with Linux's layout.  After many  failed attempts at loading Linux packages in the past (mostly due to  using proprietary laptops), I figured it was time with Ubuntu v10.10 on a  standard desktop.

I didn't choose an automated install because I wanted control over which  partitions were assigned data, so I chose a manual install.  The first  step was installing XP on sda2.

My guess as to why the boot partition is split is because I thought boot  partition meant bootloader, when it actually means OS boot files  (kernel), so I put /boot on sda2 (MBR partition).  Not knowing  specificlly, I don't think 11mb is enough room for kernel files.

Since sda9 was 100gb and was to be a temporarily swap location, I assume  the installer saw that as too much space and divided it, creating  another partition (sda11).

Even though Ububtu failed, I decided to try XP from the GRUB menu per your request.  It failed.

Figuring the pointers were wrong and assuming Ubuntu could fix it if I  set the parameters right, I reinstalled Ubuntu using manual allcocation.

sda2: do not use 
sda5: format as ext4, mount as /
bootloader: sda2

After restart, there was some boot text, the CD kicked out, and a screen full of errors:

```

squashFS error: unable to read fragment cache entry e40156
squashFS error: unable to read page, block e40156a, size 1cfff
.
.
end request: I/O error, dev sr0m sector 533096
.
.
plymouth post-start process (32390) terminated with status 2
unexpectedly disconnected fron boot system daemon
.
.
plymouth post-start process (32390) terminated with status 1
end request

```Not knowing what else to do, I pulled the CD out and reboot.  The GRUB  menu came up with Ubuntu and XP.  XP failed to load.  Reboot.  Ubuntu,  with more errors:

```

[0.544686] kernel panic - not syncing: VFS : unable to mount root FS on unknown block (0,0)
[0.544756] Pid: 1, comm: swapper not tainted 2.6.35-22-generic #33-Ubuntu
[0.544818] Call Trace:
[0.544882]
[<c05c6468>] ? printk+0x2d/0x35
[<c05c6468>] panic+...
[<c05c6468>] mount_block_root+...
[<c05c6468>] ? sys_mkmod+...
[<c05c6468>] mount_root+...
[<c05c6468>] prepare namespace+...
[<c05c6468>] sys_acces+...
[<c05c6468>] kernel_int+...
[<c05c6468>] ? kernel_init+...
[<c05c6468>] kernel_thread_helper+...

```That's where it stopped, keyboard indicator lights blinking.  No soft  boot allowed.  Had to hard reboot into the LiveCD, which is where I'm at  now.

Apparently, I still don't understand Linux's layout.  What options do I choose if I want:

bootloader on sda2 (11mb)
Ubuntu on sda5
swap on sda9

I found I could not set /home to NTFS, FAT, or FAT32, so I'll just have  to accept it as sda5 (with the rest of the Ubuntu files) for now and  change it later.

---

### Post by wilee-nilee on 2010-11-05
I would just say here since you are obviously experienced, loading the bootloader whether MS or grub or any to the HD mbr to boot is easy. The boot partition is not needed the regular mbr the first 512Mib of the HD is fine, you have heard inaccurate descriptions of dual booting problems cross distros. 

As was mentioned you where missing files in the original script, and you have messed around so generally we ask to see another script if things are different.

If it was me I would reload the MS bootloader to the HD mbr to confirm XP runs, you know the drill I suspect, fixmbr from the XP install disc repair command line.

I would then just reinstall Ubuntu to the partition you want it in and let grub go to the mbr at the front of the disc. Get rid of the boot partition it is not needed.

---

### Post by oldfred on 2010-11-05
You may be mixing up /boot partition which is where the kernel & grub are and the boot loader which is installed in the MBR. BIOS only boots from the MBR. If you install the part of grub that goes into the MBR into a partition it is considered less reliable. Also if you install to a windows partition it corrupts windows as windows has to have the second part of its boot loader in the PBR or partition boot sector. Grub does not normally use the PBR.

---

### Post by yuler on 2010-11-07
Thanks again.  I ran the script again and compared it with the old, but I'm not at the machine at the moment to paste it.  However, I can tell you what I did in the interim:

1) Booted to XP CD, ran fixmbr.  Reboot.  No OS.
2) Booted to XP CD, ran fixboot.  Reboot.  No OS.
3) Booted to Hiren's Boot CD, ran GRUB2 entry:

```

title ³ Boot from Hard Drive - Windows XP (NTLDR)        ³\n
find --set-root --ignore-floppies --ignore-cd /ntldr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /ntldr
chainloader /ntldr
savedefault --wait=2

```XP booted.  

4) Booted into Ubuntu LiveCD.  Compared sda2 (the boot partition) to sda5/boot (Ubuntu).  The files are exactly the same (GRUB2, etc).

5) Booted to Hiren's Boot CD to launch the boot partition.  Ran GRUB2 entry:
```

title Boot HDD 1 Partition 2\n
rootnoverify (hd0,1)
chainloader +1

```That was intended for sda2 (boot partition).  No OS.

I don't recall if I ran Hiren's Boot CD GRUB2 menu to launch sda5 (Ubuntu).

6) Ran Hiren's Boot CD > MBR utils > MBRwork to look at the MBR pointers.  

[LIST]
[*]Partition 0 (sda1) pointed to the CHS/LBA corrosponding to the XP partition.
[*]Partition 1 (sda2) pointed to the CHS/LBA corrosponding to the boot partition (starting at sector 2048, I believe).
[*]Partition 2 (sda5) pointed to the CHS/LBA corrosponding to the Ubuntu partition
[/LIST]
Taking a cue from the [UbuntuGuide Multiple OS Installation]("http://ubuntuguide.org/wiki/Multiple_OS_Installation"), my intention is to use the "boot partition" (sda2) as a master bootloader.   I don't want the master bootloader inside the Ubuntu /boot folder, which is what I suspect the default setttings do.  If I decide to wipe the Ubuntu partition, I won't be able to get into XP.  Further, I may decide to have partitions for current and previous versions of Ubuntu, or try out other flavors of Ubuntu.  In short, I want the boot path to look like:

MBR > boot partition with GRUB2 > branch to OS's, other options

---

### Post by oldfred on 2010-11-07
You can do what you what and I did have a dedicated grub partition with grub legacy. But  If you do that you have to manually edit all grub stanzas. If you understand grub that is not impossible, but many versions want grub2 installed to a PBR so you can chainboot.

Grub2 has an osprober that is very good at finding other systems and setting up the boot stanza. Since grub2 I rarely use my grub partiiton. If I install another system, I decide which I want in charge and either update the MBR or not. When I reboot the system in charge I can run sudo update-grub and it finds the new system.

A boot stanza that boots a partition not the specific system. Ubuntu puts links in / that link to the newest kernel & initrd.

Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest boatable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
grub-setup -v /dev/sda6
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force

Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)


Grub2 with chainboot examples
[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0)

---

### Post by yuler on 2010-11-09
Here is the boot script, generated after the last Ubuntu format/reinstall.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 12880720 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

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

/dev/sda1    *         24,576     4,218,879     4,194,304   7 HPFS/NTFS
/dev/sda2               2,048        24,575        22,528  83 Linux
/dev/sda3           4,220,926   976,773,119   972,552,194   5 Extended
/dev/sda5           4,220,928    67,135,487    62,914,560  83 Linux
/dev/sda6          67,137,536   119,566,335    52,428,800  82 Linux swap / Solaris
/dev/sda7         119,568,384   329,283,583   209,715,200   7 HPFS/NTFS
/dev/sda8         329,285,632   434,143,231   104,857,600   7 HPFS/NTFS
/dev/sda9         434,145,280   643,860,479   209,715,200   7 HPFS/NTFS
/dev/sda10        643,862,528   767,057,919   123,195,392  82 Linux swap / Solaris
/dev/sda11        767,059,968   976,773,119   209,713,152   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       ef1abebf-8af9-4642-acc8-502286785770   swap                                     
/dev/sda11       372BEC693358883C                       ntfs       backup                        
/dev/sda1        A8D4B8BCD4B88E56                       ntfs       xp                            
/dev/sda2        9dd2845c-04c4-43df-a99f-088edf6bc2c1   ext4       boot                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        9c828ded-432e-4028-b090-0659ac21aa19   ext4       ubuntu                        
/dev/sda6        6169D9721131CAB2                       ntfs       winapps                       
/dev/sda7        474FFAF25A21D641                       ntfs       audio                         
/dev/sda8        5AE3AB3457AE7051                       ntfs       general                       
/dev/sda9        77A0E81F12D7963B                       ntfs       secure                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

============================= sda2/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 22672a0a-841e-4f93-bb46-eecda829da30
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a8d4b8bcd4b88e56
    drivemap -s (hd0) ${root}
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

=================== sda2: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: vmlinuz-2.6.35-22-generic

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
search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a8d4b8bcd4b88e56
    drivemap -s (hd0) ${root}
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9c828ded-432e-4028-b090-0659ac21aa19 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=ef1abebf-8af9-4642-acc8-502286785770 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   6.5GB: boot/grub/core.img
  30.2GB: boot/grub/grub.cfg
  13.5GB: boot/initrd.img-2.6.35-22-generic
   2.5GB: boot/vmlinuz-2.6.35-22-generic
  13.5GB: initrd.img
   2.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
000001b0  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 00 bc  |................|
000001c0  77 06 83 fe ff ff 02 00  00 00 00 00 c0 03 00 fe  |w...............|
000001d0  ff ff 05 fe ff ff 95 00  c0 03 6d 07 20 03 00 00  |..........m. ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by yuler on 2010-11-09
> 
[]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition")Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.


Earlier, I said I wanted to make a "boot" partition, but I may have obscured my intention by using improper vernacular.  Boot partitions, from my understanding, are for Linux kernels.  This is NOT what I meant.  I want a GRUB2 partition that is handed control from the MBR.  In this GRUB2 partition, I want to launch the OS's.

Still learning the Linux layout and lingo...

---

### Post by efflandt on 2010-11-10
One thing nobody seems to have mentioned yet is that your partition order is mixed up.  sda1 is "after" sda2.  I do not know if that causes boot issues, but many people who have problems seem to have mixed up partitions.

But if you leave things like they are for now, grub2 is currently on sda2, so try running gparted and **mark /dev/sda2** as the **boot** partition.  Ignore the "core.img can not be found at this location." (boot info script always says that when grub is on a partition).  Then the standard Windows mbr should boot grub on sda2.  But if that does not work your may need to run grub-install on /dev/sda2 but mount /dev/sda5 somewhere to point to for the rest of grub files so it boots /dev/sda5.  I don't know if grub would work simply installed to sda5 because I don't know if the Windows mbr can boot a logical partition.

if that boots Ubuntu, then run **sudo update-grub**, see if that comes up with errors, or if you are then able to boot Ubuntu and Windows.

---

### Post by yuler on 2010-11-10
> **efflandt said:**
> One thing nobody seems to have mentioned yet is that your partition order is mixed up.  sda1 is "after" sda2.  I do not know if that causes boot issues, but many people who have problems seem to have mixed up partitions.

Thank you, efflandt.  

The hard drive was originally partitioned for XP in a primary  partition (sda1), and with the remaining partitions as logical.  It was only afterward that I realized I wanted a grub/boot partition, so I shrunk sda1 by 11mb, made a primary partition from it, which moved the XP sda1 to sda2 and the grub/boot 11mb as sda2.

> But if you leave things like they are for now, grub2 is currently on sda2, so try running gparted and **mark /dev/sda2** as the **boot** partition.

When I go to system > admin > disk util > hard drive > sda2 and mark it as bootable, the busy circle sits there.  Since it was unmounted, I tried to mount it, but it said it was busy.  Although there is likely a way to end the process, I do not know how to do that.  Should I just reboot into the LiveCD again and mount it first before marking it bootable?  Or is there something else going on?

---

### Post by oldfred on 2010-11-10
Besides Disk Utility, you can use gparted, right click on partition & manage flags, Disk Utility, or command line:
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
OR:
    #make a partition active ("makeactive" in grub legacy)
    parttool (hd0,4) boot+

    #remove active flag from a partition
    parttool (hd0,3) boot-

Partition editing is best from liveCD but I have changed boot flags from working systems, just not sure if partition was mounted or not. Not mounted is always better, & that is why liveCD works better.

If you have proven your windows boots ok, then I would still install grub2 to the MBR and sda2, then you can manually create your grub.cfg with windows and Ubuntu boot stanzas.

After installing grub2 to sda2 & the MBR this should work as your grub.cfg. Double check that I have your correct UUID for windows.

```
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set A8D4B8BCD4B88E56
    drivemap -s (hd0) ${root}
    chainloader +1
}


menuentry "Ubuntu on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img


menuentry "Reboot" {
    reboot
}


```

---

### Post by yuler on 2010-11-10
[LEFT]> **oldfred said:**
> Besides Disk Utility, you can use gparted, right click on partition & manage flags, Disk Utility, or command line:
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda


Upon scouring the forums, I realized I could use Gparted and successfully changed the boot flag.  However, reboot resulted in the "No OS" error, so I booted back to LiveCD, loaded Gparted, and changed it back.  Over time, I'll become more familiar with the CLI commands.

Incidentally, there was a crash report available after attempting to change the boot flag with system > admin > disk util, but it could not load.  I suspect it timed out, but I'll never know.

I'll try to reinstall grub2 to sda2 per your instructions and report back with results.  Thanks for being patient.
[/LEFT]

---

### Post by yuler on 2010-11-10
> If you have proven your windows boots ok, then I would still install grub2 to the MBR and sda2Yes, the XP partition (sda1) can be booted with the right grub2 settings, which was launched from Hiren's Boot CD.  It had a GRUB2 entry to boot NTLDR.

I tried this:
```
ubuntu@ubuntu:~$ grub-setup -v sda2
```and got this:
```
grub-setup: info: cannot open `/boot/grub/device.map'.
Invalid device `sda2'.
Try `grub-setup --help' for more information.
```So I tried:
```
ubuntu@ubuntu:~$ grub-setup --help
```and noticed this:
```
Usage: grub-setup [OPTION]... DEVICE
Set up images to boot from DEVICE.
DEVICE must be a GRUB device (e.g. `(hd0,1)').
You should not normally run grub-setup directly.  **Use grub-install instead.**
```So I did:
```
ubuntu@ubuntu:~$ grub-install -v sda2.
```and got this:
```
grub-install (GRUB) 1.98+20100804-5ubuntu3.
```I didn't notice any change in the files or flags on sda2.  Did I do that correctly?

---

### Post by oldfred on 2010-11-10
Grub does not use the boot flag. Windows does. About the  only way to see what is installed in MBR or partition boot sectors is to run the boot info script.

---

### Post by yuler on 2010-11-11
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 12880720 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

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

/dev/sda1    *         24,576     4,218,879     4,194,304   7 HPFS/NTFS
/dev/sda2               2,048        24,575        22,528  83 Linux
/dev/sda3           4,220,926   976,773,119   972,552,194   5 Extended
/dev/sda5           4,220,928    67,135,487    62,914,560  83 Linux
/dev/sda6          67,137,536   119,566,335    52,428,800  82 Linux swap / Solaris
/dev/sda7         119,568,384   329,283,583   209,715,200   7 HPFS/NTFS
/dev/sda8         329,285,632   434,143,231   104,857,600   7 HPFS/NTFS
/dev/sda9         434,145,280   643,860,479   209,715,200   7 HPFS/NTFS
/dev/sda10        643,862,528   767,057,919   123,195,392  82 Linux swap / Solaris
/dev/sda11        767,059,968   976,773,119   209,713,152   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       ef1abebf-8af9-4642-acc8-502286785770   swap                                     
/dev/sda11       372BEC693358883C                       ntfs       backup                        
/dev/sda1        A8D4B8BCD4B88E56                       ntfs       xp                            
/dev/sda2        9dd2845c-04c4-43df-a99f-088edf6bc2c1   ext4       boot                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        9c828ded-432e-4028-b090-0659ac21aa19   ext4       ubuntu                        
/dev/sda6        6169D9721131CAB2                       ntfs       winapps                       
/dev/sda7        474FFAF25A21D641                       ntfs       audio                         
/dev/sda8        5AE3AB3457AE7051                       ntfs       general                       
/dev/sda9        77A0E81F12D7963B                       ntfs       secure                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/boot              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/ubuntu            ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

============================= sda2/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 22672a0a-841e-4f93-bb46-eecda829da30
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9dd2845c-04c4-43df-a99f-088edf6bc2c1
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a8d4b8bcd4b88e56
    drivemap -s (hd0) ${root}
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

=================== sda2: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: vmlinuz-2.6.35-22-generic

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
search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a8d4b8bcd4b88e56
    drivemap -s (hd0) ${root}
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9c828ded-432e-4028-b090-0659ac21aa19 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=ef1abebf-8af9-4642-acc8-502286785770 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   6.5GB: boot/grub/core.img
  30.2GB: boot/grub/grub.cfg
  13.5GB: boot/initrd.img-2.6.35-22-generic
   2.5GB: boot/vmlinuz-2.6.35-22-generic
  13.5GB: initrd.img
   2.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
000001b0  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 00 bc  |................|
000001c0  77 06 83 fe ff ff 02 00  00 00 00 00 c0 03 00 fe  |w...............|
000001d0  ff ff 05 fe ff ff 95 00  c0 03 6d 07 20 03 00 00  |..........m. ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

Unless I am seeing this wrong, it appears I did not install GRUB2 into the MBR.

[FONT=monospace]```
[/FONT]=> Windows is installed in the MBR of /dev/sda
```

That means grub-install -v sda2 did not work, so I tried:

```

ubuntu@ubuntu:~$ sudo grub-install sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

```

OK, so I can't install into sda.  What do I type to install grub2 into the MBR?

---

### Post by wkhasintha on 2010-11-11
You may be mixing up /boot partition which is where the kernel & grub are and the boot loader which is installed in the MBR. BIOS only boots from the MBR. If you install the part of grub that goes into the MBR into a partition it is considered less reliable. Also if you install to a windows partition it corrupts windows as windows has to have the second part of its boot loader in the PBR or partition boot sector. Grub does not normally use the PBR.

---

### Post by yuler on 2010-11-11
> **wkhasintha said:**
> You may be mixing up /boot partition which is where the kernel & grub are and the boot loader which is installed in the MBR. BIOS only boots from the MBR. If you install the part of grub that goes into the MBR into a partition it is considered less reliable. Also if you install to a windows partition it corrupts windows as windows has to have the second part of its boot loader in the PBR or partition boot sector. Grub does not normally use the PBR.

I realise you are quoting Oldfred, but unfortunately, it does not help me understand what exactly I must do to install GRUB2 into the MBR.

---

### Post by yuler on 2010-11-11
From [Herman's Illustrated MBR page,]("http://members.iinet.net.au/%7Eherman546/p6.html") I've dumped the MBR to console.

```

ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 | hexdump -C

00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  8d f5 8d f5 00 00 80 87  |.....,Dc........|
000001c0  07 01 07 9c 56 06 00 60  00 00 00 00 40 00 00 20  |....V..`....@.. |
000001d0  21 00 83 87 06 01 00 08  00 00 00 58 00 00 00 bc  |!..........X....|
000001e0  75 06 05 fe ff ff fe 67  40 00 02 f8 f7 39 00 00  |u......g@....9..|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00075281 s, 680 kB/s

```

[quote="Herman"]
**Boot Loader Code Area**
The MBR consists of 512 bytes of data, and the first 446 bytes of the MBR, (the lines between 00000000 and 000001b0) that look like this, 'eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00', may contain code for the bootloader if you have one installed. This code is essentially for pointing the BIOS to some other location in a hard disk where it should find more code for a boot loader. If no boot loader has code written in this area, it can be empty or contain garbage.  If there is no bootloader code in the MBR, the BIOS will go to boot sector of the active partition, (whichever partition is marked with the  'boot flag' in the partition table).[/quote]

Looking at the lines between 00000000 and 000001b0), in particular 00000120-00000170, it appears there is no boot loader code.

```

00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|

```

So, the final question is - how to I install GRUB2 into the MBR?

---

### Post by wilee-nilee on 2010-11-11
n

---

### Post by oldfred on 2010-11-11
You cannot just say to install grub unless you are already booted in Ubuntu as it has to know which partition grub is in. If booted it knows, but when using liveCD you have to mount the partition with grub so it can use that. I have grub in several partitions so I have to be specific.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

If you are using a boot partition in sda2 you also have to mount it. But now your install in sda5 looks complete?

If separate /boot
$ sudo mount /dev/sda5 /mnt
$ sudo mount /dev/sda2 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

---

### Post by wkhasintha on 2010-11-11
> **yuler said:**
> I realise you are quoting Oldfred, but unfortunately, it does not help me understand what exactly I must do to install GRUB2 into the MBR.

sorry bro. I have know idea

---

### Post by yuler on 2010-11-12
> **oldfred said:**
> 
Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda


Hallelujah!  It actually booted from the hard drive.  ***Thank you!***

I am able to continue into Ubuntu from sda5, but I'm wondering - do I not want the MBR to pass control to sda2/boot/grub?  Having grub2 on a separate partition from the OS (XP/sda1, Ubu/sda5) was the reason for creating sda2.

Also noticed I cannot boot to XP from the grub2 menu.  However, sad5/boot/grub/grub.cfg is different than your suggested settings.  I thought I'd cut-n-paste, but accessing it through gedit doesn't work (read-only). I suspect the boot folder itself is root only.  I'll comb over the provided Windows boot links to see if I can get figure out how to edit it.

```

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
search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9c828ded-432e-4028-b090-0659ac21aa19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9c828ded-432e-4028-b090-0659ac21aa19
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a8d4b8bcd4b88e56
    drivemap -s (hd0) ${root}
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

```

---

### Post by oldfred on 2010-11-12
You are not using the grub partition to boot. I stopped using a separate grub partition once I learned how well grub2 works.

You do not edit grub.cfg in Ubuntu. If you have a grub.cfg in a grub partition or on a USB flash drive then you can only manual edit it as the automatic edits do not work. Then you have to know exactly what boot stanza to add.

If you want custom configurations in Ubuntu's grub.cfg you can use 40_custom.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

Does grub transfer boot to windows and it is a windows boot issue? All grub does is jump to the partition boot sector of the windows partition to boot windows. This is all the windows boot loader in the MBR does, so if windows is not booting, it is usually a windows issue not a grub issue.

---

