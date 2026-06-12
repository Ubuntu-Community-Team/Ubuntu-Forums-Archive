---
title: "GRUB2 and Boot Info Script results help."
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by rob34 on 2014-02-04
I'd like to understand a little (more) how GRUB2 works.
I've read the whole official manual, and a good number of posts in several forums, mainly in this ubuntuforum, some of them having a guide or basic guide or tutorial about GRUB2.

Any of these readings have cleared my doubts.
Perhaps my little knowledge of English didn't help, (I must to say that I haven't been able to understand all what I have read).

Anyway here I am, to see if someone can help me to understand **what GRUB2 has done with my system and what choices I have to leave it in a clearer way**.
Moreover, I've seen that most of GRUB2 relevant questions have been posted in this forum (Installation & Upgrades) but if someone think it's better to place it in another forum (even outside from ubuntuforums) I'll be glad to listen all suggestions and follow them if possible.
 
**My situation****:** nowadays I've connected only one HD (2TB) to my system.

I installed Debian 7 (yes I know, this is an Ubuntu forum, but I think my problem is with GRUB2, and I've seen here a lot of GRUB2 knowledge and nicely GRUB2 gurus, on the other hand Ubuntu was made from Debian, so I think maybe I could get some help anyway).

Partitions created are:

[LIST]
[*]sda1-> / with Debian installed (ext3) 
[*]sda2-> (swap) 
[*]sda3-> Extended partitios for /home and others GNU/linux OS 
[*]sda5-> /home for several GNU/linux OS, Debian 7initially, (ext4) 
[*]sda 4-> To contain Windows Vista data recovered from another HD (NTFS). This partition doesn't have any OS installed, only a image file of another computer HD for forensics and recuperation purposes. 
[/LIST]
 Later, after moving, shinrinkg, formatting, reinstalling... partitions and Debian 7, I made room into sda3 to a **new ****logical****partition**** (sda6)**. Here I installed OpenSuse 13.1. During this installation I choose to NOT install any boot loader from OpenSuse. When OpenSuse installaton procedure decided, unilaterally, to reboot the system, obviously OpenSuse wasn't able to start. So I started Debian and run 'grub-update', then reboot again. This time I was able to login into OpenSuse, but... my GRUB2 menú has ¡6 entries! for OpenSuse.
 
The **first ****question** is why **Boot****Info****Script** results file (see below) has so little info and, specifically:

[LIST]
[*]why says 'Mounting failed: mount: /dev/sda1 is already mounted or sda1 is busy' under sda1 in the Boot Info Summary section. 
[*]why i can't see any grub.cfg file 
[*]what is the last line meaning: 'xz: (stdin): Compressed data is corrupt'. 
[/LIST]
The fact is the file BootInfoScript generated is really different from those I've seen in this forum, and I'm wondering why.

 The **second ****question** is if anybody can explain me **why the 6 ****entries** for OpenSuse in grub menu. They seem the same, but if you look at grub.cfg file (see below the second Script results file) they aren't.
 
Any help to improve my (or our) knowledge is appreciated.
(Too if you think this isnt' the right place to post these questions and you can say me where must I have to submit them I'll be glad to do it).
**Thanks.**

Script results when I run it from Debian 7:
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /dev/sda1 ya está montado o sda1 está ocupado

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Welcome to openSUSE 13.1 
                       "Bottle" - Kernel ().
    Boot files:        /etc/fstab

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      Grub Legacy (v) in the file /HD1TBImg looks at sector 
                       1 of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, 3907029168 sectores en total
Units = sectores of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   248,588,287   248,586,240  83 Linux
/dev/sda2         248,589,810   285,635,699    37,045,890  82 Linux swap / Solaris
/dev/sda3         285,635,700   816,744,599   531,108,900   5 Extended
/dev/sda5         419,923,968   810,547,199   390,623,232  83 Linux
/dev/sda6         285,638,656   419,921,919   134,283,264  83 Linux
/dev/sda4         816,744,600 3,219,618,779 2,402,874,180   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        cf3a845f-8075-4121-9772-6246dcc6f546   ext3       RenuevaRaizExt3
/dev/sda2        06836c6f-deac-4c8b-89ca-d316c1accb58   swap       
/dev/sda4        5411C8E203F72C38                       ntfs       RecupNTFS
/dev/sda5        b155f785-c6b3-4a52-a2e7-cd07040beb1e   ext4       
/dev/sda6        ea38ba5e-2fc7-4b84-9960-d4e399b2efb2   ext4       
/dev/sr0                                                iso9660    Debian 7.3.0 amd64 1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/disk/by-uuid/cf3a845f-8075-4121-9772-6246dcc6f546 /                        ext3       (rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered)
/dev/sda5        /home                    ext4       (rw,relatime,user_xattr,barrier=1,data=ordered)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,noexec,relatime,user=roberto)


=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/disk/by-id/ata-ST2000DM001-1CH164_Z340DEEX-part6 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-ST2000DM001-1CH164_Z340DEEX-part2 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-ST2000DM001-1CH164_Z340DEEX-part5 /home                ext4       defaults              1 2
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 176.346817017 = 189.350952960  boot/grub/stage2                               1
 139.827358246 = 150.138482688  boot/initrd                                    1
 139.827358246 = 150.138482688  boot/initrd-3.11.6-4-desktop                   1
 176.342304230 = 189.346107392  boot/vmlinuz                                   1
 176.342304230 = 189.346107392  boot/vmlinuz-3.11.6-4-desktop                  1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

Script results when I run it from OpenSuse 13.1:
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Debian GNU/Linux 7
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Welcome to openSUSE 13.1 
                       "Bottle" - Kernel ().
    Boot files:        /etc/fstab

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      Grub Legacy (v) in the file /HD1TBImg looks at sector 
                       1 of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes, 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   248,588,287   248,586,240  83 Linux
/dev/sda2         248,589,810   285,635,699    37,045,890  82 Linux swap / Solaris
/dev/sda3         285,635,700   816,744,599   531,108,900   5 Extended
/dev/sda5         419,923,968   810,547,199   390,623,232  83 Linux
/dev/sda6         285,638,656   419,921,919   134,283,264  83 Linux
/dev/sda4         816,744,600 3,219,618,779 2,402,874,180   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        cf3a845f-8075-4121-9772-6246dcc6f546   ext3       RenuevaRaizExt3
/dev/sda2        06836c6f-deac-4c8b-89ca-d316c1accb58   swap       
/dev/sda4        5411C8E203F72C38                       ntfs       RecupNTFS
/dev/sda5        b155f785-c6b3-4a52-a2e7-cd07040beb1e   ext4       
/dev/sda6        ea38ba5e-2fc7-4b84-9960-d4e399b2efb2   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /home                    ext4       (rw,relatime,data=ordered)
/dev/sda6        /                        ext4       (rw,relatime,data=ordered)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root cf3a845f-8075-4121-9772-6246dcc6f546
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root cf3a845f-8075-4121-9772-6246dcc6f546
  set locale_dir=($root)/boot/grub/locale
  set lang=es_ES
  insmod gettext
fi
terminal_output gfxterm
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root cf3a845f-8075-4121-9772-6246dcc6f546
insmod png
if background_image /usr/share/images/desktop-base/joy-grub.png; then
  set color_normal=white/black
  set color_highlight=black/white
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Debian GNU/Linux, with Linux 3.2.0-4-amd64' --class debian --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root cf3a845f-8075-4121-9772-6246dcc6f546
    echo    'Loading Linux 3.2.0-4-amd64 ...'
    linux    /boot/vmlinuz-3.2.0-4-amd64 root=UUID=cf3a845f-8075-4121-9772-6246dcc6f546 ro  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-4-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.2.0-4-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root cf3a845f-8075-4121-9772-6246dcc6f546
    echo    'Loading Linux 3.2.0-4-amd64 ...'
    linux    /boot/vmlinuz-3.2.0-4-amd64 root=UUID=cf3a845f-8075-4121-9772-6246dcc6f546 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-4-amd64
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "openSUSE 13.1 (x86_64) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root ea38ba5e-2fc7-4b84-9960-d4e399b2efb2
    linux /boot/vmlinuz root=/dev/sda6
    initrd /boot/initrd
}
menuentry "openSUSE 13.1 (x86_64) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root ea38ba5e-2fc7-4b84-9960-d4e399b2efb2
    linux /boot/vmlinuz root=/dev/sda6
    initrd /boot/initrd-3.11.6-4-desktop
}
menuentry "openSUSE 13.1 (x86_64) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root ea38ba5e-2fc7-4b84-9960-d4e399b2efb2
    linux /boot/vmlinuz root=/dev/sda6
    initrd /boot/initrd
}
menuentry "openSUSE 13.1 (x86_64) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root ea38ba5e-2fc7-4b84-9960-d4e399b2efb2
    linux /boot/vmlinuz root=/dev/sda6
    initrd /boot/initrd-3.11.6-4-desktop
}
menuentry "openSUSE 13.1 (x86_64) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root ea38ba5e-2fc7-4b84-9960-d4e399b2efb2
    linux /boot/vmlinuz-3.11.6-4-desktop root=/dev/sda6
    initrd /boot/initrd-3.11.6-4-desktop
}
menuentry "openSUSE 13.1 (x86_64) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root ea38ba5e-2fc7-4b84-9960-d4e399b2efb2
    linux /boot/vmlinux-3.11.6-4-desktop.gz root=/dev/sda6
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=cf3a845f-8075-4121-9772-6246dcc6f546 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=b155f785-c6b3-4a52-a2e7-cd07040beb1e /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=00f33e75-01d8-4ac2-ab3a-32b963567b16 none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/disk/by-id/ata-ST2000DM001-1CH164_Z340DEEX-part6 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-ST2000DM001-1CH164_Z340DEEX-part2 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-ST2000DM001-1CH164_Z340DEEX-part5 /home                ext4       defaults              1 2
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
cat: /tmp/BootInfo-0LMPV8Zp/Tmp_Log: No existe el fichero o el directorio
cat: /tmp/BootInfo-0LMPV8Zp/Tmp_Log: No existe el fichero o el directorio
  No volume groups found
mdadm: No arrays found in config file or automatically

```

---

### Post by rob34 on 2014-02-05
:cry: Sigh... maybe i have to do a poll to see why there isn't any answer to my questions...


[LIST=1]
[*]Post too long 
[*]Problem too complex 
[*]Too much questions (but all of them related I think) 
[*]Doesn't like my OS 
[*]I'm not English speaker 
[*]I haven't take a shower yesterday (you know, smell...) 
[*]Moon isn't in the right phase 
[*]I must be more patient 
[*]Boot Info Script gurus are abroad (and GRUB2 ones too) 
[*]This isn't the right place to put this question, because exists more specific places (which ones, please?) 
[/LIST]

Vote your answer!
Thank you.
(Well, if somebody don't want to participate but have some clue to my questions I will wait for them too, of course :), and really happy to read them).

---

### Post by grahammechanical on 2014-02-05
> 
[LIST]
[*]why says 'Mounting failed: mount: /dev/sda1 is already mounted or sda1 is busy' under sda1 in the Boot Info Summary section.
[/LIST]


Are you running BootInfoScript from Debian or a Ubuntu live session? Scripts like this need to mount all the partitions in order to read the configurations files. If we run scripts like this from an operating system that is already loaded then the partition that the operating system is running from will already be mounted. The script is informing you of that fact.

I am unfamiliar with Debian and OpenSuse. So, I cannot tell you where to find the grub.cfg file. But in Ubuntu it is at /boot/grub. It is also clear to me that the OpenSuse developers do things differently from the Ubuntu Developers. In Ubuntu all Linux kernels are listed in grub.cfg but we can tell which kernel is which. But that does not happen with the grub.cfg of OpenSuse. For example, on my grub.cfg I see this:

> linux    /boot/vmlinuz-3.13.0-2-generic root=UUID=1f782ff4-552c-4761-82ef-ae6e58fc93a9 ro  quiet splash $vt_handoff

> linux    /boot/vmlinuz-3.13.0-2-generic root=UUID=1f782ff4-552c-4761-82ef-ae6e58fc93a9 ro recovery nomodeset 

> linux    /boot/vmlinuz-3.13.0-1-generic root=UUID=1f782ff4-552c-4761-82ef-ae6e58fc93a9 ro  quiet splash $vt_handoff

The first line will load Ubuntu with the Linux kernel 3.13.0-2.

The second line will load Ubuntu with the same kernel but will run a recovery utility that will help us repair a broken Ubuntu boot process and without setting a video mode as the problem may be caused by a video driver.

The third line will load Ubuntu with the earlier Linux kernel 3.13.0-1.

So, the additional entries in grub.cfg are all earlier kernels + kernels that will load with a recovery utility. This is not clear in that OpenSuse grub.cfg.

> [COLOR=#000000][FONT=Ubuntu Mono]linux /boot/vmlinuz root=/dev/sda6[/FONT][/COLOR]
> [COLOR=#000000][FONT=Ubuntu Mono]linux /boot/vmlinuz-3.11.6-4-desktop root=/dev/sda6[/FONT][/COLOR]

I can only guess that they are different kernels but it is not clear. Seeing this makes me appreciate the work done by the Ubuntu developers and is a reason why I use Ubuntu.

Regards.

---

### Post by rob34 on 2014-02-07
Hi graham!
And thank you very much for your answer.
> Are you running BootInfoScript from Debian or a Ubuntu live session?  Scripts like this need to mount all the partitions in order to read the  configurations files. If we run scripts like this from an operating  system that is already loaded then the partition that the operating  system is running from will already be mounted. The script is informing  you of that fact.
mmmm, NO, I'm running script from Debian 7 installed in my box (and, the second BootInfoScript has been run from OpenSuse installed too).
**Do you think it's better to run script from a live session?**
Maybe this way I get more and more accurated info?
I can try it (sure I'll do it, but your opinion matters to me anyway).

I appreciate very much your clues about possible differente kernels, but like you said it is not clear. I go research too this.

```
this makes me appreciate the work done by the Ubuntu developers and is a reason why I use Ubuntu
```
Yes, I wanted to install two GNU/Linux OS to choose between Debian, OpenSuse and Ubuntu.
I've started from Debian and I was forced to use OpenSuse next by other questions.

But I think, when I'll be able to clarify my 'system status', then will install OpenSuse (thay I need to recover data and, mainly, mount disk images with several partitions into them like loop devices in an easier and more comfortable way) and **Ubuntu**.
I've started with Debian because I think I'll install an Ubuntu LTS release, and install a release which is two years old (12.04) only by two months... seems a pity to me.

Anyway thank you again.
I'll continue to research about all this stuff and will wait to see if anybody can point me on anothers ways to understand it better.
Best regards.

---

### Post by oldfred on 2014-02-07
Normally Ubuntu's os-prober finds the grub.cfg or grub.conf or other configuration files & just copies those. When it sees a system without a config file, it often just creates its own boot stanza's using found kernels.
Do not know about other systems and how they configure grub or boot loader.

I find with multiple installs of Ubuntu is just is easier to turn off os-prober and manually add boot stanza's to 40_custom. And with Ubuntu it adds links to most current kernel in /boot so you can boot link and have most current kernel booting from another Ubuntu install without having to boot into first install and run sudo update-grub or manually maintain grub.cfg.

       Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus) 

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by rob34 on 2014-02-09
Hi Oldfred.
Thank you very much for your answer too.

I'll try to put together your info with graham answer and I hope I'll be able to understand Grub2 'internals'.

I think this is specially interesting for me to know:
> **oldfred said:**
> 
I find with multiple installs of Ubuntu is just is easier to turn off os-prober and manually add boot stanza's to 40_custom. And with Ubuntu it adds links to most current kernel in /boot so you can boot link and have most current kernel booting from another Ubuntu install without having to boot into first install and run sudo update-grub or manually maintain grub.cfg.
Probably I'll follow your advise when I install Ubuntu.

Thanks again to both, and hope 'read' you later.
Best regards.

---

