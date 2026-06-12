---
title: "Full Install to USB won't boot : &quot;Reboot and select a proper boot device&quot;"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by cL0h on 2011-06-17
Hi all,
First let me say that I have looked for help with my issue over at the XBMC.org forums but got little traction. XBMC Linux is based on Ubuntu 10.04.2 LTS so I'm hoping the folks here can help. I've been getting most of my info from searching ubuntuforums anyway and people here seem to know a lot more.

I'm fairly new to Linux but I do understand computer terminology from years using Windows. 
OK so I used an XBMC 10.1 Live CD to do a "full install" onto a USB flash drive but when I reboot the machine with all other disks unplugged/removed and with the USB as the first boot device I get
"Reboot and select a proper boot device"

I have used Gparted to confirm the USB contains a single ext2 partition with (what looks to me like) an intact file system.
GParted shows also that the boot flag is set on the partition. I formatted the USB flash disk as ext2 before running the install with label "XBMCRally" and during the install I chose to install an MBR and no swap. From reading numerous posts here on UbuntuForums I believe this should work.

I think I have done everything necessary to make the device bootable. The three considerations I am aware of are :
a) I have set the USB device to be loaded as a Hard Disk and not "auto".
b) It is the first (and only) boot device
c) I have set the boot flag on the partition to which Linux is installed and this is the only partition on the only device in the system.

That's as far as my knowledge goes. Anyone know what I should do next? How do I confirm or fix the MBR?

---

### Post by DirtyPC on 2011-06-17
It could be one of three things:
1.You have made an error
2.Your mobo doesn't support USB boot
3.Your USB doesn't support booting.

Look into unetbootin.

---

### Post by oldfred on 2011-06-17
If computer does not boot from USB then unetbootin will not work either. I think then the only choice is plop.

Boot flag is not used by grub. Some BIOS require one, so leave it.

Are you sure you have grub2's boot loader installed to the MBR?

If you have Ubuntu running somewhere or a liveCD or USB with Linux plug in flash drive and run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by cL0h on 2011-06-17
Wow thanks for the quick turnaround. I can confirm the stick and mobo boot. I'm not sure I have grub2 loaded to MBR. Here's that file.  Shell output was preceded by:  "gawk" could not be found, using "busybox awk" instead. This may lead to unreliable results.
Any ideas?

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    15,728,639    15,726,592  83 Linux
/dev/sda2          15,730,686    16,775,167     1,044,482   5 Extended
/dev/sda5          15,730,688    16,775,167     1,044,480  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4076 MB, 4076863488 bytes
166 heads, 54 sectors/track, 888 cylinders, total 7962624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     7,962,623     7,960,576  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        057c72d3-a5b8-45a5-92b2-5eb81a19893d   ext4       
/dev/sda5        477253e0-cadf-41b0-b6e5-7f9fa818033e   swap       
/dev/sdb1        cdeb4ad6-3b35-4c23-84bd-3000da697d6a   ext2       xbmcrally

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/xbmcrally         ext2       (rw,nosuid,nodev,uhelper=udisks)


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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 057c72d3-a5b8-45a5-92b2-5eb81a19893d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 057c72d3-a5b8-45a5-92b2-5eb81a19893d
set locale_dir=($root)/boot/grub/locale
set lang=en_IE
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 057c72d3-a5b8-45a5-92b2-5eb81a19893d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=057c72d3-a5b8-45a5-92b2-5eb81a19893d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 057c72d3-a5b8-45a5-92b2-5eb81a19893d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=057c72d3-a5b8-45a5-92b2-5eb81a19893d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 057c72d3-a5b8-45a5-92b2-5eb81a19893d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 057c72d3-a5b8-45a5-92b2-5eb81a19893d
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=057c72d3-a5b8-45a5-92b2-5eb81a19893d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=477253e0-cadf-41b0-b6e5-7f9fa818033e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.164783478 = 0.176934912    boot/grub/core.img                             1
   0.164794922 = 0.176947200    boot/grub/grub.cfg                             1
   1.631801605 = 1.752133632    boot/initrd.img-2.6.38-8-generic               2
   0.951591492 = 1.021763584    boot/vmlinuz-2.6.38-8-generic                  1
   1.631801605 = 1.752133632    initrd.img                                     2
   0.951591492 = 1.021763584    vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cdeb4ad6-3b35-4c23-84bd-3000da697d6a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set cdeb4ad6-3b35-4c23-84bd-3000da697d6a
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=800x600
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdeb4ad6-3b35-4c23-84bd-3000da697d6a
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=cdeb4ad6-3b35-4c23-84bd-3000da697d6a ro   quiet splash xbmc=autostart,nodiskmount loglevel=0 video=vesafb
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=800x600
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cdeb4ad6-3b35-4c23-84bd-3000da697d6a
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=cdeb4ad6-3b35-4c23-84bd-3000da697d6a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=cdeb4ad6-3b35-4c23-84bd-3000da697d6a /               ext2    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.603771210 = 2.795778048    boot/grub/core.img                             1
   2.508907318 = 2.693918720    boot/grub/grub.cfg                             1
   2.603157043 = 2.795118592    boot/initrd.img-2.6.32-29-generic              5
   2.543991089 = 2.731589632    boot/vmlinuz-2.6.32-29-generic                 2
   2.603157043 = 2.795118592    initrd.img                                     5
   2.543991089 = 2.731589632    vmlinuz                                        2

=============================== StdErr Messages: ===============================

unlzma: Decoder error




```

---

### Post by oldfred on 2011-06-17
Boot script looks normal and grub is installed in the MBR. It sees it as sda, but if you have everything else unplugged that would still be correct. Even if sda or hd0 is wrong the search by UUID is correct and should override and find correct partition.

Error seems like it is more from BIOS. On my system I have many options to boot USB devices and none of them will boot a flash drive. I thought mine did not work either, but then one day with flash plugged in I was changing hard drives to boot and there it was. It was under hard drives to boot not any USB devices. It has to be plugged in before booting and then select hard drive to boot.

---

### Post by cL0h on 2011-06-18
I was confirming for the upteenth time that I can in fact boot USB sticks from the BIOS when I gave the OCZ Rally2 another go and it booted. It booted and began doing a disk check and then after a minute or two the machine reset. Now it won't boot again at all. It booted before when I had it running a Live iso which is what had me think it was a software issue. 

So I strongly believe it is the USB stick. I'm not sure if reformatting it as ext messed it up? It is annoying because I bought it especially to use as a boot drive. (It got a great review at [http://www.pendrivereviews.com/ocz-rally-2/](http://www.pendrivereviews.com/ocz-rally-2/))

I'm going to rustle up an old USB stick and put PLOP on it to chain load the fancy speedy OCZ one for now.

Big thanks for the help oldfred I think I've learned more about Linux in the last week than I ever knew. In fact I'm writing this from a Virtualbox hosted XUbuntu right now. :)

---

### Post by oldfred on 2011-06-18
I have used Kingston,& Microcenter's house brand and some old noname flash drives without any issue (may not be quickest or best but have worked). Other have posted issues with certain brands and configurations.

---

