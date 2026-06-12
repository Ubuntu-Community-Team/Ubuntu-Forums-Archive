---
title: "Windows 7 lost on update to 10.04 - googled fixes not working"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by viva_cthulhu on 2010-06-03
SOLVED: See post three.

This problem is apparently [pretty common]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724").

When I try booting windows from grub, I get nothing but a black screen, and blinking cursor. 
I have succedeed in locating the issue - when I have updated from 9.10 to 10.04, grub asked where he was supposed to install itself, and I followed its polite advice and cheerfully clicked on all drives since I wasn't sure - apparently, this does bad things to NTFS boot sectors.

I've tried the [testdisk]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") fix, that apparently solves the problem for most people, to no avail.
I tried recovering [through the Win7 disk]("http://forums.techguy.org/linux-unix/921261-ubuntu-10-04-upgrade-cant.html#13") too, and, eerily, that only succeded in killing the mbr too, forcing me to reinstall grub from the livecd.

I really hope you guys can help. I feel pretty desperate.

sudo fdisk-l says this:

```
Disco /dev/sda: 1000.2 GB, 1000204886016 byte
255 testine, 63 settori/tracce, 121601 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x000eb7e9

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      114791   922058676    7  HPFS/NTFS
/dev/sda2          114792      121601    54701325    5  Esteso
/dev/sda5          114792      121317    52420063+  83  Linux
/dev/sda6          121318      121601     2281198+  82  Linux swap / Solaris

Disco /dev/sdb: 750.2 GB, 750156374016 byte
255 testine, 63 settori/tracce, 91201 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x81f8bd54

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    7  HPFS/NTFS

```

And this is grub.cfg.

```
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 22e76025-985f-4de2-b7ec-e2af1f1c4211
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 22e76025-985f-4de2-b7ec-e2af1f1c4211
set locale_dir=($root)/boot/grub/locale
set lang=it
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
menuentry 'Ubuntu, con Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22e76025-985f-4de2-b7ec-e2af1f1c4211
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=22e76025-985f-4de2-b7ec-e2af1f1c4211 ro nomodeset  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic-pae (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22e76025-985f-4de2-b7ec-e2af1f1c4211
	echo	'Caricamento Linux 2.6.32-22-generic-pae...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=22e76025-985f-4de2-b7ec-e2af1f1c4211 ro single nomodeset
	echo	'Caricamento ramdisk iniziale...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22e76025-985f-4de2-b7ec-e2af1f1c4211
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=22e76025-985f-4de2-b7ec-e2af1f1c4211 ro nomodeset  quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.31-21-generic-pae (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22e76025-985f-4de2-b7ec-e2af1f1c4211
	echo	'Caricamento Linux 2.6.31-21-generic-pae...'
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=22e76025-985f-4de2-b7ec-e2af1f1c4211 ro single nomodeset
	echo	'Caricamento ramdisk iniziale...'
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.31-16-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22e76025-985f-4de2-b7ec-e2af1f1c4211
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=22e76025-985f-4de2-b7ec-e2af1f1c4211 ro nomodeset  quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
menuentry 'Ubuntu, con Linux 2.6.31-16-generic-pae (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22e76025-985f-4de2-b7ec-e2af1f1c4211
	echo	'Caricamento Linux 2.6.31-16-generic-pae...'
	linux	/boot/vmlinuz-2.6.31-16-generic-pae root=UUID=22e76025-985f-4de2-b7ec-e2af1f1c4211 ro single nomodeset
	echo	'Caricamento ramdisk iniziale...'
	initrd	/boot/initrd.img-2.6.31-16-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22e76025-985f-4de2-b7ec-e2af1f1c4211
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 22e76025-985f-4de2-b7ec-e2af1f1c4211
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 36ae5070ae502b1f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

To a quick check, it looks like the important parts are readable, but if you need translations from the italian, I'm ready to oblige.

Thanks a lot in advance...

---

### Post by darkod on 2010-06-03
If you selected all drives (disks) you would still be good. You also selected all partitions. Just to clear the confusion.

If you are sure you did the testdisk procedure correctly and it doesn't work, and because reinstalling grub2 from live cd is very easy, I recommend using the win7 dvd again to try the repair process. Run it few times, it's been said it needs about three runs to fix everything.

Alternatively, you also have manual commands from the command line here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once that is done, just reinstall grub2 to the MBR again.

---

### Post by viva_cthulhu on 2010-06-03
Ok, that link did the trick! I had to use the fixboot option, now everything works like a charm!
Sir, you are deserving of my eternal gratitude. I was at the end of my rope.
Thanks!

---

