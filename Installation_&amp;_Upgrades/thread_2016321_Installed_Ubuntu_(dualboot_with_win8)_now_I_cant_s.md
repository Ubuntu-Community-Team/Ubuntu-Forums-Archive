---
title: "Installed Ubuntu (dualboot with win8) now I cant start win8"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by wakary on 2012-07-04
I had 1 hard disk split like this: 
-C
-(unallocated space)

I had Win8 installed on drive C and installed Ubuntu using the bootable usb method on a new partition 
( I made a new ext4 partition for Ubuntu and put the bootloader thing on the windows 8 (loader))

Now when the "grub menu" appears I get the option to boot:
- ubuntu
- ubuntu repair
- memory diagostic
- ... ubuntu related stuff
- windows 8 (loader)

When I select Win8 it just goes to the grub menu again, no matter how many times I select Win 8 it still stays at the grub menu.

EDIT: I was in a hurry and there were no replies here so I reinstalled win8.
Now it boots win8 but ubuntu has disappeared completely.

How do I bring back ubuntu? (without losing windows)

---

### Post by TheFlanman91 on 2012-07-04
I'm having this exact problem but with Win7! The Windows 7 (loader) is visible and selectable but any time I select it the screen goes blank as if about to load the OS and then GRUB appears again. Any support on the matter would be greatly appreciated.

---

### Post by lukeiamyourfather on 2012-07-04
Try updating GRUB with this command. That will usually fix any issues.

```
sudo grub-update
```

---

### Post by TheFlanman91 on 2012-07-04
Have tried that a few times, even edited the file located at etc/default/grub to change the default selection on boot to the Windows 7 (loader). Nothing.

I'm curious to see is it a problem with GRUB or with my Windows 7 partition?

If there's any log files or anything that would help out please let me know.

---

### Post by darkod on 2012-07-04
Well, you said it yourself. You put the grub2 bootloader on the win8 partition. The bootloader usually goes to the MBR of the disk, like /dev/sda, /dev/sdb, etc. Without a number in it.

If grub2 is installed onto the windows partition, when you try to boot it it will open grub that is on the partition.

You should be able to use testdisk to remove grub2 from the windows partition:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

After that it should be fine.

---

### Post by wakary on 2012-07-04
I was in a hurry and there were no replies here so I reinstalled win8.
Now it boots win8 but ubuntu has disappeared completely.

How do I bring back ubuntu? (without losing windows)

---

### Post by darkod on 2012-07-04
> **wakary said:**
> I was in a hurry and there were no replies here so I reinstalled win8.
Now it boots win8 but ubuntu has disappeared completely.

How do I bring back ubuntu? (without losing windows)

You need to use the ubuntu cd in live mode and reinstall grub2 to the MBR. You have instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Since win8 was reinstalled, you might need to boot ubuntu first and run in terminal:
sudo update-grub

---

### Post by oldfred on 2012-07-04
Is this part of the problem? Windows 8 does not play nice with other systems even other Windows.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by wakary on 2012-07-04
> **darkod said:**
> You need to use the ubuntu cd in live mode and reinstall grub2 to the MBR. You have instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Since win8 was reinstalled, you might need to boot ubuntu first and run in terminal:
sudo update-grub

Ok I used easyBCD (found on your link) and I can now boot on choice win8 or ubuntu.
(I get a menu:
-windows 8
-ubuntu
If I select windows 8 it boots normally. But when I select ubuntu it takes me to the grub menu and I must select from there, again, ubuntu [also the old windows 8 (loader) still appears on this grub menu])

I would like to get rid of this extra grub menu and if possible remove the windows 8 entry on it.

---

### Post by darkod on 2012-07-04
> **wakary said:**
> Ok I used easyBCD (found on your link) and I can now boot on choice win8 or ubuntu.
(I get a menu:
-windows 8
-ubuntu
If I select windows 8 it boots normally. But when I select ubuntu it takes me to the grub menu and I must select from there, again, ubuntu [also the old windows 8 (loader) still appears on this grub menu])

I would like to get rid of this extra grub menu and if possible remove the windows 8 entry on it.

Well, no one mentioned using easybcd. I mentioned reinstalling grub2 to the MBR.

But also note what oldfred posted about win8 not playing nice in dual boot.

As for what you want to do now, first undo all that you did with easybcd, so that you have only win8 again in the windows bootloader. Then use the instructions to reinstall grub2. Under the assumption your root partition is /dev/sda5, the commands to reinstall grub2 would be:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note that you will need to check which is the root partition with fdisk as explained in that link.

That should provide the grub2 boot menu with ubuntu and win8.

---

### Post by sudodus on 2012-07-04
[I]Edit: darkod's instruction in the previous post is important, and may solve the problem in your case. It is vital to get grub into the MBR (the beginning of the drive).
[/I]
I made a test install with Windows 8 Developer's Preview some months ago. I started with an empty internal hard disk drive and installed Win8 in /dev/sda1 alias '(hd0,msdos1)'

Then I installed Lubuntu 12.04 in /dev/sda5 alias '(hd0,msdos5)'

I had no issues, it was 'business as usual', I had a grub menu with the various entries, one of them being Win8.

Later on I participated in beta testing of Lubuntu and installed several daily builds (with and without pae) several times in

/dev/sda4 alias '(hd0,msdos4)',
/dev/sda6 alias '(hd0,msdos6)' and
/dev/sda7 alias '(hd0,msdos7)'

The 'main' Lubuntu in /dev/sda5 was updated several times and I updated grub ```
sudo update-grub
``` several times without getting problems to boot Win8.

This is my grub.cfg file
```
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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root b35da0b1-d551-48a3-98d7-1806f2152c49
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root b35da0b1-d551-48a3-98d7-1806f2152c49
  set locale_dir=($root)/boot/grub/locale
  set lang=sv_SE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/blue
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, med Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root b35da0b1-d551-48a3-98d7-1806f2152c49
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=b35da0b1-d551-48a3-98d7-1806f2152c49 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, med Linux 3.2.0-23-generic-pae (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root b35da0b1-d551-48a3-98d7-1806f2152c49
	echo	'Läser in Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=b35da0b1-d551-48a3-98d7-1806f2152c49 ro recovery nomodeset 
	echo	'Läser in initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, med Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root b35da0b1-d551-48a3-98d7-1806f2152c49
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=b35da0b1-d551-48a3-98d7-1806f2152c49 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, med Linux 3.2.0-23-generic (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root b35da0b1-d551-48a3-98d7-1806f2152c49
	echo	'Läser in Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=b35da0b1-d551-48a3-98d7-1806f2152c49 ro recovery nomodeset 
	echo	'Läser in initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root b35da0b1-d551-48a3-98d7-1806f2152c49
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root b35da0b1-d551-48a3-98d7-1806f2152c49
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
[COLOR="Red"]menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 56CA491D4B15082A
	drivemap -s (hd0) ${root}
	chainloader +1
}[/COLOR]
menuentry "Ubuntu, med Linux 3.2.0-23-generic (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 3c6e794f-f29e-47f1-b5a3-d91a39084053
	linux /boot/vmlinuz-3.2.0-23-generic root=UUID=3c6e794f-f29e-47f1-b5a3-d91a39084053 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Ubuntu, med Linux 3.2.0-23-generic (återställningsläge) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 3c6e794f-f29e-47f1-b5a3-d91a39084053
	linux /boot/vmlinuz-3.2.0-23-generic root=UUID=3c6e794f-f29e-47f1-b5a3-d91a39084053 ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Ubuntu, med Linux 3.2.0-23-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 546a8a6a-42e7-4cc4-9d5b-3506309f2b9e
	linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=546a8a6a-42e7-4cc4-9d5b-3506309f2b9e ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry "Ubuntu, med Linux 3.2.0-23-generic-pae (återställningsläge) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 546a8a6a-42e7-4cc4-9d5b-3506309f2b9e
	linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=546a8a6a-42e7-4cc4-9d5b-3506309f2b9e ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry "Ubuntu, med Linux 3.2.0-23-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 546a8a6a-42e7-4cc4-9d5b-3506309f2b9e
	linux /boot/vmlinuz-3.2.0-23-generic root=UUID=546a8a6a-42e7-4cc4-9d5b-3506309f2b9e ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Ubuntu, med Linux 3.2.0-23-generic (återställningsläge) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 546a8a6a-42e7-4cc4-9d5b-3506309f2b9e
	linux /boot/vmlinuz-3.2.0-23-generic root=UUID=546a8a6a-42e7-4cc4-9d5b-3506309f2b9e ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Ubuntu, med Linux 3.2.0-23-generic-pae (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 114760d3-9c0e-4ac0-abe9-2b412459ffcf
	linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=114760d3-9c0e-4ac0-abe9-2b412459ffcf ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry "Ubuntu, med Linux 3.2.0-23-generic-pae (återställningsläge) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 114760d3-9c0e-4ac0-abe9-2b412459ffcf
	linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=114760d3-9c0e-4ac0-abe9-2b412459ffcf ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry "Ubuntu, med Linux 3.2.0-23-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 114760d3-9c0e-4ac0-abe9-2b412459ffcf
	linux /boot/vmlinuz-3.2.0-23-generic root=UUID=114760d3-9c0e-4ac0-abe9-2b412459ffcf ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Ubuntu, med Linux 3.2.0-23-generic (återställningsläge) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 114760d3-9c0e-4ac0-abe9-2b412459ffcf
	linux /boot/vmlinuz-3.2.0-23-generic root=UUID=114760d3-9c0e-4ac0-abe9-2b412459ffcf ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-23-generic
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
```

This section makes the Win8 entry in the grub menu:
```
menuentry "Windows Recovery Environment (loader) (on /dev/sda[COLOR="Red"]1[/COLOR])" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd[COLOR="Red"]0[/COLOR],msdos[COLOR="red"]1[/COLOR])'
	search --no-floppy --fs-uuid --set=root [COLOR="red"]56CA491D4B15082A[/COLOR]
	drivemap -s (hd[COLOR="red"]0[/COLOR]) ${root}
	chainloader +1
}
```

Use it as a template if you like, but remember to change the device and partition numbers and the uuid to fit your installation. Furthermore, when you know it works, you should copy it to ***/etc/grub.d/40_custom*** so that it survives automatic and manual updates of grub.

---

### Post by wakary on 2012-07-05
> **darkod said:**
> Well, no one mentioned using easybcd. I mentioned reinstalling grub2 to the MBR.

But also note what oldfred posted about win8 not playing nice in dual boot.

As for what you want to do now, first undo all that you did with easybcd, so that you have only win8 again in the windows bootloader. Then use the instructions to reinstall grub2. Under the assumption your root partition is /dev/sda5, the commands to reinstall grub2 would be:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note that you will need to check which is the root partition with fdisk as explained in that link.

That should provide the grub2 boot menu with ubuntu and win8.

Thanks, it boots properly now.

---

