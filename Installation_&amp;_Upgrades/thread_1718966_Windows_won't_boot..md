---
title: "Windows won't boot."
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by telphan on 2011-04-01
Untill 2 days ago i had on my i3-540 pc a dual boot between windows 7 and mac osx, i needed linux so i've replaced my osx with ubuntu 10.10 now grub2 made my dual boot. Now windows won't boot. So i searched a lot for solutions. In a post in this forum someone said to run in cmd(from vista cd) some bootrec comands. Worked smoothyl till bootrec /rebuildbcd the command finds my windows partion but can't write boot. In addition to that i tried reinstalling windows and instead of finding in the wizard my 4 partitons(swap linux winsystem  and win) i find only one partition which is the whole hdd. And if i try to boot hdd system  says "bootfailure insert systemdisk". I'm acctualy sending this message throught my android phone so please help.

---

### Post by telphan on 2011-04-01
Ok, managed to get the grub menu back and running. Any ideas for the windows boot?

---

### Post by Hedgehog1 on 2011-04-01
We need to see what the conditions of your partitions are.

I need to ask you to boot from your LiveCD/LiveUSB and do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by telphan on 2011-04-01
Edited

---

### Post by Hedgehog1 on 2011-04-01
Sadly, the text you posted is only about 1/2 of the script output.  

Would you please post is again with all the text (also please use the '#' button (give you the **CODE**, **/CODE** tags) and paste the text between the **CODE**, **/CODE** tags so we can read it easier.

Thanks!

***The Hedge***

:KS

---

### Post by telphan on 2011-04-02
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 162982656 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048    11,718,655    11,716,608 Linux Swap
/dev/sda2      11,718,656   195,983,359   184,264,704 Linux or Data
/dev/sda3     195,985,408   488,953,855   292,968,448 Linux or Data
/dev/sda4     488,953,856 1,953,523,711 1,464,569,856 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        41c3e93e-e32b-4045-aec2-c0236fd1bc2e   swap                                     
/dev/sda2        9183fb24-8f5a-4bf6-880d-2607f92e7a27   ext4                                     
/dev/sda3        C88C02C38C02ABCE                       ntfs                                     
/dev/sda4        0864962364961412                       ntfs       Documents                     
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Ubuntu 10.04 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda2/boot/grub/menu.lst: ===========================

title Windows 7
rootnoverify (hd0,0)
map (hd1)(hd0)
map (hd0)(hd1)
chainloader +1

title Ubuntu, 10-10
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

=========================== sda2/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set 9183fb24-8f5a-4bf6-880d-2607f92e7a27
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set 9183fb24-8f5a-4bf6-880d-2607f92e7a27
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 9183fb24-8f5a-4bf6-880d-2607f92e7a27
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9183fb24-8f5a-4bf6-880d-2607f92e7a27 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 9183fb24-8f5a-4bf6-880d-2607f92e7a27
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9183fb24-8f5a-4bf6-880d-2607f92e7a27 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 9183fb24-8f5a-4bf6-880d-2607f92e7a27
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9183fb24-8f5a-4bf6-880d-2607f92e7a27 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 9183fb24-8f5a-4bf6-880d-2607f92e7a27
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9183fb24-8f5a-4bf6-880d-2607f92e7a27 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 9183fb24-8f5a-4bf6-880d-2607f92e7a27
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 9183fb24-8f5a-4bf6-880d-2607f92e7a27
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	rootnoverify (hd0,3)	
	insmod ntfs
	set root='(hd0,gpt3)'
	search --no-floppy --fs-uuid --set c88c02c38c02abce
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  83.4GB: boot/grub/core.img
  16.0GB: boot/grub/grub.cfg
  83.4GB: boot/grub/menu.lst
  83.4GB: boot/initrd.img-2.6.32-21-generic
   6.5GB: boot/initrd.img-2.6.35-28-generic
  83.4GB: boot/vmlinuz-2.6.32-21-generic
  83.5GB: boot/vmlinuz-2.6.35-28-generic
   6.5GB: initrd.img
  83.5GB: vmlinuz
``` Sorry, i was in a hurry.

---

### Post by Hedgehog1 on 2011-04-02
Thanks for the script results.

Here is the deal: Your hard drive has a GUID Partiton Table (required by OSX) and then an MBR table inside it to support dual-boot between OSX and Windows.  

The snag is that OSX was the control; and when you deleted /dev/sda1 and dev/sda2 you knocked the foundation out of windows to boot in this 'OSX' environment. Windows has real trouble booting in a GPT (**G**UID **P**artiton **T**able) situation.

The ideal situation is to restructure you disk with an MBR partition table (the only one Windows understands).  This is a fair about of work, and has some risk associated with it.

The basic idea is you would turn this layout:

> GPT partition map
/dev/sda1  Linux Swap
/dev/sda2  Linux or Data
/dev/sda3  Linux or Data (Presented as NTFS)
/dev/sda4  Linux or Data (Presented as NTFS)

To this:

> MBR partition map
/dev/sda1  ntfs (Windows boot)
/dev/sda2  ntfs (Windows)
/dev/sda3  ext4 '/' for Ubuntu
/dev/sda4  Linux Swap

Or to this:

> MBR partition map
/dev/sda1  ntfs (Windows boot)
/dev/sda2  ntfs (Windows)
/dev/sda3  Extended Partition
__/dev/sda5  ext4 '/' for Ubuntu
__/dev/sda6  ext4 '/home' for Ubuntu
__/dev/sda7  Linux Swap

This is not a small project.

***The Hedge***

:KS

---

### Post by telphan on 2011-04-02
Small or not small i have to do it. So can you direct me or show me some links to reach the solution?

---

### Post by srs5694 on 2011-04-02
Actually, it's not that bad:


[list=1]
[*]Download [Super GRUB 2 Disk](http://www.supergrubdisk.org/) and burn it to CD. Set it aside; you'll need it later.
[*]Download and install GPT fdisk (gdisk) in whatever way is most convenient. (See my recently-updated [Obtaining GPT fdisk](http://www.rodsbooks.com/gdisk/download.html) page.)
[*]Launch gdisk on your disk, as in "sudo gdisk /dev/sda" from a Terminal window.
[*]Type "p" to view your partitions and verify that you're working on the correct disk.
[*]Type "r" to enter the recovery & transformation menu.
[*]Type "g" to enter the MBR conversion menu.
[*]Type "p" to view the the MBR partitions the program has prepared that are equivalent to your current partitions.
[*]Ensure that partitions 2, 3, and 4 are all flagged as being primary. (Your partition #1 can safely be a logical partition, but that's not necessary, and it's a bit weird to have the first partition be a logical partition.)
[*]Use the "t" option to change the type code of partition #2 from 0x07 to 0x83.
[*]Type "p" again to view your partition table again and verify that it looks correct.
[*]Type "w" to save the partition table. If you have doubts, don't do this; instead, type "q" to exit from the MBR conversion menu, then "q" again to exit from gdisk.
[*]Insert the Super GRUB 2 Disk in the drive.
[*]Reboot and use the Super GRUB 2 Disk options to locate your GRUB menu and boot Linux.
[*]At a shell prompt (in a Terminal window), type "sudo grub-install". This re-installs GRUB, which is necessary because there are different versions of the on-disk GRUB code for MBR vs. GPT.
[*]Remove the Super GRUB 2 Disk from the optical drive.
[*]Reboot to verify that everything works.
[/list]


[This page,](http://www.rodsbooks.com/gdisk/mbr2gpt.html) and particularly the "Converting from GPT to MBR" section, describes most of the process in more detail. You may also find my [FixParts page](http://www.rodsbooks.com/fixparts/) helpful, since the MBR conversion menu in gdisk is identical to the main menu in FixParts.

There is one other option, which is a bit simpler and easier in the short run but which is much riskier in the long run: You can create a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) that contains your two NTFS partitions. This is probably the configuration you had when you were experimenting with the Hackintosh setup. The process is similar to the above, but you'd select the "h" option rather than the "g" option in step #6, then follow the prompts to select the partitions to include in the hybrid MBR. You will not need to re-install GRUB if you do it this way. The downside is that, as described on the hybrid MBR page to which I've just linked, hybrid MBRs are flaky and dangerous. They can cause many problems, so you're better off with a straight-MBR or straight-GPT configuration whenever possible -- and a straight-MBR configuration is possible in your case.

One final final caveat: Windows is very picky about its boot partition. Once you've converted back to MBR form, it's entirely possible that Windows will turn its nose up and refuse to boot. If that happens, I can't help any more; you're in the realm of Windows flakiness, about which I know very little. I usually re-install Windows when it refuses to boot, since that's usually quicker than trying to troubleshoot it, in my experience.

---

### Post by Hedgehog1 on 2011-04-02
> **srs5694 said:**
> Actually, it's not that bad: ...

**The Partition Doctor is _IN_.**

I was hoping you might see this thread :D



***The Hedge***

:KS

---

### Post by telphan on 2011-04-02
@srs5694
When i try to change my code from 0x07 to 0x83, and i hit p for verification, the code for the #2 partition is 0x0A. ?!?!?
[Solved]

---

### Post by srs5694 on 2011-04-02
> **telphan said:**
> @srs5694
When i try to change my code from 0x07 to 0x83, and i hit p for verification, the code for the #2 partition is 0x0A. ?!?!?
[Solved]

That's peculiar. I'd like to see the exact interactions; could you cut-and-paste the text session into a text file and send them to me or post them?

In the meantime, the workaround is to *not* make this change in gdisk, but to use fdisk to make this change after you've converted to MBR.

---

### Post by telphan on 2011-04-03
When it was requesting a hex number i was entering like an idiot 0x83 instead of 83:))). I solved everything windows boots correctly. Parts are showing perfect. Thanks a lot for the help. You really are the Doctor partition:))

---

### Post by srs5694 on 2011-04-03
Thanks. I've made a note to look into the "0x" prefix issue for a future version of GPT fdisk.

---

