---
title: "Getting Grub to show multiple Windows installs"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by TerryArnott on 2011-09-12
Hi All,

Not sure if this is the right spot for this question, if not, could it be nudged into the right place?

Here is my situation.
I have a HDD Partitioned into 3 primary, and an extended, with 3 partitions on the extended.

The 3 Primaries each have a complete independent installation of WinXP, one for the kids, one for the Mrs and one for me.  YES, this is necessary as the kids tend to trash theirs in a matter of weeks, the Mrs needs hers for work, and mine is set up for games and stuff like that.  Essentially its like 3 separate PC's in the one box.
I'm also dabbling with linux so the Extended partition has a Linux Partition and a swap Partition, and finally a large Data partition that we can all share.

I installed the 3 windows parts first and windows set up its own boot manager allowing me to select which instance to boot into, then I installed Ubuntu 11.4 which then set up grub.  But Grub only shows options for the Windows boot manager or linux.  The linux option boots linux fine, and the windows option brings up the windows boot manager where I can select from the 3 instances of XP.

What I am trying to achieve is to have Grub list all 3 XP instances and linux in the one go, rather than having to go through 2 different managers.

My Big Question is, HOW?  :confused:

I have installed Grub customizer but cant figure how to get it to show the 3 XP instances instead of just showing the manager.

Any Suggestions?  :confused:

---

### Post by raja.genupula on 2011-09-12
i dont know is it going to work for you or not ? 
but i am sure by doing this you lose nothing 

```
sudo dpkg-reconfigure grub-pc
``` 
try once

---

### Post by ubudog on 2011-09-12
Hi, in Grub Customizer, select File > Install to MBR > click OK.  It should automatically select the correct hard drive.

Now, make your modifications, click save, and reboot.  You should see all your OS'es in a list.  Let us know if you need any help.  :-)

---

### Post by saltmarshlamb on 2011-09-12
As each is a seperate partition I assume that a grub update finds one only - you could add the others as custom entries

[https://help.ubuntu.com/community/Grub2#Custom_Menu_Entries](https://help.ubuntu.com/community/Grub2#Custom_Menu_Entries)

post 14/15 here might be of help [http://ubuntuforums.org/showthread.php?t=1285711](http://ubuntuforums.org/showthread.php?t=1285711)

You should also be able to look at the existing grub.cfg to see how it needs to look I think.

---

### Post by oldfred on 2011-09-12
Windows only knows to boot from the active (boot flag) partition. Second or more installs literally move the boot files from the second install to the first install. So grub then cannot find the second install's boot files.

Since they are all XP and in primary partitions, it should be a bit easier. You need to move ntldr back into each install and create a boot.ini for each that only boots that one install. Possibly repair boot sector.

To be sure of what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

To understand Windows multboot, examples are for new installs, so we have to manually reedit some things to make it work on existing installs.
To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly

I get a lot of my info from old posts by meierfra.
Repair 2 windows installs to get each to be able to have grub entries XP & Win7 or Vista
[http://ubuntuforums.org/showthread.php?t=1362297](http://ubuntuforums.org/showthread.php?t=1362297)
[http://ubuntuforums.org/showthread.php?t=1421737](http://ubuntuforums.org/showthread.php?t=1421737)

[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by TerryArnott on 2011-09-13
Hi OLDFRED and others,

OK, while all posts have been helpfull, it looks like OLDFRED really knows his kit, as I tried the custom entry idea but it kept saying that there were no boot files in the partitions so wouldn't boot to them.  That makes sense with what you said, pity M$ has to **** around with things so much.  
Moving the boot files each time you boot? What The hell were they smoking THAT day?

Here is the output from the BootInfoScript


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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   307,202,047   307,200,000   7 NTFS / exFAT / HPFS
/dev/sda2         307,210,995   768,003,389   460,792,395   7 NTFS / exFAT / HPFS
/dev/sda3         768,003,390 1,228,795,784   460,792,395   7 NTFS / exFAT / HPFS
/dev/sda4       1,228,795,902 3,907,028,991 2,678,233,090   5 Extended
/dev/sda5       1,843,206,144 3,907,028,991 2,063,822,848   7 NTFS / exFAT / HPFS
/dev/sda6       1,228,795,904 1,815,861,247   587,065,344  83 Linux
/dev/sda7       1,815,863,296 1,843,202,047    27,338,752  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        00F43D1CF43D157E                       ntfs       Kids
/dev/sda2        EE88E74588E70AC3                       ntfs       Marni
/dev/sda3        ACBCE78EBCE7517E                       ntfs       Daddy
/dev/sda5        2A408E554A089176                       ntfs       Data
/dev/sda6        a2eea2b9-5e1f-417f-8a1b-fa8733ab8959   ext4       
/dev/sda7        15a60e94-4171-42e5-9172-8c131cf6678e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

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
set default="${saved_entry}"
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
search --no-floppy --fs-uuid --set=root a2eea2b9-5e1f-417f-8a1b-fa8733ab8959
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root a2eea2b9-5e1f-417f-8a1b-fa8733ab8959
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	savedefault
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a2eea2b9-5e1f-417f-8a1b-fa8733ab8959
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=a2eea2b9-5e1f-417f-8a1b-fa8733ab8959 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a2eea2b9-5e1f-417f-8a1b-fa8733ab8959
	echo	'Loading Linux 2.6.38-11-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=a2eea2b9-5e1f-417f-8a1b-fa8733ab8959 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" --class windows --class os {
	savedefault
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 00F43D1CF43D157E
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
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=15a60e94-4171-42e5-9172-8c131cf6678e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 594.069580078 = 637.877354496  boot/grub/core.img                             1
 750.084682465 = 805.397295104  boot/grub/grub.cfg                             1
 588.331615448 = 631.716261888  boot/initrd.img-2.6.38-11-generic-pae          2
 586.975040436 = 630.259650560  boot/vmlinuz-2.6.38-11-generic-pae             1
 588.331615448 = 631.716261888  initrd.img                                     2
 586.975040436 = 630.259650560  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

I will take a look at those other posts you refered too and see if I can figure out what I need to do.  
Of course if you think its simple enough to reply with some 'baby steps' type instructions for me to follow that would be good too... lol

Thanks
Terry

EDIT:
WOW! I looked at that "http://www.multibooters.co.uk/multiboot.html" one!  I think that guy has a couple of extra zeros on the end of his IQ that I don't have, it's all way over my head.
Couldn't they just put the files to boot each partition ON the partition so that all the boot manager has to do it point and shoot?

---

### Post by oldfred on 2011-09-13
The person who first posted that multibooter's site refered to the pictures and I just copied that as that explains the basics. But he does have a lot of good detail.

Please go back to post #6 and change to Microsoft. We try to show some respect for the competition. Part of my brand new moderation responsibilities.

You should just be able to copy boot.ini, ntldr & ntdetect.com to your other installs. You then have to edit boot.ini to show each one (you may just be able to leave all 3)? But may want to change the default to be sure it boots the correct one as default.

If you edit boot.ini in Ubuntu be just to save with Windows line endings.

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to choose windows format.

If you ever use the Windows XP CD to repair, you have to move boot flag to the partition you want to repair first.
XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

---

