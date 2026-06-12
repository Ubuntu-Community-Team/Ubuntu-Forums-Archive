---
title: "Ubuntu 10.10 upgraded to 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Lordestabia on 2011-04-29
:confused:Upgraded from Ubuntu 10.10 (x64) to 11.04 (x64). Upgrade completed, and rebooted when requested. Stuck on the GRUB loader with the following:
[INDENT]error:  symbol not found: 'grub_env_export'
grub rescue> _
[/INDENT]Only commands working are insmod, ls, set, and boot. No other boot media available. What can I do to boot up? It's quite urgent at the moment.
 
Any assistance is greatly appreciated.

---

### Post by sikander3786 on 2011-04-29
We need you to boot an Ubuntu Live CD/USB and run this command.

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh; hb=HEAD'
```

It would download bootinfoscript in your home directory. Now run this command.

```
sudo bash boot_info_script.sh
```

It would generate a Results.txt file in your home directory. Copy all text from it and in your new reply, click the # icon to generate [code] tags and paste your text in between the tags.

It would let us take a look at your boot setup and advise accordingly.

---

### Post by Lordestabia on 2011-04-29
Would have been my first action, but none avail. Stuck at work with a laptop. Did the following in the meantime.
[INDENT]insmod part_msdos
insmod ext2
 
ls (hd0,msdos2)/boot
[/INDENT]Got a listing for the files in /boot.

---

### Post by Lordestabia on 2011-04-29
I used set to point to the initrd, and linux files. Got No loaded kernel. Tried insmod normal, and got error: symbol not found: 'grub_env_export'. Tried insmod linux, and got error: symbol not found: 'grub_mm_base'.
 
Anyone:?:

---

### Post by Lordestabia on 2011-04-29
:mad:

---

### Post by sikander3786 on 2011-04-29
Why not try Grub re-installation.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by yaronf on 2011-04-29
Hi Sikander,

this is the second time in a row my computer dies on me when I upgrade to the next major revision. This time I half-expected it, so it only wasted an hour of my life repairing GRUB from the LiveCD (from the Karmic LiveCD, by the way), and now the netbook is booting into Natty just fine. Is there still any way I can report the problem and provide meaningful information to the maintainers?

Thanks,
     Yaron

---

### Post by Lordestabia on 2011-04-29
Because at the time I had no boot/live distros (cd/dvd/usb/etc) with me, and needed to get in via the rescue console for grub. No-one had any advice, so I waited till I got home to fix the boot loader.

As it is, got it fixed, only to run into a bigger problem. Everytime I log in, the laptop keeps locking up completely, forcing a complete manual shutdown. I noticed the Caps lock keeps flashing non stop. This happened with my account, and with a Demo account. It only worked from (Ubuntu safemode), sans networking. Logged out, tried Ubuntu classic, no visuals, and locked up again. Right now, I'm using the previous kernel still on the laptop to get on the net.

From what I can gather, I got some kind of kernel panic, no idea what unfortunately.

Any ideas?

---

### Post by sikander3786 on 2011-04-29
Glad it is sorted for you now.

I can't say how you can report this as we don't know any possible causes and the original problem. Still, you can use Launchpad if you've got all the information.

---

### Post by Lordestabia on 2011-04-29
> **sikander3786 said:**
> We need you to boot an Ubuntu Live CD/USB and run this command.

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh; hb=HEAD'
```It would download bootinfoscript in your home directory. Now run this command.

```
sudo bash boot_info_script.sh
```It would generate a Results.txt file in your home directory. Copy all text from it and in your new reply, click the # icon to generate [code] tags and paste your text in between the tags.

It would let us take a look at your boot setup and advise accordingly.

This is the output for the command as requested by you:
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file 
                       /BS-Ubuntu-10_10_sda2.bsf looks at sector 213467192 of 
                       the same hard drive for core.img, but core.img can not 
                       be found at this location.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 343492632 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       btrfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 NTFS / exFAT / HPFS
/dev/sda2         204,797,952   400,109,567   195,311,616  83 Linux
/dev/sda3         400,111,614   701,077,503   300,965,890   5 Extended
/dev/sda5         400,111,616   595,421,183   195,309,568  83 Linux
/dev/sda6         595,423,232   603,420,671     7,997,440  82 Linux swap / Solaris
/dev/sda7         603,422,720   701,077,503    97,654,784  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.9 GB, 15931539456 bytes
255 heads, 63 sectors/track, 1936 cylinders, total 31116288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               8,192    31,116,287    31,108,096   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        78B8F0F3B8F0B12C                       ntfs       
/dev/sda2        dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c   ext4       
/dev/sda5        847abcf4-e6e3-4137-86a1-fb64af92ac5e   btrfs      
/dev/sda6        aab79d15-d290-4b6b-9285-e7c56835bcbd   swap       
/dev/sda7        4722a464-e1dd-40a3-8d8b-34ae933ce69c   ext4       
/dev/sdb1        6466-6438                              vfat       SDHC_16GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/SDHC_16GB         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
c:\BS-Ubuntu-10_10_sda2.bsf="Ubuntu 10.10"--------------------------------------------------------------------------------

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

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c
set locale_dir=($root)/boot/grub/locale
set lang=en_ZA
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
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c
    linux    /boot/vmlinuz-2.6.35-29-generic root=UUID=dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c
    echo    'Loading Linux 2.6.35-29-generic ...'
    linux    /boot/vmlinuz-2.6.35-29-generic root=UUID=dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 78B8F0F3B8F0B12C
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
UUID=dbc8f3f9-cd4d-4dcb-9244-6b759c3ed91c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=aab79d15-d290-4b6b-9285-e7c56835bcbd none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 163.793190002 = 175.871598592  boot/grub/core.img                             1
 172.208892822 = 184.907890688  boot/grub/grub.cfg                             1
 128.795452118 = 138.293063680  boot/initrd.img-2.6.35-29-generic              2
 105.754634857 = 113.553174528  boot/initrd.img-2.6.38-8-generic               2
 163.935184479 = 176.024064000  boot/vmlinuz-2.6.35-29-generic                 1
 125.253238678 = 134.489640960  boot/vmlinuz-2.6.38-8-generic                  1
 105.754634857 = 113.553174528  initrd.img                                     2
 128.795452118 = 138.293063680  initrd.img.old                                 2
 125.253238678 = 134.489640960  vmlinuz                                        1
 163.935184479 = 176.024064000  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by sikander3786 on 2011-04-29
There are multiple problems with that output. You should try to purge and re-install Grub as mentioned here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Lordestabia on 2011-04-30
Confirmed kernel panic. Logged in via tty2,3,4 to capture relevant error messages from messages, and syslog using
[INDENT]tail -f /var/log/messages > error-messages 2>&1 3>&1              on tty2
tail -f /var/log/syslog > error-syslog 2>&1 3>&1                        on tty3
monitored syslog from tty4
[/INDENT]No details for the crash was recorded. How can I capture the details to post online? linux-2.6.38-8-generic x86_64 is the latest kernel pn the laptop. Using linux-2.6.35-29-generic x86_64 right now.

---

### Post by Lordestabia on 2011-04-30
The upgrade also completely messed up my software sources on the software centre. Re enabled, no effect. PPA for Uplink not showing. PPA for Vendetta not showing. PPA for cdemu only showing 1 of 9 items. CDemu broken, and not working had to remove vhba-dkms to get the update compete, then removed the PPA itself. Not happy with this experience.:icon_frown: Apparently the Upgrade completely removed CDEmu itself, and I'm using that.

---

### Post by Lordestabia on 2011-04-30
Kernel panic probably caused by problem with vhba-dkms module. Back to new kernel. Looks like problem solved for now. Only teething problems now.:)

---

### Post by tomdkat on 2011-05-05
> **Lordestabia said:**
> Kernel panic probably caused by problem with vhba-dkms module. Back to new kernel. Looks like problem solved for now. Only teething problems now.:)
Thanks for posting this. I also had CDEmu installed and I was also getting kernel panics when booting normally.  Booting in safe mode was the only way I could boot my system, after the upgrade. Uninstalling CDEmu worked for me as well.

Thanks again!  :)

Peace...

---

