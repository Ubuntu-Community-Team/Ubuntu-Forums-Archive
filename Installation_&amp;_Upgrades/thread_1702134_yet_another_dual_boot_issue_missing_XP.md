---
title: "yet another dual boot issue: missing XP"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by janx on 2011-03-07
After a Lubuntu 10.10 installation on a machine with Windows XP, involving a HD shrinking, I am able to boot into Linux but there is no entry for Windows.

I ran the boot info script. Here is the result of the fifth screen:
```

Disk /dev/sda - 82 GB / 76 GiB - CHS 10011 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  2436  66 52   39138487

Boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK

Backup boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

```

Could not run the sixth screen because of the missing "BackupBS".

Windows appears still there. Here is the result of fdisk:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2437    19569243+   7  HPFS/NTFS
/dev/sda2            2437       10012    60848129    5  Extended
/dev/sda5            2437        9697    58318848   83  Linux
/dev/sda6            9697       10012     2528256   82  Linux swap / Solaris

```

I am also listing part of grub.cfg:
```

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5 ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set a0e07a06-8ce2-4ecf-be84-3b78ee1de1f5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

```

Is there any chance I can have a correct dual boot system, preferably without reinstalling from scratch Windows or Linux?

tia

---

### Post by FoxEWolf on 2011-03-07
Are you Saying that you shrunk the partitions?

---

### Post by janx on 2011-03-07
Right. With the Ubuntu install.

---

### Post by FoxEWolf on 2011-03-07
How did you exactly carry out the operation? Wubi.exe? or a boot cd that allowed you to shrink partitions. Shrinking partitions that have an install on it and making that unallocated space and not formatting it will cause problems.

---

### Post by wilee-nilee on 2011-03-07
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Lets not speculate with bad news eh, this will give us a what is where.

---

### Post by janx on 2011-03-07
@FoxEWolf
Sorry if it was not clear. This machine had only Windows XP filling 100% of the disk. I installed Ubuntu with a boot CD. I cannot remember exactly, but I think I chose the default option: 'install side by side' involving a shrink of the Windows partition.

@wilee-nilee
This is the boot info script with testdisk, that I used. The result is the first paste in my message. I did that with Linux booted from the HD, not from the live CD.

---

