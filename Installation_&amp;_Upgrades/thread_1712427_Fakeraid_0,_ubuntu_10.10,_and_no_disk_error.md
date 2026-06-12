---
title: "Fakeraid 0, ubuntu 10.10, and no disk error"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by bp787 on 2011-03-22
hello.
 
I have been building a HTPC and intended on using Ubuntu.  I am no stranger to Unix/Linux, but have mostly been in the Solaris and Fedora/Redhat world, so Ubuntu is just a little bit different to me. :)
 
I have a new ASRock 880G/USB3 RC 2.0 motherboard that supports Raid 0,1, etc...  I configured the Mobo to use both of my 120GB 5400RPM 2.5" laptop SATA drives as Raid 0.  I then proceeded to install 10.10.  It seemed to recognize the raid array just fine.  Upon install completion, I immediately end up at the grub-rescue> prompt with the following error:
 
grub-rescue> No Such Disk
 
I have read till my eyes bleed and attempted a number of things, including modifying the liveCD's boot paramters to include:  libata.ignore_hpa=0, which did have some slight effect on how the partitioner identified the array.  However, when attempting follow the rest of the steps found at [http://samueltaylor.me.uk/2011/01/31/setting-up-nvidia-nforce-fakeraid-on-ubuntu-10-10/](http://samueltaylor.me.uk/2011/01/31/setting-up-nvidia-nforce-fakeraid-on-ubuntu-10-10/) , I was unable to enter the boot loader after reboot by pressing SHIFT during initial boot.  Tried this a few times without success.
 
I have also attempted a number of actions while in grub-rescue.  ls reports nothing back.  set reports something like:  (hd0,msdos)/boot/grub  I will have to wait until I get home to put the exact output up here.
 
So, I'm assuming that the boot partition is on the wrong place on the drive.  Any thoughts on how to correct this?  I'm about to install to a single 7200RPM or do software raid only, as I've spent about 3 days on this.  I may try a fedora 14 disk just for the hell of it and see what it does.
 
Thanks for any help you can provide!  
 
-Drew

---

### Post by Hedgehog1 on 2011-03-23
> ASRock 880G/USB3 RC 2.0 motherboard that supports Raid 0,1, etc... I configured the Mobo to use both of my 120GB 5400RPM 2.5" laptop SATA drives as Raid 0

Can we get a look at the drives and partitions?  That would allow us to see if we can help.

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by bp787 on 2011-03-23
Thanks for any help.  I think I see a few potential errors, but will let you all look and see what you find.

```
 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/mapper/pdc_djejhceeej and looks on 
    the same drive in partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

pdc_djejhceeej1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

pdc_djejhceeej2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_djejhceeej5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1                 256   445,917,951   445,917,696  83 Linux
/dev/sda2         445,918,206   464,843,519    18,925,314   5 Extended
Invalid MBR Signature found
/dev/sda5     ?   445,918,206   445,918,205                   Unknown
/dev/sda6     ?   445,918,206   445,918,205                   Unknown

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda2

Drive: pdc_djejhceeej ___________________ _____________________________________________________

Disk /dev/mapper/pdc_djejhceeej: 238.0 GB, 237999882240 bytes
255 heads, 63 sectors/track, 28935 cylinders, total 464843520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_djejhceeej1                256   445,917,951   445,917,696  83 Linux
/dev/mapper/pdc_djejhceeej2        445,918,206   464,843,519    18,925,314   5 Extended
/dev/mapper/pdc_djejhceeej5        445,918,208   464,843,519    18,925,312  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_djejhceeej1 92d3327b-e878-4fec-9dc9-93508e22ebcc   ext4                                     
/dev/mapper/pdc_djejhceeej5 d1d8e15b-902c-48e5-bd34-5fca995e873c   swap                                     
/dev/mapper/pdc_djejhceeej: PTTYPE="dos" 
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb                                                promise_fasttrack_raid_member                               
error: /dev/mapper/pdc_djejhceeej2: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_djejhceeej
pdc_djejhceeej1
pdc_djejhceeej5

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


===================== pdc_djejhceeej1/boot/grub/grub.cfg: =====================

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
set root='(/dev/mapper/pdc_djejhceeej,msdos1)'
search --no-floppy --fs-uuid --set 92d3327b-e878-4fec-9dc9-93508e22ebcc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/mapper/pdc_djejhceeej,msdos1)'
search --no-floppy --fs-uuid --set 92d3327b-e878-4fec-9dc9-93508e22ebcc
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
    set root='(/dev/mapper/pdc_djejhceeej,msdos1)'
    search --no-floppy --fs-uuid --set 92d3327b-e878-4fec-9dc9-93508e22ebcc
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=92d3327b-e878-4fec-9dc9-93508e22ebcc ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/pdc_djejhceeej,msdos1)'
    search --no-floppy --fs-uuid --set 92d3327b-e878-4fec-9dc9-93508e22ebcc
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=92d3327b-e878-4fec-9dc9-93508e22ebcc ro single 
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
    set root='(/dev/mapper/pdc_djejhceeej,msdos1)'
    search --no-floppy --fs-uuid --set 92d3327b-e878-4fec-9dc9-93508e22ebcc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/pdc_djejhceeej,msdos1)'
    search --no-floppy --fs-uuid --set 92d3327b-e878-4fec-9dc9-93508e22ebcc
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

========================== pdc_djejhceeej1/etc/fstab: ==========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pdc_djejhceeej1 /               ext4    errors=remount-ro 0       1
/dev/mapper/pdc_djejhceeej5 none            swap    sw              0       0

============== pdc_djejhceeej1: Location of files loaded by Grub: ==============


 171.9GB: boot/grub/core.img
 171.9GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
 171.9GB: boot/vmlinuz-2.6.35-22-generic
    .9GB: initrd.img
 171.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on pdc_djejhceeej2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/mapper/pdc_djejhceeej2: No such file or directory
hexdump: /dev/mapper/pdc_djejhceeej2: No such file or directory
 
```

---

### Post by ronparent on 2011-03-23
Is the raid drive set as your boot drive in bios (ie /dev/mapper/pdc_djejhceeej)? If it is the boot setor on that raid drive (/dev/mapper/pdc_djejhceeej) points to the correct raid partition (/dev/mapper/pdc_djejhceeej1 and should boot!

The sda drive on the other hand is a raid member along wit sdb. There should be no boot loader on sda and the system normally prevents you from writing one there.

---

### Post by bp787 on 2011-03-23
I will check here in about an hour, but it does default to booting the HD at startup, but I will check the specifics as to if it's calling out the individual drive or if it is correctly booting the raid device.
 
As a side note, and not sure that it matters, the SATA connections are on SATA 3 and 4 respectively on the Mobo.  I coudn't  find anything that says this will cause boot problems in the Mobo documentation, but I have experienced this in the past with certain boards.  I only did this because Sata 1 and 2 are right in the way of the Power supply cabling run and it makes it difficult to get everything routed.
 
Might be worth me plugging them into 1 and 2 just for the heck of it.

---

### Post by bp787 on 2011-03-23
yes, the BIOS is detecting the HD as "Raid Ary 1" for first boot device.

---

### Post by ronparent on 2011-03-24
Try a grub reinstall, really simple two step.

Step 1 - from a live cd terminal, mount your install partition:
> sudo mount /dev/mapper/pdc_djejhceeej1 /mnt
Step 2 - do the reinstall
> sudo grub-install --root-directory=/mnt/ /dev/mapper/pdc_djejhceeej
If it doesn't boot properly now we will try something else.

Your results from the boot script seems to be OK and so is your boot order. But a reinstall as above is quick and simple and should work if it is only a minor quirk now affecting you. Post how you make out.

---

### Post by bp787 on 2011-03-30
The grub re-install seems to have corrected the issue.  I haven't yet checked to see what has changed. 
 
Now, on to my other, non RAID Ubuntu problems :D

---

