---
title: "Can't Boot w/o First Using Live CD...  Other Problems..."
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by casparov on 2010-05-06
Hi, Everyone...   [NOTE Contents of grub.cfg on my system appears following narrative--if that helps.]

I must first admit that I posted this particular problem to these forums here: [http://ubuntuforums.org/showthread.php?p=9200087#post9200087](http://ubuntuforums.org/showthread.php?p=9200087#post9200087)  However, I guess I have met my match--I really find it difficult to follow some instructions, and find that I lose patience when things get too technical.  So, I apologize to those who have provided excellent advice, which I just found a bit beyond my reach.  

I installed Lucid to a 500GB blank drive after running Karmic for about 6 mos. (and being satisfied w/ it :p).  The live CD install for Lucid partitioned the drive into two, roughly, 250GB partitions, of which one now runs Lucid.  I spent the typical amount of time installing Ubuntu restricted extras, Java, etc....  

I have two basic problems now.  First, I cannot boot into Lucid unless I use the live CD for Karmic, because that CD grants a "boot from first disk" option.  If I don't use a live CD all I get is a GRUB instruction on a black screen for "Press enter to boot from CD", or something like that.  If I do not press enter then I get a system disk error.  

Secondly, I cannot use my DVD player and posted this problem to these forums here: [http://ubuntuforums.org/showthread.php?p=9185520#post9185520](http://ubuntuforums.org/showthread.php?p=9185520#post9185520)  This did not resolve the issue.  The upshot is that I cannot load and play a CD/DVD of ANY type unless I reboot the system.  Once I sign on to the Net, or wait a while, or whatever the system will not recognize the DVD unit or a disk entered into it. (NOTE: I have installed libdvdcss2.)


Is there any way that I can simply reinstall Lucid WITHOUT having to rebuild the system again?  Is there anyway to reinstall GRUB so that I might be able to boot without a live CD?  Is there anyway to recapture DVD capability in my system?

Karmic was a breeze--it dual booted Windows and ran flawlessly.  Lucid has been a nightmare of sorts--insofar as these types of problems can be considered significant (which they really aren't in the big scheme of things).  I have spent a good effort over the last couple of years proselytizing for Linux/Ubuntu, and now I feel that I can't make the system work, either.

Thanks so much to all that have read or contributed to this request for help.

Sincerely, Casp

Contents of grub.cfg:  

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 7711f358-cec4-43d4-9e15-9131e5ee6e7e
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 7711f358-cec4-43d4-9e15-9131e5ee6e7e
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7711f358-cec4-43d4-9e15-9131e5ee6e7e
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=7711f358-cec4-43d4-9e15-9131e5ee6e7e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7711f358-cec4-43d4-9e15-9131e5ee6e7e
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=7711f358-cec4-43d4-9e15-9131e5ee6e7e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7711f358-cec4-43d4-9e15-9131e5ee6e7e
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7711f358-cec4-43d4-9e15-9131e5ee6e7e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7711f358-cec4-43d4-9e15-9131e5ee6e7e
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7711f358-cec4-43d4-9e15-9131e5ee6e7e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7711f358-cec4-43d4-9e15-9131e5ee6e7e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 7711f358-cec4-43d4-9e15-9131e5ee6e7e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

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

---

