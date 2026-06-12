---
title: "I give up.. can´t upgrade, can´t install"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by helmarfernandes on 2010-10-25
Hi guys...
I´m loosing my hopes...

I have a laptop HD pavilion DV6910us and I always had problems with installation of other OS in there.
When I was trying to install Ubuntu 9.10 in it I always had the "I/O error"... "error no05"... 
Until someone told me to disable ACPI in installation options...
After very times I managed to install 9.10 on it.

OK... everything was working fine... until I decided to upgrade last week to 10.04...
I have had alll kinds of problems during the upgrade using the update manager... after FIVE days os work lost (and money lost consequently) I could log in my laptop... but there´s no nautilus runing, no window manager, no sound... I can run some programs by Cairo Doc Bar.... but the windows has no close button, minimize or maximize... I´ve already tried to run compiz again, replace metacity, but nothing seems to work...
I´m desperated ´cause I need my machine to work... there is no other OS in there.. almost 100GB of information in my home folder and no backup..
When I try to install the 10.10 version I have the feared message (unexpected error) after 60% of progress asking me to check my disc... Even if I use the NOACPI option it doesn´t work...
The disc is OK... I tested it in another machine... 

PLEASE HELP ME!!!

---

### Post by wilee-nilee on 2010-10-25
> **helmarfernandes said:**
> Hi guys...
I´m loosing my hopes...

I have a laptop HD pavilion DV6910us and I always had problems with installation of other OS in there.
When I was trying to install Ubuntu 9.10 in it I always had the "I/O error"... "error no05"... 
Until someone told me to disable ACPI in installation options...
After very times I managed to install 9.10 on it.

OK... everything was working fine... until I decided to upgrade last week to 10.04...
I have had alll kinds of problems during the upgrade using the update manager... after FIVE days os work lost (and money lost consequently) I could log in my laptop... but there´s no nautilus runing, no window manager, no sound... I can run some programs by Cairo Doc Bar.... but the windows has no close button, minimize or maximize... I´ve already tried to run compiz again, replace metacity, but nothing seems to work...
I´m desperated ´cause I need my machine to work... there is no other OS in there.. **almost 100GB of information in my home folder and no backup..**
When I try to install the 10.10 version I have the feared message (unexpected error) after 60% of progress asking me to check my disc... Even if I use the NOACPI option it doesn´t work...
The disc is OK... I tested it in another machine... 

PLEASE HELP ME!!!

This bold part is certainly a important point. If you had everything backed up you could then start trying fresh installs to find a working OS, it may be that this computer would run best on the original MS OS, I don't know. 

Upgrading without a backup is a not a smart practice. Sorry to be to the point, but you will get the same basic advice from others on the forum.

You mention the 100 gigs in home, is this on a separate partition?, it will be helpful for others to know this.

---

### Post by sikander3786 on 2010-10-25
It would be better to backup all your data and try to reinstall 10.04. Upgrades seem to cause problems sometimes, to be honest most of the times for me.

10.04 has worked on almost all the hardware I have. Nearly 15 PCs and all without any problems whatsoever.

Can you try to boot a 10.04 Live CD and if successful, test your hardware. If everything works, mount your data partition, copy it over to a safe location and reinstal Ubuntu 10.04. It will be supported till 2013 so if you get it working, no real hurry for upgrading. In the mean time you can think of an alternative if you want one.

---

### Post by helmarfernandes on 2010-10-25
> **sikander3786 said:**
> It would be better to backup all your data and try to reinstall 10.04. Upgrades seem to cause problems sometimes, to be honest most of the times for me.

10.04 has worked on almost all the hardware I have. Nearly 15 PCs and all without any problems whatsoever.

Can you try to boot a 10.04 Live CD and if successful, test your hardware. If everything works, mount your data partition, copy it over to a safe location and reinstal Ubuntu 10.04. It will be supported till 2013 so if you get it working, no real hurry for upgrading. In the mean time you can think of an alternative if you want one.


Hey guys... I know upgrading without a backup is a foolishness...
But for me I supposed to only a simple "update"... I didn't expect for all those problems...

The data is on sda1, thje only logical partition... I created another partition with GParted where I tried to install the 10.10...

I thank you for your response but this kind a comments doesnt helps me

---

### Post by kansasnoob on 2010-10-25
What Live CD's do you have available?

We need some idea of what's going on, the partitioning arrangement, etc. So if you have any Ubuntu Live CD, regardless of age, please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

We may or may not be able to rescue the OS, but we can almost certainly save your data if you're patient and stop freaking out!

There are alternate instructions for using the Boot Info Script here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

BUT! If you can't get a 10.10 Ubuntu Live CD to run on your machine I have doubts that you'll be able to use 10.10. I'd prefer if you could use a known good 10.04.1 Live CD because it's LTS and you said, "I always had problems with installation of other OS".

If you have enough disc space we can create a new OS and you can then move data from the "dead" OS to the new one.

It would also be helpful to see the output of:

```
cat /proc/cpuinfo
```

```
lspci | grep VGA
```

```
free
```

Troubleshoot first ........... freakout later :)

---

### Post by helmarfernandes on 2010-10-25
Ok kansasnoob... lets stop freaking (whatever it be)... I m a brazilian guy 

Here's the cpuinfo results

> root@helmar-desktop:/proc# cat cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-60
stepping	: 2
cpu MHz		: 2000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 4000.28
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-60
stepping	: 2
cpu MHz		: 2000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 4000.40
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps


---

### Post by helmarfernandes on 2010-10-25
by the way... I can login into my native OS (Ubuntu 10.04 recently upgraded) but with no nautilus, no window manager, no close, minimize buttons, no sound, no changing language in my keyboard, etc just as I said...
I also can login with 9.10 live cd or 10.10 live cd

---

### Post by wilee-nilee on 2010-10-25
The bootscript will be the biggest help as well if you can.;) As well as the two other commands kansasnoob gave you. When you copy and paste text to a reply use the code tags, click on the # in the reply panel and put the text in between the code tags generated.

---

### Post by helmarfernandes on 2010-10-25
OK... this is the bootscript info

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   255,738,734   255,738,672  83 Linux
/dev/sda2         602,871,316   625,137,344    22,266,029   5 Extended
/dev/sda5         602,871,318   625,137,344    22,266,027  82 Linux swap / Solaris
/dev/sda3         255,739,904   602,869,759   347,129,856  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2bc73fd9-7eb8-4240-b38a-9aaacb9260e3   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        14d04670-9075-4c1a-8e0e-82471280c9c7   ext4                                     
/dev/sda5        6f8026fb-4d88-46ef-a59f-3e4012017e2e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2bc73fd9-7eb8-4240-b38a-9aaacb9260e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=2bc73fd9-7eb8-4240-b38a-9aaacb9260e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=2bc73fd9-7eb8-4240-b38a-9aaacb9260e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=2bc73fd9-7eb8-4240-b38a-9aaacb9260e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=2bc73fd9-7eb8-4240-b38a-9aaacb9260e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    echo    'Loading Linux 2.6.31-16-generic ...'
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=2bc73fd9-7eb8-4240-b38a-9aaacb9260e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=2bc73fd9-7eb8-4240-b38a-9aaacb9260e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    echo    'Loading Linux 2.6.31-15-generic ...'
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=2bc73fd9-7eb8-4240-b38a-9aaacb9260e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2bc73fd9-7eb8-4240-b38a-9aaacb9260e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2bc73fd9-7eb8-4240-b38a-9aaacb9260e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2bc73fd9-7eb8-4240-b38a-9aaacb9260e3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2bc73fd9-7eb8-4240-b38a-9aaacb9260e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6f8026fb-4d88-46ef-a59f-3e4012017e2e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 101.4GB: boot/grub/core.img
  41.4GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-14-generic
    .6GB: boot/initrd.img-2.6.31-15-generic
    .2GB: boot/initrd.img-2.6.31-16-generic
   6.5GB: boot/initrd.img-2.6.31-22-generic
  11.0GB: boot/initrd.img-2.6.32-25-generic
    .3GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-15-generic
   1.3GB: boot/vmlinuz-2.6.31-16-generic
   5.1GB: boot/vmlinuz-2.6.31-22-generic
   6.0GB: boot/vmlinuz-2.6.32-25-generic
  11.0GB: initrd.img
   6.5GB: initrd.img.old
   6.0GB: vmlinuz
   5.1GB: vmlinuz.old

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=14d04670-9075-4c1a-8e0e-82471280c9c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6f8026fb-4d88-46ef-a59f-3e4012017e2e none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
000001b0  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 ab c0 53 01 00 00  |............S...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by helmarfernandes on 2010-10-25
here`s the lscpi results

> 00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)


---

### Post by helmarfernandes on 2010-10-25
and finally the free command results

>          total       used       free     shared    buffers     cached
Mem:       3799760    1162000    2637760          0     117824     509720
-/+ buffers/cache:     534456    3265304
Swap:     11133008          0   11133008


---

### Post by helmarfernandes on 2010-10-25
Sorry man... now I understand the code tags issue

---

### Post by helmarfernandes on 2010-10-26
I've sent you all the things you ask me.

Could someone help me?

---

