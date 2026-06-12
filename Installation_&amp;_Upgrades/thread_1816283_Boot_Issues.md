---
title: "Boot Issues"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by Matchlighter on 2011-08-01
I am having some issues getting Ubuntu 11.04 to boot. I have tried Googling, but to no avail. I installed Ubuntu Server 11.04 X64 and it worked fine, but I meant to install the desktop version. When I did that, it installed successfully, but when I try to boot it says something to affect of "No boot disc. Insert boot disc and press any key." I have tried reinstalling the desktop version and the server version. I get the same message every time. The only way I can get it to work again is to use Wubi (I can install and boot Windows successfully). However, I would prefer to use Wubi since I am using this as a Home Server (with a a Gui interface instead of command line). I have tried completely formatting the HDD but that did not help. 

Any help would be appreciated :)
Matchlighter

---

### Post by oldfred on 2011-08-01
Welcome to the forums.

If you installed server and it worked it sounds like a Video issue. What video card. 

Do you have in Intel motherboard. They often require a boot flag on a primary partition. Grub does not use a boot flag, so they must be thinking only of windows which has to have a boot flag. 

Do you have it installed? If so run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Video issues:
Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by Matchlighter on 2011-08-02
It is an Intel chipset graphics. The computer is essentially a Gateway [GT5408 ]("http://support.gateway.com/s/pc/R/1014168/1014168nv.shtml")with a larger HDD. But, I believe that I tried reinstalling Server again, but it does that same thing. I will retry server again to make sure. I would prefer a Gui, but I may have to make do. I will try the BootInfoScript with a Live USB key and get back to you. I am guessing that it is the boot flag you mentioned that is the problem.

---

### Post by Matchlighter on 2011-08-02
Here is that Output file for the Boot Info Script.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30510 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34         1,987         1,954 BIOS Boot partition
/dev/sda2           1,988 3,904,951,206 3,904,949,219 Data partition (Windows/Linux)
/dev/sda3   3,904,951,207 3,907,029,118     2,077,912 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             48     7,831,551     7,831,504   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        660a8a49-ddcb-4045-9788-cceb28ff649f   ext4       
/dev/sda3        e60e185d-f42f-4846-b7f8-ace5708d06e4   swap       
/dev/sdb1        1B08-1039                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt2)'
search --no-floppy --fs-uuid --set=root 660a8a49-ddcb-4045-9788-cceb28ff649f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt2)'
search --no-floppy --fs-uuid --set=root 660a8a49-ddcb-4045-9788-cceb28ff649f
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root 660a8a49-ddcb-4045-9788-cceb28ff649f
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=660a8a49-ddcb-4045-9788-cceb28ff649f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root 660a8a49-ddcb-4045-9788-cceb28ff649f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=660a8a49-ddcb-4045-9788-cceb28ff649f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root 660a8a49-ddcb-4045-9788-cceb28ff649f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt2)'
    search --no-floppy --fs-uuid --set=root 660a8a49-ddcb-4045-9788-cceb28ff649f
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=660a8a49-ddcb-4045-9788-cceb28ff649f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=e60e185d-f42f-4846-b7f8-ace5708d06e4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 684.134981155 = 734.584342528  boot/grub/core.img                             1
 684.134988785 = 734.584350720  boot/grub/grub.cfg                             1
   0.415010452 = 0.445614080    boot/initrd.img-2.6.38-8-generic               2
 684.133253098 = 734.582487040  boot/vmlinuz-2.6.38-8-generic                  1
   0.415010452 = 0.445614080    initrd.img                                     2
 684.133253098 = 734.582487040  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by oldfred on 2011-08-02
Even though you are using gpt and gpt supposedly does not use a boot flag & grub does not use a boot flag, we have seen before several users with Intel motherboards that would not boot without the boot flag on a partition.

---

### Post by srs5694 on 2011-08-02
I'm far from positive of this, but my suspicion is that you've got a BIOS that requires a boot flag to be present on a *Master Boot Record (MBR)* partition. Your disk currently uses the competing GUID Partition Table (GPT) partitioning system, so you should *not* attempt to set a boot flag using parted or GParted; these tools interpret "boot flag" as being something completely different on such disks. Instead, set the boot flag with fdisk. You should see just one partition in fdisk, of type "ee". Type "a" to set the boot flag, then "w" to save your changes.

---

### Post by srs5694 on 2011-08-02
Oh, one other thing: You've mentioned WUBI, which implies Windows; but if your computer uses a conventional BIOS, you won't get Windows to boot on that first hard disk, since Microsoft has chosen to limit Windows to boot from MBR disks on BIOS-based computers. Thus, if you intend to dual boot with Windows, you'll have to convert the disk from GPT to MBR form. This in turn obviates the need to do anything with the type-ee protective partition in the MBR.

---

### Post by Matchlighter on 2011-08-02
Yes when I tried WUBI I converted the disk to MBR and then installed Windows. But that was just a test to see if it would work and fix the problem for booting Ubuntu when I installed. Crazy, I know.

---

### Post by Matchlighter on 2011-08-02
Fdisk as in Microsft Fdisk? Is there a command line I can use to access it from a Windows Recovery Command Prompt?

---

### Post by srs5694 on 2011-08-02
No, fdisk as in Linux's fdisk. There's no evidence of a current Windows installation in your Boot Info Script output, so if you've changed things since then my advice concerning what to do might also change.

Note that Microsoft's partitioning tools do an incomplete job of converting from GPT to MBR. The result is technically an MBR disk, but there's enough left over GPT data to confuse some tools, including several Linux partitioning tools. Thus, if you installed Windows after you took the Boot Info Script results you posted, there's no telling what your disk is like now and you might need to do something completely different with it than what I suggested.

---

### Post by Matchlighter on 2011-08-02
I don't have Windows on it right now. But that would explain why I get a message like "There is some GPT data on the hard drive but it is corrupt" when I to install Ubuntu. Do I just type 'fdisk' in the Ubuntu CD's Terminal to access it?

---

### Post by Matchlighter on 2011-08-02
Excellent. The fdisk utility fixed it right up. Thank you.

---

### Post by srs5694 on 2011-08-02
If you're getting a message about corrupt GPT data, then something else may be wrong. I recommend you run the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) and post the RESULTS.txt file that it produces here. Also, the output of "sudo parted /dev/sda print" may be useful. Please post both between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to improve legibility.

---

### Post by YannBuntu on 2011-08-03
Hi.

> **srs5694 said:**
> Your disk currently uses the competing GUID Partition Table (GPT) partitioning system, so you should *not* attempt to set a boot flag using parted or GParted; these tools interpret "boot flag" as being something completely different on such disks.

Is there a bug report for this ? (I just found [this]("http://osdir.com/ml/bug-parted-gnu/2011-06/msg00045.html"))

---

### Post by srs5694 on 2011-08-03
re: "boot flag" having different meanings for MBR vs. GPT

> **YannBuntu said:**
> Is there a bug report for this ? (I just found [this]("http://osdir.com/ml/bug-parted-gnu/2011-06/msg00045.html"))

I don't think the libparted developers consider this a bug. Personally, I think that the way libparted conflates flags and partition type codes generally, and the "boot flag" having different meanings in GPT and MBR specifically, is a very poor design choice and should be changed, but that would be a pretty huge change to the software.

---

### Post by YannBuntu on 2011-08-03
Thanks. I created a report in case it could be improved: [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/820719](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/820719)

For follow-up.

---

