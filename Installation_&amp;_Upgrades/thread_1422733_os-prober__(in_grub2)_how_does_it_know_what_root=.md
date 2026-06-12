---
title: "os-prober  (in grub2) how does it know what root="
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by WOTHed on 2010-03-05
Hi all I cloned a  partion with  ubuntu installed (karmic).
I changes fstab accordingly and just deleted device.map so it would respawn correctly.

Prober almost gets it right when i run update-grub but it still points to the old partion in grub.cfg on that menu entry.

how does  prober know what root should = in the boot menu.
What do I need to edit in my cloned partion to appease it?


Thanks.

---

### Post by stlsaint on 2010-03-05
Please see the grub2 link in my signature.

---

### Post by WOTHed on 2010-03-06
> **stlsaint said:**
> Please see the grub2 link in my signature.

Very good grub 2 guide but that is not what I'm after.

I know the basics of grub2 to you put your settings into /etc/default/grub and /etc/grub.d/* run update-grub and it combibulates it all to grub.cfg

I also know I can use /etc/grub.d/40_custom to do stuff the old school way.

What I want to know is why os-prober produces this:

```
menuentry "Ubuntu, Linux <kernelbla> (on /dev/sdb2)" {
        insmod ext2
        set root=(hd1,1)
        search --no-floppy --fs-uuid --set <uuidbla>
        linux /vmlinuz-<kernelbla> root=/dev/sdb4 ro quiet splash
        initrd /initrd.img-<kernelbla>
```
My annoyance is root=/dev/sdb4 should be sdb2
Even the title says "on /dev/sdb2" !

this is a clone of ubuntu that is sitting on /dev/sdb4 so my only guess is that there is somthing os-prober is finding on the file system that makes it think its still on /dev/sdb4.

I can edit this entry at boot but  I don't want to do this every time.

I updated fstab what is os-prober doing?!

---

### Post by WOTHed on 2010-03-06
I would really love to know for my own education and hopefully to answer this problem:

How does os-prober decide what root= in that bit of the menuentry?

---

### Post by meierfra. on 2010-03-06
update-grub   looks at kernels, menu.lst;s and grub.cfg's to determine  the entries for grub.cfg. I'm not sure what exactly is happening in your case, so lets check out your system: Follow these [instructions]("http://bootinfoscript.sourceforge.net") to run the boot info script  and post the RESULTS.txt

---

### Post by WOTHed on 2010-03-06
> **meierfra. said:**
> update-grub   looks at kernels, menu.lst;s and grub.cfg's to determine  the entries for grub.cfg. 

I'll try the script thanks.

update-grub looks at grub.cfg?!  Is this what you mean?

I thought update-grub looks at settings placed in /etc/default/grub and /etc/grub.d/ and then OVERRIDES grub.cfg REGARDLESS of what was in it?

Or am I wrong here?

PS when I get home I'll try the script! :D

---

### Post by WOTHed on 2010-03-06
If update grub cares about grub.cfg I will delete the dam thing then run update-grub again.

---

### Post by meierfra. on 2010-03-06
update-grub will not look at  "grub.cfg" on the root partition.  But if you have a "grub.cfg" on a different partition (like  your  ubuntu   clone /dev/sda4) update-grub will look at that grub.cfg, modify those entries  and place them in the "os-prober" part of  grub.cfg.

---

### Post by WOTHed on 2010-03-08
> **meierfra. said:**
> update-grub will not look at  "grub.cfg" on the root partition.  But if you have a "grub.cfg" on a different partition (like  your  ubuntu   clone /dev/sda4) update-grub will look at that grub.cfg, modify those entries  and place them in the "os-prober" part of  grub.cfg.


/dev/sdb4  is the original the clone is /dev/sdb2 just to be clear.

I have a boot partition so grub.cfg is only  on /boot/ not on 2 or 4.

So if that rules out that then where  is os-prober geting the idea from  /dev/sdb2 that it needs root=/dev/sdb4 in its menuentry?

Again I have updated fstab on sdb2.

---

### Post by meierfra. on 2010-03-08
Please post the RESULTS.txt.

---

### Post by WOTHed on 2010-03-08
> **meierfra. said:**
> Please post the RESULTS.txt.

sda has some old operating systems by the way sda3 is ubuntu and sda4 is gentoo.

Maybe grub has pulled of these in sda's /boot menu.lst, still that would be stupid as there on a different hardrive.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /grub/menu.lst 
                       /boot/grub/grub.conf /grub/grub.conf

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 6.06.1 LTS
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [0;35;40m . [0;35;40m .vir. 
                       d$b [0;35;40m .d$$$$$$b. .cd$$b. .d$$b. d$$$$$$$$$$$b 
                       .d$$b. .d$$b. [0;35;40m $$$$( )$$$b d$$$()$$$. 
                       d$$$$$$$b Q$$$$$$$P$$$P.$$$$$$$b. .$$$$$$$b. 
                       [0;35;40m Q$$$$$$$$$$B$$$$$$$$P" d$$$PQ$$$$b. $$$$. 
                       .$$$P' `$$$ .$$$P' `$$$ [0;35;40m "$$$$$$$P Q$$$$$$$b 
                       d$$$P Q$$$$b $$$$b $$$$b..d$$$ $$$$b..d$$$ [0;35;40m 
                       d$$$$$$P" "$$$$$$$$ Q$$$ Q$$$$ $$$$$ `Q$$$$$$$P 
                       `Q$$$$$$$P [0;35;40m $$$$$$$P `""""" "" "" Q$$$P 
                       "Q$$$P" "Q$$$P" [0;35;40m `Q$$P" """ [0;37;40m This 
                       is .()
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ec2e8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       392,111       392,049  83 Linux
/dev/sda2             392,112     1,393,055     1,000,944  82 Linux swap / Solaris
/dev/sda3           1,393,056    31,394,159    30,001,104  83 Linux
/dev/sda4          31,394,160   156,301,487   124,907,328  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008560b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       594,404       594,342  83 Linux
/dev/sdb2             594,405     5,879,789     5,285,385  83 Linux
/dev/sdb3          27,961,118    28,961,118     1,000,001  82 Linux swap / Solaris
/dev/sdb4          28,965,195   156,360,644   127,395,450  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        uidbla------------------------------   ext2                                     
/dev/sda2        uidfoo------------------------------   swap                                     
/dev/sda3        uidmoo------------------------------   ext3                                     
/dev/sda4        uidegg------------------------------   ext3                                     
/dev/sdb1        uidham------------------------------   ext2                                     
/dev/sdb2        uidcheese---------------------------   ext3                                     
/dev/sdb3        uidbacon----------------------------   swap                                     
/dev/sdb4        uidbread----------------------------   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb4        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /boot                    ext2       (rw)


========================== sda1/boot/grub/grub.conf: ==========================

# Which listing to boot as default. 0 is the first, 1 the second etc.
default 0
# How many seconds to wait before the default listing is booted.
timeout 30
# Nice, fat splash-image to spice things up :)
# Comment out if you don't have a graphics card installed
#splashimage=(hd0,0)/boot/splash.xpm.gz

title=Gentoo Linux 2.6.23-r3
#Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-2.6.23-gentoo-r3 root=/dev/hda4
#
title=Gentoo with openvz for VEs  Kernel 2.6.18-028.027
#Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-2.6.18-openvz-tjos2-028.027 root=/dev/hda4



#ubntu stuf may not work
#
##
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
savedefault
boot
#
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd		/initrd.img-2.6.15-26-386
boot

============================= sda1/grub/grub.conf: =============================

# Which listing to boot as default. 0 is the first, 1 the second etc.
default 0
# How many seconds to wait before the default listing is booted.
timeout 30
# Nice, fat splash-image to spice things up :)
# Comment out if you don't have a graphics card installed
#splashimage=(hd0,0)/boot/splash.xpm.gz

title=Gentoo Linux 2.6.23-r3
#Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-2.6.23-gentoo-r3 root=/dev/hda4
#
title=Gentoo with openvz for VEs  Kernel 2.6.18-028.027
#Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-2.6.18-openvz-tjos2-028.027 root=/dev/hda4



#ubntu stuf may not work
#
##
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
savedefault
boot
#
title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd		/initrd.img-2.6.15-26-386
boot

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.conf
    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.15-26-386
    .0GB: boot/vmlinuz-2.6.15-26-386
    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.15-26-386
    .0GB: vmlinuz-2.6.15-26-386

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext2    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# noatime turns off atimes for increased performance (atimes normally aren't 
# needed; notail increases performance of ReiserFS (at the expense of storage 
# efficiency).  It's safe to drop the noatime options if you want and to 
# switch between notail / tail freely.
#
# The root filesystem should have a pass number of either 0 or 1.
# All other filesystems should have a pass number of 0 or greater than 1.
#
# See the manpage fstab(5) for more information.
#

# <fs>			<mountpoint>	<type>		<opts>		<dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
/dev/hda1		/boot		ext2		defaults,noatime	1 2
/dev/hda4		/		ext3		noatime		0 1
/dev/hda2		none		swap		sw		0 0
/dev/cdrom1	/mnt/cdrom	iso9660		noauto,ro,users	0 0
#/dev/fd0		/mnt/floppy	auto		noauto		0 0
#/dev/sda1		/mnt/usbmp3er	vfat		defaults,noauto,users,loop	0 0

# NOTE: The next line is critical for boot!
proc			/proc		proc		defaults	0 0

# glibc 2.2 and above expects tmpfs to be mounted at /dev/shm for 
# POSIX shared memory (shm_open, shm_unlink).
# (tmpfs is a dynamically expandable/shrinkable ramdisk, and will
#  use almost no memory if not populated with files)
shm			/dev/shm	tmpfs		nodev,nosuid,noexec	0 0

============================= sdb1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,4)
search --no-floppy --fs-uuid --set uidbread----------------------------
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set uidham------------------------------
	linux	/vmlinuz-2.6.31-17-generic-pae root=UUID=uidbread---------------------------- ro   quiet splash
	initrd	/initrd.img-2.6.31-17-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set uidham------------------------------
	linux	/vmlinuz-2.6.31-17-generic-pae root=UUID=uidbread---------------------------- ro single 
	initrd	/initrd.img-2.6.31-17-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set uidham------------------------------
	linux	/vmlinuz-2.6.31-14-generic-pae root=UUID=uidbread---------------------------- ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set uidham------------------------------
	linux	/vmlinuz-2.6.31-14-generic-pae root=UUID=uidbread---------------------------- ro single 
	initrd	/initrd.img-2.6.31-14-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set uidham------------------------------
	linux /vmlinuz-2.6.31-17-generic-pae root=/dev/sdb4 ro quiet splash
	initrd /initrd.img-2.6.31-17-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set uidham------------------------------
	linux /vmlinuz-2.6.31-17-generic-pae root=/dev/sdb4 ro single
	initrd /initrd.img-2.6.31-17-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set uidham------------------------------
	linux /vmlinuz-2.6.31-14-generic-pae root=/dev/sdb4 ro quiet splash
	initrd /initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set uidham------------------------------
	linux /vmlinuz-2.6.31-14-generic-pae root=/dev/sdb4 ro single
	initrd /initrd.img-2.6.31-14-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic-pae
    .0GB: initrd.img-2.6.31-17-generic-pae
    .0GB: vmlinuz-2.6.31-14-generic-pae
    .0GB: vmlinuz-2.6.31-17-generic-pae

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=uidcheese--------------------------- /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=uidham------------------------------ /boot           ext2    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=uidbacon---------------------------- none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=uidbread---------------------------- /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=uidham------------------------------ /boot           ext2    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=uidbacon---------------------------- none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb4: Location of files loaded by Grub: ===================


  14.8GB: initrd.img
  14.8GB: initrd.img.old
  14.8GB: vmlinuz
  14.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc 

```

---

### Post by meierfra. on 2010-03-08
It seems update-grub  does take the entries from your grub.cfg:

It finds Ubuntu on /dev/sdb2, determines that /dev/sdb1 is  the boot partition associated to /dev/sdb2 and so looks at the grub.cfg in /dev/sdb1 to determine the menuentry. So basically update-grub gets confused since you use the same boot partition for /dev/sdb2 and /dev/sdb4.

Anyway, see what happens if you delete grub.cfg and then run update-grub.

---

### Post by drs305 on 2010-03-08
WOTHed,

Since you mentioned cloning, I was interested in the UUIDs from meierfra.'s script. I thought you might have duplicate UUIDs after the cloning operation.

Did you really make the effort to rename the uuid's ham, cheese, etc? If so, that's pretty funny.

---

### Post by WOTHed on 2010-03-08
> **drs305 said:**
> WOTHed,
Did you really make the effort to rename the uuid's ham, cheese, etc? If so, that's pretty funny.

lol yes I did a find replace so they are all still accurate.

that is the only thing I edited.:D

---

### Post by WOTHed on 2010-03-08
> **meierfra. said:**
> It seems update-grub  does take the entries from your grub.cfg:

............

Anyway, see what happens if you delete grub.cfg and when run update-grub.

Ok will do when i come back from work later.

So far no one has mentioned any other file (and I changed fstab properly) So this seems the best guess at the moment. 

After that I think I will unplug sda, its just sitting there doing nothing.  Just to eliminate odds.

---

### Post by WOTHed on 2010-03-09
> **meierfra. said:**
> 
Anyway, see what happens if you delete grub.cfg and then run update-grub.

It worked! ... well sorta.
I suppose I'm getting someware now.

I'll try to rein-act:

rm /boot/gurb/grub.cfg
update-grub

At this point it worked menuentry now says /dev/sdb2 (yay)
Then I tried run it again to see what would happen
after first backing up cp /boot/grub/grub.cfg{,.bak} 

update-grub

Disaster!  grub.cfg the second time round strangely all changed to uuid's but the uuid was not for sdb2 it was again for sdb4

What the?  I don't get it worked like you said the fist time but the second time EVEN THOUGH grub.cfg was now correct it  override it with  a uuid which was sd4!

Where did gurb2/os-prober get that idea? it did it write the first time!

And now if I delete   grub.cfg I can not reproduce the good result.  .. Well maybe I need to delete grub.cfg.bak I guess.



I would love to have a doc on exactly how grub2/os-probers crazy mind works!!

I have seen reports that other things don't work in karmic like grub-reboot (or with probs) maybe I should just wait for LTS.

---

### Post by WOTHed on 2010-03-09
> **meierfra. said:**
> 
Anyway, see what happens if you delete grub.cfg and then run update-grub.

It worked! ... well sorta.
I suppose I'm getting someware now.

I'll try to rein-act:

rm /boot/gurb/grub.cfg
update-grub

At this point it worked menuentry now says /dev/sdb2 (yay)
Then I tried run it again to see what would happen
after first backing up cp /boot/grub/grub.cfg{,.bak} 

update-grub

Disaster!  grub.cfg the second time round strangely all changed to uuid's but the uuid was not for sdb2 it was again for sdb4

What the?  I don't get it worked like you said the fist time but the second time EVEN THOUGH grub.cfg was now correct it  override it with  a uuid which was sd4!

Where did gurb2/os-prober get that idea? it did it write the first time!

And now if I delete   grub.cfg I can not reproduce the good result.  .. Well maybe I need to delete grub.cfg.bak I guess.



I would love to have a doc on exactly how grub2/os-probers crazy mind works!!

I have seen reports that other things don't work in karmic like grub-reboot (or with probs) maybe I should just wait for LTS.

---

### Post by WOTHed on 2010-03-09
Ok rm  /boot/grub/grub.cfg* works

update-grub will work only once and then I have to

rm  /boot/grub/grub.cfg* again

(so even my grub.cfg.bak is read?)

otherwise running update-grub will put sdb4 instead of sdb2

This is crazy! what is going on here??

I guess this is solved-ish but I never read I have to delete grub.cfg all the time, os-prober is sposed to be handy this is a pain.

---

### Post by WOTHed on 2010-03-09
Ok update:

grub.cfg.bak which I made doesn't affect grub-update (sorry I was wrong)

If  /boot/grub/grub.cfg doesn't exist grub-update does the right thing on creating it and it say's /dev/sdb2 (but annoyingly not in uuid form).

If grub.cfg does exist even if made right (with sdb2) runing grub again  will replace sdb2 with the uuid form of sdb4!!

Now I understand if a kernel update is done grub-update is run?

@#%$@!

---

### Post by meierfra. on 2010-03-09
> If /boot/grub/grub.cfg doesn't exist grub-update does the right thing on creating it and it say's /dev/sdb2 (but annoyingly not in uuid form).

If grub.cfg does exist even if made right (with sdb2) runing grub again will replace sdb2 with the uuid form of sdb4!!

That does make sense.  "update-grub",  when creating the menuentry for /dev/sdb2, assumes that "grub.cfg" was created by the operating system on /dev/sdb2 so its looks at the "10_linux" part of grub.cfg  and not at the 30_osprober part.

There are a couple of options:

[list=1]
[*]  Create an entry for /deb/sdb2 in 40_custom and disable 30_os_prober
[*]  Edit 30_os_prober
[/list]

I don't have time right now to sort out the details, but I'll look into into tonight.

---

### Post by WOTHed on 2010-03-09
> **meierfra. said:**
> 
There are a couple of options:

[list=1]
[*]  Create an entry for /deb/sdb2 in 40_custom and disable 30_os_prober
[*]  Edit 30_os_prober
[/list]

I don't have time right now to sort out the details, but I'll look into into tonight.

Thanks a lot for you guidance so far.

Option 3 might be to submit a bug report and hope this doesn't  happen in Lucid LTS.

---

### Post by dom22 on 2010-12-29
Hi,

I don't use Ubuntu (sorry...) but perhaps this can help :

I had a similar problem with Debian.
I cloned the system partition before upgrading from 5.0 to 6.0 (and from grub legacy to grub2).
For me, clone is sda4, original is sda1
And upgrade-grub2 (os-prober) generates a wrong "root=/dev/sda1" in the menu entry that should boot the old release.

The solution for me was to delete the /boot/grub/menu.lst  in the cloned partition sda4,
and them re-run upgrade-grub2
It seems that update-grub2 takes some info from this file.

After this deletion, I don't have menu entries begining with "Grub sda4" anymore.
I have entries "Debian GNU/Linux (5.0.7) (on /dev/sda4)" with the correct root
(root=/dev/sda4)

---

