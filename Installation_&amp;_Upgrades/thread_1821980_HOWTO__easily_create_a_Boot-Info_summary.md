---
title: "HOWTO : easily create a Boot-Info summary"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by YannBuntu on 2011-08-09
[B][COLOR="DarkRed"]Help on this topic has been moved to the following Ubuntu Community document: 

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

The following thread was created for discussion of the contents of the community document:

[Discussion - https://help.ubuntu.com/community/Boot-Info]("http://ubuntuforums.org/showthread.php?t=2023420")


If you need help, support threads/questions should be posted in normal forums.
[/COLOR][/B]
--- 

I made a little GUI to do it very easily:

1) Boot on Ubuntu live-CD or live-USB. (or [Boot-Repair-Disk]("https://sourceforge.net/projects/boot-repair-cd/files/") which will lead you automatically to step 4)
2) Connect internet
3) Open a terminal and type :
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

4) Click on "Create a BootInfo summary":
[[img]http://pix.toile-libre.org/upload/original/1335260967.png[/img]](http://pix.toile-libre.org/upload/original/1335260967.png)
5) Done ! 

[[img]http://pix.toile-libre.org/upload/original/1335261480.png[/img]](http://pix.toile-libre.org/upload/original/1335261480.png)

Now just indicate your URL (http:......) to people who help you on this forum.

---

### Post by oldfred on 2011-08-10
@YannBuntu
I tried you script but my system is a bit complex with 3 drives and several Ubuntus & XP.
It did not just run boot script but did its full analysis of system and I found it running this:

About 8000 entries like this in boot-repair.log.tee file before I killed it.
SET@_progressbar1.pulse()

****************DEBUG LOG OF boot-repair 2011-08-09__22:53****************
boot-repair version : 2.7-0ppa27~maverick
clean-ubiquity-common version : 2.7-0ppa6~maverick
boot-repair-common version : 2.7-0ppa26~maverick

I am not sure what it was checking but if I just want script it should run fairly quick if you want to use it.

---

### Post by YannBuntu on 2011-08-10
> **oldfred said:**
> I tried you script but my system is a bit complex with 3 drives and several Ubuntus & XP.

No problem, it worked with much more complex systems ;)

Please can you send me by email your boot-repair.log.tee file ? ( yannubuntu ATT gmail DOTcom)

---

### Post by YannBuntu on 2011-08-17
**@all :** if you have the same problem as oldfred, just install the "pastebinit" package before running Boot-Repair.

---

### Post by mikitz on 2011-08-18
Hi there YannBuntu and others,

I have a new Asus 1215b that came with Win7, I used the 11.04 livecd to create a dual boot. There is a separate boot partition for grub on sda5 and the Ubuntu o/s is on sda7.

 Upon boot, the win7 mbr comes up with ubuntu and windows options, windows loads fine... but ubuntu hangs at the grub command line! I investigated and could not find a device.map file for grub anywhere and grub doesn't seem to generate one for me.

Here is my boot-repair output [http://paste.ubuntu.com/669390/](http://paste.ubuntu.com/669390/)
Any help would be greatly appreciated!

---

### Post by oldfred on 2011-08-18
YannBuntu,

Just so everyone knows it runs just fine on my system. I even tried uninstalling pastebinit and it still runs. It looks like you reinstall if it is missing with your latest version of your script. Good program 

@mikitz

You have syslinux installed to the MBR, not grub. And it looks like your windows partition needs chkdsk or other repairs. After resize it wants to run chkdsk to fix issues from the resize and Linux will not mount a NTFS partition with the chkdsk flag set to prevent damage that chkdsk may then not be able to fix.

#If separate /boot
$ sudo mount /dev/sda7 /mnt
$ sudo mount /dev/sda5 /mnt/boot
$ sudo grub-install --boot-directory=/mnt/boot /dev/sda


Be sure to include the mount of your /boot as that is often just a footnote as most desktops do not have a separate /boot.
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Hakunka-Matata on 2011-08-18
@YannBuntu

It worked on this 11.04 - 64 bit Desktop OS for me.  RESULTS.txt included - Thanks

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    40,962,047    40,961,985   7 NTFS / exFAT / HPFS
/dev/sda2         122,886,142   156,301,311    33,415,170   5 Extended
/dev/sda5         152,207,360   156,301,311     4,093,952  82 Linux swap / Solaris
/dev/sda6         122,886,144   152,205,311    29,319,168  83 Linux
/dev/sda3          40,962,048   122,882,047    81,920,000  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3E70A89B70A85B81                       ntfs       
/dev/sda3        44d39709-6b44-4f74-b18d-59cdb61e5ef9   ext4       HOMEDATA
/dev/sda5        29fdb798-7952-4ebd-84bf-868f8f6a5a32   swap       
/dev/sda6        05ba506d-cf31-431c-956c-1b6fea39208b   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /home                    ext4       (rw,nosuid,nodev,commit=0)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /usepmtimer 
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 05ba506d-cf31-431c-956c-1b6fea39208b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 05ba506d-cf31-431c-956c-1b6fea39208b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 05ba506d-cf31-431c-956c-1b6fea39208b
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=05ba506d-cf31-431c-956c-1b6fea39208b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 05ba506d-cf31-431c-956c-1b6fea39208b
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=05ba506d-cf31-431c-956c-1b6fea39208b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 05ba506d-cf31-431c-956c-1b6fea39208b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=05ba506d-cf31-431c-956c-1b6fea39208b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 05ba506d-cf31-431c-956c-1b6fea39208b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=05ba506d-cf31-431c-956c-1b6fea39208b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 05ba506d-cf31-431c-956c-1b6fea39208b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 05ba506d-cf31-431c-956c-1b6fea39208b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3E70A89B70A85B81
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=05ba506d-cf31-431c-956c-1b6fea39208b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=29fdb798-7952-4ebd-84bf-868f8f6a5a32 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=44d39709-6b44-4f74-b18d-59cdb61e5ef9   /home    ext4          nodev,nosuid       0       2 
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  68.937110901 = 74.020659200   boot/grub/core.img                             1
  63.099514008 = 67.752587264   boot/grub/grub.cfg                             1
  71.370597839 = 76.633595904   boot/initrd.img-2.6.38-10-generic              2
  61.476100922 = 66.009460736   boot/initrd.img-2.6.38-8-generic               1
  61.585273743 = 66.126684160   boot/vmlinuz-2.6.38-10-generic                 2
  68.935382843 = 74.018803712   boot/vmlinuz-2.6.38-8-generic                  1
  71.370597839 = 76.633595904   initrd.img                                     2
  61.476100922 = 66.009460736   initrd.img.old                                 1
  61.585273743 = 66.126684160   vmlinuz                                        2
  68.935382843 = 74.018803712   vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by YannBuntu on 2011-08-18
**@oldfred :** Boot-Repair now manages separate /boot partitions, no need for command lines any more ;)

[[img]http://pix.toile-libre.org/upload/img/1313715508.png[/img]](http://pix.toile-libre.org/?img=1313715508.png)

(where do you see the chkdsk flag? is it something you guess from the "Mounting failed" ?)


**@Hakunka-Matata :** thanks for the feedback.

---

### Post by oldfred on 2011-08-18
It is just a guess when ever a partition does not mount. If it is NTFS or FAT then chkdsk is probably the fix, if it is in the ext family then e2fsck should be run. Generally partition/file repair will not cause further problems, but files that have issues may be moved to separate folders.

---

### Post by YannBuntu on 2011-08-19
ok thanks. For information, the "Repair filesystems" option in Boot-Repair uses ntfsfix on NTFS partitions (and fsck on others) , so it won't do the Windows chkdsk job but will help by forcing chkdsk on next Windows boot. If you know a better ntfs repair tool that I could include don't hesitate to tell me ;)

---

### Post by mikitz on 2011-08-19
Thank YannBuntu for the easy to use utility for those of us not comfortable with grub on our own. oldfred, I just needed to install grub to the right partition.. the 3 lines of code you posted were all that was needed. Thanks so much!

---

### Post by YannBuntu on 2011-08-23
Happy it helps :)

@all: the project is young, so if you have 5 minutes please help translating in your language !
[https://translations.launchpad.net/boot-repair/trunk](https://translations.launchpad.net/boot-repair/trunk)

---

### Post by Quackers on 2011-08-23
Very nice programme :-)
Works a treat for my Oneiric/grub 1.99 system and it's a lot easier than going to the website, downloading, running etc etc etc.

---

### Post by YannBuntu on 2011-09-04
Hello,

I slightly simplified the interface, so that it becomes even faster : just one click !!!

[[img]http://pix.toile-libre.org/upload/img/1315190606.png[/img]](http://pix.toile-libre.org/?img=1315190606.png)

---

### Post by YannBuntu on 2012-02-06
Dear all,

after discussion with Gert, i have set the last BootInfoScript GIT version as default in Boot-Repair.
Currently no regression from the current stable BIS, but several improvements, especially concerning EFI detection.

This will also help us improving BIS.

---

### Post by YannBuntu on 2012-02-29
Updated with Gert's last GIT version.

---

### Post by YannBuntu on 2012-03-16
Just improved Boot-Repair's log so that it displays GRUB conf files.
This can be useful, eg to detect DISABLE_OS_PROBER...

---

### Post by blackhill on 2012-06-19
Humble appologises

I realised too late that the question asked about sdb referred to my second hard disk and not the  USB stick as I first  thought

The correct output from boot-repair script is at
http//paste.ubuntu.com/1049695

---

### Post by YannBuntu on 2012-06-20
@Blackhill: we will answer on your thread ( [http://ubuntuforums.org/showthread.php?t=2002963&page=3](http://ubuntuforums.org/showthread.php?t=2002963&page=3) )

---

### Post by YannBuntu on 2012-07-12
**@all:** I just moved the HOWTO to the Ubuntu Wiki. From now, please refer to: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

**@Fred or any forum admin:** please could you replace the content of my post#1 by a big warning saying :

> This thread is for any question/comment about this tutorial: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

This is not a thread for support, **if you need help please create your new own thread [here]("http://ubuntuforums.org/newthread.php?do=newthread&f=333").**

---

### Post by drs305 on 2012-07-12
> **YannBuntu said:**
> **@all:** I just moved the HOWTO to the Ubuntu Wiki. From now, please refer to: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

**@Fred or any forum admin:** please could you replace the content of my post#1 by a big warning saying :

Thanks for migrating this to the wiki.

I've added a note in the first post. If you'd like the formatting or wording changed just let me know.

---

### Post by YannBuntu on 2012-07-12
Thanks. Please remove the old content under the note. And add the link on the "here" word.

---

### Post by YannBuntu on 2012-07-12
Thread moved to [http://ubuntuforums.org/showthread.php?t=2023420](http://ubuntuforums.org/showthread.php?t=2023420)

---

### Post by drs305 on 2012-07-12
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2023420](http://ubuntuforums.org/showthread.php?t=2023420)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

