---
title: "grub2 timeout problem"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by prazzb on 2011-01-01
I have a very unique problem as regards to grub2.

I installed meerkat and then installed backtrack4 (did not install bootloader).On rebooting, it came back to meerkat with no error (was expected)

I ran **sudo update-grub **and last line showed **found ubuntu 8.10 on /dev/sda2**. (This is also expected as backtrack's wiki page on dual boot shows the same i.e ubuntu 8.10).My meerkat is on /dev/sda1

When I reboot, there is no timeout. Even on pressing shift grub menu only flashes for a second or so and it boots into meerkat.

I then changed /etc/default/grub but still no difference.Plzzz help me.I still haven't booted into backtrack.

My /etc/default/grrub's initial lines:
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=100
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=" splash"

---

### Post by drs305 on 2011-01-01
If you run the boot info script and post the contents of the RESULTS.txt it may show what is happening:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

In the meantime, you can edit the grub.cfg file and set the timeout to -1 to see if that at least displays the menu until you make a selection. Since you already have a 100 second delay, this shouldn't be necessary and may not solve it, even temporarily. 

If this doesn't work it's possible your system may be using a different grub.cfg. The RESULTS.txt should clarify things.

Note that if you run update-grub any change you make to grub.cfg will be overwritten:

Open the file for editing:
```
gksu gedit +60 /boot/grub/grub.cfg
```

Replace this section:
> 
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  [COLOR="Red"]set timeout=100[/COLOR]
fi
with:
> 
#if [ "${recordfail}" = 1 ]; then
#  set timeout=-1
#else
  [COLOR="Red"]set timeout=-1[/COLOR]
#fi
Save the file. Do not update-grub. Reboot.

---

### Post by prazzb on 2011-01-01
no change after changing grub.cfg

results.txt attached

---

### Post by wilee-nilee on 2011-01-01
Always post the request, if you can.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    64,002,959    64,002,897  83 Linux
/dev/sda2          64,002,960    88,004,069    24,001,110  83 Linux
/dev/sda3         107,217,810   117,210,239     9,992,430  82 Linux swap / Solaris
/dev/sda4          88,004,070   107,217,809    19,213,740  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        cd55e827-9a48-4d88-ac90-61ed1cd5bdd5   ext3                                     
/dev/sda2        8e417095-cd9b-41c4-87e6-29bd9a661e0b   ext3                                     
/dev/sda3        cd480c7f-2e52-41ce-a09d-06f67922a717   swap                                     
/dev/sda4        d6865560-ba7f-4422-9056-0f91b45243e7   ext3       LFS                           
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set cd55e827-9a48-4d88-ac90-61ed1cd5bdd5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set cd55e827-9a48-4d88-ac90-61ed1cd5bdd5
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=100
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set cd55e827-9a48-4d88-ac90-61ed1cd5bdd5
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=cd55e827-9a48-4d88-ac90-61ed1cd5bdd5 ro  splash  
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set cd55e827-9a48-4d88-ac90-61ed1cd5bdd5
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=cd55e827-9a48-4d88-ac90-61ed1cd5bdd5 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set cd55e827-9a48-4d88-ac90-61ed1cd5bdd5
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=cd55e827-9a48-4d88-ac90-61ed1cd5bdd5 ro  splash  
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set cd55e827-9a48-4d88-ac90-61ed1cd5bdd5
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=cd55e827-9a48-4d88-ac90-61ed1cd5bdd5 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set cd55e827-9a48-4d88-ac90-61ed1cd5bdd5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set cd55e827-9a48-4d88-ac90-61ed1cd5bdd5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Memory Test (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 8e417095-cd9b-41c4-87e6-29bd9a661e0b
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 8e417095-cd9b-41c4-87e6-29bd9a661e0b
	linux /boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro vga=0x317
	initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (recovery mode) (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 8e417095-cd9b-41c4-87e6-29bd9a661e0b
	linux /boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro single
	initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 8e417095-cd9b-41c4-87e6-29bd9a661e0b
	linux /boot/memtest86+.bin 
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=cd480c7f-2e52-41ce-a09d-06f67922a717 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.3GB: boot/grub/core.img
   6.2GB: boot/grub/grub.cfg
   6.3GB: boot/initrd.img-2.6.35-22-generic
   6.3GB: boot/initrd.img-2.6.35-24-generic
   6.2GB: boot/vmlinuz-2.6.35-22-generic
   6.2GB: boot/vmlinuz-2.6.35-24-generic
   6.3GB: initrd.img
   6.3GB: initrd.img.old
   6.2GB: vmlinuz
   6.2GB: vmlinuz.old

=========================== sda2/boot/grub/menu.lst: ===========================

# By default, boot the first entry.
default 0

# Boot automatically after 30 secs.
timeout 30

vga=0x317image=/boot/grub/bt4.xpm.gz


title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title                Memory Test
kernel                /boot/memtest86+.bin

title                Boot the First Hard Disk
root                (hd0)
chainloader +1
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a76c7835-eb6f-459f-a891-496f16bc00eb

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

splashimage=a76c7835-eb6f-459f-a891-496f16bc00eb/boot/grub/splash.xpm.gz

title		Ubuntu 8.10, kernel 2.6.30.9
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro vga=0x317 
initrd		/boot/initrd.img-2.6.30.9
quiet

title		Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=a76c7835-eb6f-459f-a891-496f16bc00eb ro  single
initrd		/boot/initrd.img-2.6.30.9

title		Ubuntu 8.10, memtest86+
uuid		a76c7835-eb6f-459f-a891-496f16bc00eb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8e417095-cd9b-41c4-87e6-29bd9a661e0b /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda3
UUID=cd480c7f-2e52-41ce-a09d-06f67922a717 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  38.9GB: boot/grub/menu.lst
  38.8GB: boot/grub/stage2
  38.8GB: boot/initrd.img-2.6.30.9
  38.8GB: boot/vmlinuz-2.6.30.9
  38.8GB: initrd.img
  38.8GB: vmlinuz
```

---

### Post by Quackers on 2011-01-01
wilee-nilee beat me to it :-)

---

### Post by drs305 on 2011-01-01
Your files look normal and I've imported your settings into my system and the Grub2 menu displays and counts down.

Since setting the recordfail to -1 should have displayed the menu, and it does display in my computer, I'd recommend the following steps.

1, Boot to Ubuntu. Ensure G2 is using the correct files:
```
sudo grub-install /dev/sda
sudo update-grub
```
Watch to make sure it finds the second OS. Reboot. If there is still no display:

2. Purge & reinstall G2. Since you can boot into your installation, it is a very simple process.

```
sudo apt-get update  # Make sure your Internet cnx is working. Do not proceed if it is not.
sudo apt-get purge grub-common  # Will remove grub-pc & grub-common. 
# Tab to OK when asked.
sudo apt-get install grub-pc # Will reinstall grub-common and grub-pc. 
# Install only to sda with the spacebar, then TAB to OK. Do *not* select the partition.
```
It should run update-grub at the end, if it doesn't run it manually. Open /etc/default/grub and change the timeout if desired. It should be set to 10 seconds and pause on boot as long as it has found the second OS. If you change the timeout manually, don't forget to update-grub again.

---

### Post by patond on 2011-12-11
I too have this problem.  The grub menu is shown and I can choose which option I want, but there is no timeout countdown,  Here are the contents of RESULTS.TXT

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 296927544 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 296927544 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /dev/sda7 already mounted or sda7 busy

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2         168,847,358   312,580,095   143,732,738   5 Extended
/dev/sda5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris
/dev/sda6         168,847,360   236,818,431    67,971,072  83 Linux
/dev/sda7         236,820,480   304,791,551    67,971,072  83 Linux
/dev/sda3          82,399,232   168,845,311    86,446,080  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda3        2a41cdec-9f08-4909-8228-832438ae74af   ext4       data
/dev/sda5        4e0e93c8-b31f-4ae3-a233-e82fb4c6e3f2   swap       
/dev/sda6        bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1   ext4       oneiric
/dev/sda7        bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1   ext4       oneiric

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/data              ext4       (rw,commit=0)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
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
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-13-generic
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=bea2cbcd-49c8-4df8-a936-3ec7b7f2afb1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4e0e93c8-b31f-4ae3-a233-e82fb4c6e3f2 none            swap    sw              0       0
# data is installed on /dev/sda3
UUID=2a41cdec-9f08-4909-8228-832438ae74af  /media/data   ext4  defaults  0   2
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-13-generic               1
               =                boot/vmlinuz-3.0.0-13-generic                  2
               =                initrd.img                                     1
               =                vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  80 d3 9b 09 3b 1e d4 89  12 f2 d9 3b 77 86 53 75  |....;......;w.Su|
00000010  98 05 fb cc eb c2 1e 36  99 f0 7f f2 4b 25 ce e0  |.......6....K%..|
00000020  e8 b3 7b 62 a1 75 1a 82  b6 7e 81 ea 60 64 1f 00  |..{b.u...~..`d..|
00000030  00 76 77 77 88 86 88 87  69 87 99 98 99 98 aa 98  |.vww....i.......|
00000040  99 98 89 97 a9 b9 8a a9  aa 98 7a a8 aa 89 7a 98  |..........z...z.|
00000050  ab 88 99 79 98 98 ba 89  99 88 89 99 88 89 9a 8a  |...y............|
00000060  98 ba ab 98 b7 b9 a8 aa  ba a9 98 66 99 a9 bb 8a  |...........f....|
00000070  aa 88 6a 78 aa 69 59 7b  aa ba cc cc d0 bd ab aa  |..jx.iY{........|
00000080  cc 9a bb ba cb ba ab cb  cc bb cb ab 89 99 a9 bc  |................|
00000090  ba 77 88 b9 88 88 99 ba  aa 99 a9 cb ac 88 9a 99  |.w..............|
000000a0  a9 98 a9 a9 a9 76 7a a8  aa 98 89 b8 88 98 99 a8  |.....vz.........|
000000b0  68 ab ed e0 de de 0e 00  ae e0 00 00 00 00 00 00  |h...............|
000000c0  00 a8 bc 0e 00 ee 00 00  0e 98 99 db 0e 00 0e 00  |................|
000000d0  d0 97 a9 ba cc dc dc ce  d9 97 a9 ab be ed ed e0  |................|
000000e0  ab 87 a9 ca bc ed dd ed  ac 87 99 bb cb cb cb ce  |................|
000000f0  be 86 a9 ba 0c cc ec 0c  bd 76 99 ac bb ec cd 0e  |.........v......|
00000100  ad 76 a9 bc bb cc dc ee  ae 76 a8 eb cc ed dd dd  |.v.......v......|
00000110  bd 76 a9 bb bd dd dd d0  bc 86 ba dc 0d dd 00 00  |.v..............|
00000120  d0 a9 dd 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 d1 5d d0 75 33 21 c8  4c 0f 8b ca 31 64 e5 57  |..].u3!.L...1d.W|
00000140  02 98 a0 0d 46 5d 06 22  18 8f 92 50 5a 15 c9 9f  |....F]."...PZ...|
00000150  30 e6 9a d1 5e 99 09 0c  8f fd 0f 11 11 46 e9 3b  |0...^........F.;|
00000160  48 13 05 6f fd 3a f3 f0  2e 49 05 b4 02 20 0f b1  |H..o.:...I... ..|
00000170  0e 41 88 12 05 e6 2b 0b  6f 83 61 50 41 17 23 81  |.A....+.o.aPA.#.|
00000180  ba 90 33 55 b7 3a 4c a7  9e c7 a9 f4 4f 1a 5f 0c  |..3U.:L.....O._.|
00000190  79 4b 8e 08 8f bc 9a 76  67 9f 54 57 8a be fc 3f  |yK.....vg.TW...?|
000001a0  0a 3b 2c 93 cd 85 f8 be  f0 6f f7 af 92 0e 0a 51  |.;,......o.....Q|
000001b0  42 22 ac fe 08 bc fc 86  fc d8 be ce 76 78 00 fe  |B"..........vx..|
000001c0  ff ff 82 fe ff ff 02 88  33 08 00 a8 5d 00 00 fe  |........3...]...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 28 0d 04 00 00  |...........(....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by drs305 on 2011-12-11
patond,

First, you have two partitions with the same UUID. I would change the UUID of sda7 (your non-Ubuntu partition) to something else. You can do this with *tune2fs*, using the command below. It will set the sda7 UUID to some random value:
```
sudo tune2fs -U random /dev/sda7
sudo blkid /dev/null
```
The second command will show you the new UUID for sda7. You don't have sda7 listed in fstab so you shouldn't have to make any other changes.

Next update grub. At some point it was installed on partitions, so make sure you put it in the MBR with "sda" and NOT "sda6".
```

sudo grub-install /dev/sda
sudo update-grub
```
See if the timeout now works. It's currently set to 3 seconds.

---

### Post by patond on 2011-12-12
Thank you drs305 that's fixed it. I had created a duplicate ubuntu 11.10 OS using copy in gparted in order to test things out without screwing things up.

---

### Post by drs305 on 2011-12-12
:-)


Since there were several 'helpers' monitoring this thread would you please mark it SOLVED via the 'Thread Tools' link near the top right of the first post?  Thanks.

Happy Ubuntu-ing !

---

### Post by patond on 2011-12-13
Thread Tools doesn't have this option.  Sorry.  Thanks for all your help.

---

### Post by drs305 on 2011-12-13
> **patond said:**
> Thread Tools doesn't have this option.  Sorry.  Thanks for all your help.

Forgot you weren't the OP. It's only available to the original poster and moderators.

---

