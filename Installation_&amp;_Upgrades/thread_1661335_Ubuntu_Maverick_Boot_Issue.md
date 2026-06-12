---
title: "Ubuntu Maverick Boot Issue"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by jdownes on 2011-01-06
Have installed Ubuntu 10.10 Maverick on a new seagate 150Gb HD

I disconnected the internal drive and installed Ubuntu onto the external drive

It worked fine from the initial install

Now when I re-boot the screen goes black until I hit CTRL ALT DEL hen I get the grub menu

Ubuntu fires up when I select it

So why doesnt it fire up from scratch???

The BIOS program is set to select the external HD first and internal drive second

(Have windows Vista on the internal drive!!)

Any ideas

Otherwise Ubuntu is running very fast - wont be using windows much longer - great bit of software

Thanks




:lolflag:

---

### Post by presence1960 on 2011-01-06
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by jdownes on 2011-01-07
```
Thanks for the help here is the results file:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /Boot/bcd

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   216,881,151   216,881,089   7 HPFS/NTFS
/dev/sda2         216,893,565   231,188,604    14,295,040   7 HPFS/NTFS
/dev/sda3         231,191,415   234,556,278     3,364,864   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   306,440,191   306,438,144  83 Linux
/dev/sdb2         306,442,238   312,580,095     6,137,858   5 Extended
/dev/sdb5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4E19327A7BA5EB6F                       ntfs       Old Hard Drive                
/dev/sda2        E60401290400FDF5                       ntfs       HP_RECOVERY                   
/dev/sda3        68EE811FEE80E6A2                       ntfs       OS_TOOLS                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8fc020b4-1c9f-48a1-bde6-5b908fcee3d1   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f557089f-606d-4926-9fda-d5e3c31b62ff   swap                                     
/dev/sdb: PTTYPE="dos" 

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 8fc020b4-1c9f-48a1-bde6-5b908fcee3d1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 8fc020b4-1c9f-48a1-bde6-5b908fcee3d1
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8fc020b4-1c9f-48a1-bde6-5b908fcee3d1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8fc020b4-1c9f-48a1-bde6-5b908fcee3d1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8fc020b4-1c9f-48a1-bde6-5b908fcee3d1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8fc020b4-1c9f-48a1-bde6-5b908fcee3d1 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8fc020b4-1c9f-48a1-bde6-5b908fcee3d1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8fc020b4-1c9f-48a1-bde6-5b908fcee3d1
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8fc020b4-1c9f-48a1-bde6-5b908fcee3d1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f557089f-606d-4926-9fda-d5e3c31b62ff none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  64.7GB: boot/grub/core.img
  60.2GB: boot/grub/grub.cfg
  39.3GB: boot/initrd.img-2.6.35-22-generic
  64.7GB: boot/vmlinuz-2.6.35-22-generic
  39.3GB: initrd.img
  64.7GB: vmlinuz
```

Havent got a clue what this means???

:(

---

### Post by presence1960 on 2011-01-07
Looks good to me. The only thing that seems amiss is you have the wubi entries in your windows partition. Did you have wubi installed at one time? 

Since you only have linux detected in your GRUB there will be no bootup selection menu until you hit Shift. If you do not hit shift it should boot right to ubuntu.

If this is not the case or not how you want it to work you can boot to Ubuntu and open a terminal and run ```
sudo update-grub
```to detect windows and add an entry to the GRUB menu. When completed reboot and see if you get the GRUB menu.

Reference for above info: [https://help.ubuntu.com/community/Grub2#Boot Display Behavior](https://help.ubuntu.com/community/Grub2#Boot Display Behavior)

Scroll up on that page I linked to see how to edit the Hidden Timeout. Look for "/etc/default/grub (file)" and find the hidden timeout subsection.

---

### Post by drs305 on 2011-01-07
How long are you waiting before you press CTRL-ALT-DEL?

As *presence1960* indicated, if your system doesn't detect another OS it will boot straight into Ubuntu. If you aren't giving it enough time to boot and press those keys it will generate a 'recordfail' event. When you reboot, it will find the 'recordfail' marker and display the menu (with no countdown - you have to make a selection).

I'd do what *presence1960* suggested, in which case it should see Windows and you won't have the initial behavior again. If you haven't already done what is recommended, the next time it boots notice whether there is any hard drive activity and give it a minute or so to boot into Ubuntu before pressing the reset key combination.

---

### Post by jdownes on 2011-01-08
Thanks*** presence1960*** & ***drs305 ***for the help.

I did try installing Maverick onto a disk containing windows Vista and ran into all sorts of issues,so I abandoned that route. However another distro I was playing with suggested my old hd was dying so I cloned it onto a new hd.

This is where the wubi has probably come from???

Because I want to keep Linux away from windows I got yet another hd and installed it on this and run linux off an external drive.

Point taken about the time before CTRL ALT DEL.

Everything is running super fast,just trying to convert other family members to use it.

Cheers guys


:D:D

---

### Post by presence1960 on 2011-01-08
> **jdownes said:**
> Thanks*** presence1960*** & ***drs305 ***for the help.

I did try installing Maverick onto a disk containing windows Vista and ran into all sorts of issues,so I abandoned that route. However another distro I was playing with suggested my old hd was dying so I cloned it onto a new hd.

This is where the wubi has probably come from???

Because I want to keep Linux away from windows I got yet another hd and installed it on this and run linux off an external drive.

Point taken about the time before CTRL ALT DEL.

Everything is running super fast,just trying to convert other family members to use it.

Cheers guys


:D:D

You are welcome.

---

### Post by drs305 on 2011-01-08
I came back to this thread to see if you had solved your issue. 

One reason was because after writing my previous post I ran into a situation very similar to what you described and wanted to mention it.

I'm testing Natty, the next Ubuntu release, and I also am often installing/reinstalling various Grub2 versions. Yesterday I found that my system booted to a completely blank screen (no blinking cursor, etc) and I had to reboot using CTRL-ALT-DEL. I repeated this boot several times - in most cases CTRL-ALT-DEL twice rebooted the system. In two cases, CTRL_ALT-DEL twice didn't, but knowing what would be on the screen if I could see it I just pressed ENTER and it rebooted. It's possible I could have gone to terminal but I didn't try.

The solution in my case was to edit the Grub2 entry by highlighting the first entry and pressing 'e'. On my mix of various operating systems, I was booting Grub 1.99, which had added "vt.handoff=7" at the end of the 'linux' line. Using the cursor button and DEL key I removed "vt.handoff=7", pressed CTRL-x to boot, and it booted successfully once again.

I'll note this was using a Natty 1.99 Grub and booting to a Maverick installation, so it's not like this will be a situation encountered by many users. Just thought I'd mention it here since the symptoms were the same as the OP's.

---

### Post by presence1960 on 2011-01-08
> **drs305 said:**
> I came back to this thread to see if you had solved your issue. 

One reason was because after writing my previous post I ran into a situation very similar to what you described and wanted to mention it.

I'm testing Natty, the next Ubuntu release, and I also am often installing/reinstalling various Grub2 versions. Yesterday I found that my system booted to a completely blank screen (no blinking cursor, etc) and I had to reboot using CTRL-ALT-DEL. I repeated this boot several times - in most cases CTRL-ALT-DEL twice rebooted the system. In two cases, CTRL_ALT-DEL twice didn't, but knowing what would be on the screen if I could see it I just pressed ENTER and it rebooted. It's possible I could have gone to terminal but I didn't try.

The solution in my case was to edit the Grub2 entry by highlighting the first entry and pressing 'e'. On my mix of various operating systems, I was booting Grub 1.99, which had added "vt.handoff=7" at the end of the 'linux' line. Using the cursor button and DEL key I removed "vt.handoff=7", pressed CTRL-x to boot, and it booted successfully once again.

I'll note this was using a Natty 1.99 Grub and booting to a Maverick installation, so it's not like this will be a situation encountered by many users. Just thought I'd mention it here since the symptoms were the same as the OP's.

I always welcome new learning and info. BTW your how-to threads are very helpful, not only to myself but I am sure many others. I have most of them bookmarked and converted to .pdf format.

---

