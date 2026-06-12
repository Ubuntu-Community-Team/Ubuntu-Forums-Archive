---
title: "boot failure after kernel update"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by jtmedin on 2011-03-25
Its getting so i do not suggest ubuntu to my friends. It started several months  ago on my tower. After a kernel update ubuntu would not boot. So found this procedure using the live update cd. Update grub.cfg & delete everything down to but not including the first line that starts with 'menuentry' . Then boot works ok. A couple of weeks ago it started on my notebook. Is anyone @ hq listening & able to fix this problem permanently? Or am i doing something stupid? TIA

---

### Post by Quackers on 2011-03-25
If a new kernel doesn't boot and you have only Ubuntu installed on the drive, hold down the shift key whilst booting and the grub menu should appear (on later versions). Instead of booting the latest kernel choose an older kernel and boot that.

---

### Post by drs305 on 2011-03-25
You most likely aren't doing anything wrong if you haven't tinkered with the grub scripts. By removing all the lines prior to the first menuentry you are essentially taking many of the grub scripts out of play. (It may even have been one of my posts that recommended this procedure.  ;-) ).

Although there have been updates of most versions of Grub2, it is possible you have something wrong with one of the Grub2 files.

I would recommend booting into your normal Ubuntu system, *ensuring you have an Internet connection*, and then purging and reinstalling Grub2. It's been very stable for most people and you shouldn't be having problems. By purging rather than just reinstalling, you will be ensuring that any damaged file or file moved/renamed/deleted by you is returned to its original status and location.

```
sudo apt-get update # Ensure you have a working Internet connection
sudo apt-get purge grub-common  # Purges grub-common and grub-pc
sudo apt-get install grub-pc  # Installs grub-common and grub-pc
```

As it reinstalls, you will be asked about kernel options. Tab to OK if you don't add any special instructions to the kernel line. 

When asked where to install it, select *only* the drive; do not select any of the partitions. Select the drive with the spacebar, then tab to OK.

Reboot.

---

### Post by garvinrick4 on 2011-03-25
+1 on Quackers:
From an article I read by Linus Torvalds there are 10,000 lines of code added daily
and 5,000 removed. To have an occasional boot failure by a new kernel trying to adapt
to so many different versions of hardware and drivers is not that bad. That is why you
should keep 2 or 3 different kernels installed to boot from at all times. I think it is fantastic
that the rate you actually get a boot failure from a new kernel being upgraded as often as 
they are is remarkable in itself. There is a learning curve when starting Ubuntu linux just as 
there was when someone started using Windows or Mac. I have used all 3 and prefer Ubuntu Linux and am proud of it being what it is.

EDIT: I see you have drs305 in your thread, there are a lot of good tutorials out there but in drs305 signature there
are a few that are nice, put them in your bookmarks and read them as time permits and practice using code until you understand
not only the code but the why. Also find one on dpkg command will help in some occasions. Linux really is remarkable
if you have the want to learn. Enjoy your Ubuntu and do tell your friends to give it a go, they might thank you one day.

---

### Post by drs305 on 2011-03-25
I agree about keeping and trying an older kernel, but if the OP is editing grub.cfg and only removing everything prior to the first menuentry then Grub would still be booting the same kernel entry unless he has modified the default settings in /etc/default/grub.

---

### Post by garvinrick4 on 2011-03-25
> **drs305 said:**
> I agree about keeping and trying an older kernel, but if the OP is editing grub.cfg and only removing everything prior to the first menuentry then Grub would still be booting the same kernel entry unless he has modified the default settings in /etc/default/grub. Understood and would not update-grub or grub-mkconfig just
make a new /boot/grub/grub.cfg if attempting to edit /boot/grub/grub.cfg would not be
a permanent edit. I imagine as you stated to purge and reinstall grub could only help to
get back to correct grub.cfg and menu entry's.
 *I have always purged grub-common grub-pc and installed grup-common and grub-pc
so as per your code I have purged and installed one to many packages not that it harmed
but a waste of time.

---

### Post by drs305 on 2011-03-25
@ garvinrick4,

You can put both grub-common and grub-pc in both commands, but due to dependencies you don't have to actually list them both. grub-pc cannot exist without grub-common, so when you remove grub-common it takes grub-pc with it. Similarly, to install grub-pc it has to have grub-common, so the latter is installed as well. It doesn't hurt to include them both for clarity.

The reason I suggest purging in this case is that it's possible there is something wrong in the 00_header or other files which build the first part of grub.cfg (before the first menuentry). Whenever a new kernel is added, update-grub is run and the entire grub.cfg is rebuilt. If there is a problem with the way the file is built, just running update-grub wouldn't necessarily fix it.

---

### Post by garvinrick4 on 2011-03-25
@drs305

Thank you for clarifying, enjoy your day.

---

### Post by jtmedin on 2011-04-09
Sorry i am so late in trying this fix. I have been on vacation for a couple of weeks. Tried to purge & refresh grub but no banana. Got the same no boot & had to delete everything up to the menuentry. Now it boots again. One thing i did wrong is copy all three sugestions to terminal so i got a mishmash. So then did line 2 all by itself & then line 3 all by itself. Only comment i got was delete the grub boot record after line 2. I said yes to that & then did line 3. Got none of the comments your msg suggested?

---

### Post by drs305 on 2011-04-09
> **jtmedin said:**
> So then did line 2 all by itself & then line 3 all by itself. Only comment i got was delete the grub boot record after line 2. I said yes to that & then did line 3. Got none of the comments your msg suggested?

If the second command purged grub, grub-pc (Grub2) and grub-common, the third command would have asked about where to install Grub2; so something didn't work quite correctly. 

You can try running both commands again, one at a time. Or please download and run the boot info script from the following link and post the contents of RESULTS.txt. It will show us the status of your system and boot files.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by jtmedin on 2011-04-21
Ok here is the results on the desktop pc:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   143,364,055   143,363,993   7 HPFS/NTFS
/dev/sda2    *    143,364,060   348,152,054   204,787,995   7 HPFS/NTFS
/dev/sda3         425,995,605   625,137,344   199,141,740   5 Extended
Empty Partition


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       83aaf487-866c-4200-bbd9-da8513745854   ext4                                     
/dev/sda1        54ACF470ACF44DCC                       ntfs       local Disk XP                 
/dev/sda2        E4B819BFB8199162                       ntfs       Local Disk WIN7               
/dev/sda3: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=0

[operating systems]


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
menuentry "Ubuntu, Linux 2.6.32-30-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-30-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, Linux 2.6.32-30-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-30-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, Linux 2.6.32-29-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-29-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, Linux 2.6.32-29-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-29-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, Linux 2.6.32-28-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, Linux 2.6.32-28-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 54acf470acf44dcc
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


   7.7GB: boot/grub/grub.cfg
   6.9GB: boot/initrd.img-2.6.32-21-generic
   7.1GB: boot/initrd.img-2.6.32-22-generic
   7.1GB: boot/initrd.img-2.6.32-23-generic
   6.3GB: boot/initrd.img-2.6.32-24-generic
   6.2GB: boot/initrd.img-2.6.32-25-generic
    .2GB: boot/initrd.img-2.6.32-26-generic
   8.0GB: boot/initrd.img-2.6.32-27-generic
   6.0GB: boot/initrd.img-2.6.32-28-generic
   9.6GB: boot/initrd.img-2.6.32-29-generic
   8.7GB: boot/initrd.img-2.6.32-30-generic
   6.9GB: boot/vmlinuz-2.6.32-21-generic
    .6GB: boot/vmlinuz-2.6.32-22-generic
    .8GB: boot/vmlinuz-2.6.32-23-generic
   7.3GB: boot/vmlinuz-2.6.32-24-generic
   7.5GB: boot/vmlinuz-2.6.32-25-generic
   7.5GB: boot/vmlinuz-2.6.32-26-generic
   8.3GB: boot/vmlinuz-2.6.32-27-generic
   8.0GB: boot/vmlinuz-2.6.32-28-generic
   8.6GB: boot/vmlinuz-2.6.32-29-generic
   8.6GB: boot/vmlinuz-2.6.32-30-generic
   8.7GB: initrd.img
   9.6GB: initrd.img.old
   8.6GB: vmlinuz
   8.6GB: vmlinuz.old
```

---

### Post by drs305 on 2011-04-21
I think this is the first time we knew you were using Wubi...

Rubi1200 has created a thread devoted to Wubi boot failures. Please take a look at that thread. Determine which problem is similar to yours and then apply the applicable solution. 
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

The followers of that thread are very familiar with Wubi boot failures and I'd suggest you post there so ensure they will see it. You'll probably have to post the RESULTS.txt in that thread.

---

### Post by jtmedin on 2011-04-21
Sorry i am so tardy. Here is result.txt from the boot script on the desktop


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   143,364,055   143,363,993   7 HPFS/NTFS
/dev/sda2    *    143,364,060   348,152,054   204,787,995   7 HPFS/NTFS
/dev/sda3         425,995,605   625,137,344   199,141,740   5 Extended
Empty Partition


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       83aaf487-866c-4200-bbd9-da8513745854   ext4                                     
/dev/sda1        54ACF470ACF44DCC                       ntfs       local Disk XP                 
/dev/sda2        E4B819BFB8199162                       ntfs       Local Disk WIN7               
/dev/sda3: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=0

[operating systems]


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
menuentry "Ubuntu, Linux 2.6.32-30-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-30-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, Linux 2.6.32-30-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-30-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, Linux 2.6.32-29-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-29-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, Linux 2.6.32-29-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-29-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, Linux 2.6.32-28-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, Linux 2.6.32-28-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 54acf470acf44dcc
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e4b819bfb8199162
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


   7.7GB: boot/grub/grub.cfg
   6.9GB: boot/initrd.img-2.6.32-21-generic
   7.1GB: boot/initrd.img-2.6.32-22-generic
   7.1GB: boot/initrd.img-2.6.32-23-generic
   6.3GB: boot/initrd.img-2.6.32-24-generic
   6.2GB: boot/initrd.img-2.6.32-25-generic
    .2GB: boot/initrd.img-2.6.32-26-generic
   8.0GB: boot/initrd.img-2.6.32-27-generic
   6.0GB: boot/initrd.img-2.6.32-28-generic
   9.6GB: boot/initrd.img-2.6.32-29-generic
   8.7GB: boot/initrd.img-2.6.32-30-generic
   6.9GB: boot/vmlinuz-2.6.32-21-generic
    .6GB: boot/vmlinuz-2.6.32-22-generic
    .8GB: boot/vmlinuz-2.6.32-23-generic
   7.3GB: boot/vmlinuz-2.6.32-24-generic
   7.5GB: boot/vmlinuz-2.6.32-25-generic
   7.5GB: boot/vmlinuz-2.6.32-26-generic
   8.3GB: boot/vmlinuz-2.6.32-27-generic
   8.0GB: boot/vmlinuz-2.6.32-28-generic
   8.6GB: boot/vmlinuz-2.6.32-29-generic
   8.6GB: boot/vmlinuz-2.6.32-30-generic
   8.7GB: initrd.img
   9.6GB: initrd.img.old
   8.6GB: vmlinuz
   8.6GB: vmlinuz.old
```

---

### Post by jtmedin on 2011-04-22
Ran the bootscript & got the results. Copied same to a reply but dont know what i did wrong because its not in this thread. Tried again but same result? anyone got any ideas? I will try again & watch carefully.

Now i am confused i see all the posts, guess my eyes are failing me :-). Thanks for the tip on wubi will try there.

---

### Post by GreginSJ on 2011-04-22
I am new to Ubuntu, just installed 10.04 LTS through a WUBI install a couple of weeks ago and everything was working great.  Then today, I was prompted to install certain "security updates", so I allowed the system to do that.  Now I can't reboot.  As the system tries to reboot, at the point when asked to select Windows or Ubuntu, and I select Ubuntu, the computer simply tries to reboot again and brings me right back to the Windows/Ubuntu boot selection prompt.  I can successfully boot into Windows, just not Ubuntu.
System is:  HP dx5150 desktop running on AMD Athlon 3000 chips, Windows XP sp 3, Ubuntu WUBI 10.04 LTS.

---

### Post by drs305 on 2011-04-22
GreginSJ,

This is an unfortunately common failure in Wubi after an update. Visit the Wubi megathread. Your problem is described and the solution posted in the first post.
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

---

