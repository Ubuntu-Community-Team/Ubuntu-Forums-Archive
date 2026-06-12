---
title: "dualboot (win8+ubunu12.10), grub2, Windows recovery environment"
date: 2012-12-24
forum: Installation &amp; Upgrades
---

### Post by ugiulio on 2012-12-24
Hello everybody,

I got some problem during the installation of Ubuntu on a UEFI ultrabook.
I give you all the infos about what I have done:
1) restore my laptop to the factory default configuration (so only Windwos 8 was on my harddrive);
2) install Ubuntu Secure Remix; here I got the first "surprise": "This computer currently has no detected operating system" and using os-prober I got "/dev/sda6:Windows Recovery Environment (loader):Windows:chain", while I also should got  "/dev/sda2:Window 8.....". Here you can find the Boot Info Script [http://paste.ubuntu.com/1460646/;](http://paste.ubuntu.com/1460646/;)
3) so I aborted the installation and I tried to verify my harddrive partition scheme through fixparts under Windows 8. Apparently everything was fine;
4) I tried a new installation of Ubuntu selecting "Other" and performing a manual partioning. The installation ended fine. At the first reboot I was only able to load Ubuntu through the grub2. Here you can read the Boot Info script at that moment [http://paste.ubuntu.com/1460627/](http://paste.ubuntu.com/1460627/);
5) so I performed boot-repair to get back Windows loading at the grub2 shell. After that the Boot Info Script was  [http://paste.ubuntu.com/1460646/](http://paste.ubuntu.com/1460646/) (os-prober continues to give only "/dev/sda6:Windows Recovery Environment (loader):Windows:chain");
6) at the next reboot this was what I got at the grub2 options:
a) ubuntu (that loads correctly Ubuntu OS); 
b) advance options for Ubuntu;
c) Windows UEFI loader (that loads properly Windwos 8);
d) Windows Boot UEFI bootx64.efi.bkp (as c);
e)  Windows Recovery Enviroment (loader) (on /dev/sda6) (this gives the following error messages: error: impossible find command'drivemap'; error:  invalid EFI file path; press any key to continue  (and it comes back to grub2);

How can I get working/loading the Windows Recovery Environment? The problem seems to be located in grub2. Have I to re-install grub? (Boot-repair should already have done it?!?!?!?!) 

Any recommendation is well accepted!!!

Thanks in advace

---

### Post by catalin.vasilescu on 2012-12-24
For general boot problems (even specific problems  UEFI - GPT) with grub-boot-loader you can use the  [boot]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_%3a_install_Boot-Repair_in_Ubuntu") program from a LiveCD-USB of Ubuntu.

---

### Post by ugiulio on 2012-12-24
> **catalin.vasilescu said:**
> For general boot problems (even specific problems  UEFI - GPT) with grub-boot-loader you can use the  [boot]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_%3a_install_Boot-Repair_in_Ubuntu") program from a LiveCD-USB of Ubuntu.

As I have written in the first  message, I performed the Ubuntu (12.10 64 bit) installation via Ubuntu Secure Remix that includes boot-repair and other useful tools. And I made use of it as I described at the point (5).
But even using boot-repair, I still cannot access to the Windows recovery environment at the grub2 shell.

---

### Post by YannBuntu on 2012-12-24
Hello
> **ugiulio said:**
> "This computer currently has no detected operating system" and using os-prober I got "/dev/sda6:Windows Recovery Environment (loader):Windows:chain", while I also should got  "/dev/sda2:Window 8.....". Here you can find the Boot Info Script [http://paste.ubuntu.com/1460646/;](http://paste.ubuntu.com/1460646/;)

The problem is that os-prober did not detect your Windows8:

```
=================== os-prober:
/dev/sda8:Sistema operativo ora in uso - Ubuntu-Secure-Remix 12.10 30nov2012 CurrentSession:linux
/dev/sda6:Windows Recovery Environment (loader):Windows:chain
```

Please report this bug here: [https://launchpad.net/ubuntu/+source/os-prober/+filebug](https://launchpad.net/ubuntu/+source/os-prober/+filebug) , then tell us the link so that we can follow-up.

> **ugiulio said:**
> 4) I tried a new installation of Ubuntu selecting "Other" and performing a manual partioning. The installation ended fine. At the first reboot I was only able to load Ubuntu through the grub2. Here you can read the Boot Info script at that moment [http://paste.ubuntu.com/1460627/](http://paste.ubuntu.com/1460627/);
5) so I performed boot-repair to get back Windows loading at the grub2 shell. After that the Boot Info Script was  [http://paste.ubuntu.com/1460646/](http://paste.ubuntu.com/1460646/) (os-prober continues to give only "/dev/sda6:Windows Recovery Environment (loader):Windows:chain");
6) at the next reboot this was what I got at the grub2 options:
a) ubuntu (that loads correctly Ubuntu OS); 
b) advance options for Ubuntu;
c) Windows UEFI loader (that loads properly Windwos 8);
d) Windows Boot UEFI bootx64.efi.bkp (as c);
e)  Windows Recovery Enviroment (loader) (on /dev/sda6) (this gives the following error messages: error: impossible find command'drivemap'; error:  invalid EFI file path; press any key to continue  (and it comes back to grub2);

You did everything right.

> **ugiulio said:**
> How can I get working/loading the Windows Recovery Environment? The problem seems to be located in grub2. Have I to re-install grub? (Boot-repair should already have done it?!?!?!?!)

Yes, Boot-Repair already did it. As said above, the problem is not in GRUB, but in 'os-prober' (which is used by GRUB).

In your GRUB menu, you should have 3 entries created by Boot-Repair:
1) "Windows UEFI loader"
2) "Windows Boot UEFI bootx64.efi.bkp"
3) "Windows Boot UEFI bootx64.efi.bkp sdb1"

1) and 2) should both boot Windows.
3) will probably boot the Windows Recovery. (be careful if you try it, it may break your partition table)

---

### Post by ugiulio on 2012-12-24
Hello YannBuntu!
> **YannBuntu said:**
> 
Please report this bug here: [https://launchpad.net/ubuntu/+source/os-prober/+filebug](https://launchpad.net/ubuntu/+source/os-prober/+filebug) , then tell us the link so that we can follow-up.

I've just report the bug as you suggested: [https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/1093523](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/1093523)

> **YannBuntu said:**
> 
In your GRUB menu, you should have 3 entries created by Boot-Repair:
1) "Windows UEFI loader"
2) "Windows Boot UEFI bootx64.efi.bkp"
3) "Windows Boot UEFI bootx64.efi.bkp sdb1"

1) and 2) should both boot Windows.
3) will probably boot the Windows Recovery. (be careful if you try it, it may break your partition table)

Yep, 1) and 2) options boot Windows 8 , smoothly. I have no (3) option. As I've written in the first message I got "  Windows Recovery Enviroment (loader) (on /dev/sda6)". If I select this option, it gives the  following error messages: error: impossible find command'drivemap';  error:  invalid EFI file path; press any key to c. I hope I ontinue  (and it comes  back to grub2);

Put the bug of os-prober aside for a moment, do you think I could get back the "inaccessible" Windows Recovery Environment via rEFInd, for example?

Thanks for your help. I hope I submitted the bug in the proper way. Correct me if I've made some mistake.

---

### Post by YannBuntu on 2012-12-25
Thanks for the bug report.

> **ugiulio said:**
> I have no (3) option.

My mistake. This one was linked to efi files on your usb stick, so useless.

> **ugiulio said:**
> I got "  Windows Recovery Enviroment (loader) (on /dev/sda6)". If I select this option, it gives the  following error messages

This one can't work, it is due to this GRUB bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

> **ugiulio said:**
> do you think I could get back the "inaccessible" Windows Recovery Environment via rEFInd, for example?

Refind will erase GRUB, and i'm not sure if it can help.

AFAIK, you can simply add a Windows Recovery entry in GRUB by adding the paragraph below at the bottom of the /etc/grub.d/40_custom file of your installed Ubuntu:

```
menuentry "Windows Recovery UEFI" {
search --fs-uuid --no-floppy --set=root D0FC-0E9B
chainloader (\${root})/EFI/Asclepius/bootx64.efi 
}
```

i will try to improve Boot-Repair so that it automatically adds Recovery entries.

EDIT: done. The last version of Boot-Repair ([3.197ppa8]("https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages")) should automatically add an "Other /EFI/Asclepius/bootx64.efi recovery" entry in your GRUB menu.

---

### Post by shoryuken on 2012-12-25
Hi, I don't mean to hijack this thread but I seem to be having the exact same problem as ugiulio with my new Ultrabook (S46CA). I can boot into Windows and Ubuntu but not into Windows Recovery.

I just installed and ran the new version of boot-recovery (boot-sav-extra_3.197~ppa10~quantal_all.deb) and still having the same problem. Here is the result of boot-repair: [http://paste.ubuntu.com/1466219/](http://paste.ubuntu.com/1466219/)


And in case it might be of use, here is the content of grub.cfg

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

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  ca6b5778-6ce5-4b46-b511-24d70cdb1ebd
else
  search --no-floppy --fs-uuid --set=root ca6b5778-6ce5-4b46-b511-24d70cdb1ebd
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
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
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ca6b5778-6ce5-4b46-b511-24d70cdb1ebd' {
recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  ca6b5778-6ce5-4b46-b511-24d70cdb1ebd
	else
	  search --no-floppy --fs-uuid --set=root ca6b5778-6ce5-4b46-b511-24d70cdb1ebd
	fi
	linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=ca6b5778-6ce5-4b46-b511-24d70cdb1ebd ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ca6b5778-6ce5-4b46-b511-24d70cdb1ebd' {
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-ca6b5778-6ce5-4b46-b511-24d70cdb1ebd' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  ca6b5778-6ce5-4b46-b511-24d70cdb1ebd
		else
		  search --no-floppy --fs-uuid --set=root ca6b5778-6ce5-4b46-b511-24d70cdb1ebd
		fi
		echo	'Loading Linux 3.5.0-17-generic ...'
		linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=ca6b5778-6ce5-4b46-b511-24d70cdb1ebd ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-17-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-ca6b5778-6ce5-4b46-b511-24d70cdb1ebd' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  ca6b5778-6ce5-4b46-b511-24d70cdb1ebd
		else
		  search --no-floppy --fs-uuid --set=root ca6b5778-6ce5-4b46-b511-24d70cdb1ebd
		fi
		echo	'Loading Linux 3.5.0-17-generic ...'
		linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=ca6b5778-6ce5-4b46-b511-24d70cdb1ebd ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-17-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI loader" {
search --fs-uuid --no-floppy --set=root 02F6-23A5
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi.bkp
}

menuentry "Windows Boot UEFI bootx64.efi.bkp" {
search --fs-uuid --no-floppy --set=root 02F6-23A5
chainloader (${root})/EFI/Boot/bootx64.efi.bkp
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-1072DD5B72DD45DE' {
	insmod part_gpt
	insmod ntfs
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  1072DD5B72DD45DE
	else
	  search --no-floppy --fs-uuid --set=root 1072DD5B72DD45DE
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Windows 8 (loader) (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-B6C4E84CC4E81103' {
	insmod part_gpt
	insmod ntfs
	set root='hd0,gpt4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  B6C4E84CC4E81103
	else
	  search --no-floppy --fs-uuid --set=root B6C4E84CC4E81103
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```


Attached you will find screen captures of the various partitions on sda and sdb

on sda:
partition 5 is /
partition 7 is /home
partition 8 is /SWAP

partition 2 is Recovery
partition 9 is Restore

Any help is greatly appreciated

Cheers

Shoryuken

---

### Post by oldfred on 2012-12-26
I am not real familiar with Windows 8. 

With Windows 7 there were two recovery partitions. Windows & Vendor.

Windows called its boot/repair a recovery partition and either booted system or with f8 got you into the repair console. You could make a repairCD from there also, so if  you cannot boot you still could make repairs.

The Vendor recovery was an image of the hard drive as purchased. It could restore system to as purchased as it was just an image not an install DVD set. But it usually allowed you to make a set of DVDs in case you had to restore if hard drive totally failed.

Which recovery is it that you want to get into?

       Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by shoryuken on 2012-12-26
> **oldfred said:**
> 

Windows called its boot/repair a recovery partition and either booted system or with f8 got you into the repair console. You could make a repairCD from there also, so if  you cannot boot you still could make repairs.

The Vendor recovery was an image of the hard drive as purchased. It could restore system to as purchased as it was just an image not an install DVD set. But it usually allowed you to make a set of DVDs in case you had to restore if hard drive totally failed.

Which recovery is it that you want to get into?


Thanks oldfred, 

I'm trying to get into the repair (F8) partition. Unfortunately ASUS didn't include a tool to make recovery CDs (a search on Google showed a thread where someone with Windows 8 contacted ASUS who confirmed no tools).

I looked at the link you provided but since I don't have a Windows 8 iso I can't make a bootale flash drive either. 

Cheers 

Shoryuken

---

### Post by YannBuntu on 2012-12-26
**@shoryuken:** i don't see any EFI Recovery file, so your Recovery is probably available only in Legacy mode. This is very different from ugiulio's case, so please create a new thread (then just indicate its link).

---

### Post by shoryuken on 2012-12-26
> **YannBuntu said:**
> **@shoryuken:** i don't see any EFI Recovery file, so your Recovery is probably available only in Legacy mode. This is very different from ugiulio's case, so please create a new thread (then just indicate its link).
Thanks YannBuntu. I've started a new thread as per your suggestion ([http://ubuntuforums.org/showthread.php?t=2098477](http://ubuntuforums.org/showthread.php?t=2098477)).

Cheers

---

### Post by ugiulio on 2012-12-27
> 
AFAIK, you can simply add a Windows Recovery entry in GRUB by adding the paragraph below in the /etc/grub.d/25_custom file of your installed Ubuntu:

```
menuentry "Windows Recovery UEFI" {
search --fs-uuid --no-floppy --set=root D0FC-0E9B
chainloader (\${root})/EFI/Asclepius/bootx64.efi 
}
```i will try to improve Boot-Repair so that it automatically adds Recovery entries.

EDIT: done. The last version of Boot-Repair ([3.197ppa8]("https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages")) should automatically add an "Other /EFI/Asclepius/bootx64.efi recovery" entry in your GRUB menu.First of all sorry for the delay.

I tried to edit 25_custom file as u suggested but no effect on grub. Then I tried to update the Boot-repair tool but no effect as well. 
I noted the action of Boot-repair on 25_custom file is to erase the previous manually added menuentry command. 
Ultimately, nothing's changed. :(

Thanks for your help

---

### Post by YannBuntu on 2012-12-27
> **ugiulio said:**
> I tried to edit 25_custom file as u suggested but no effect on grub.

(sorry i forgot to mention you need to type "sudo update-grub" after this. And better adding the entry inside 40_custom instead of 25_custom.)


Please update Boot-Repair , click the Recommended Repair, and indicate the new URL that will appear.

---

### Post by ugiulio on 2012-12-28
> **YannBuntu said:**
> (sorry i forgot to mention you need to type "sudo update-grub" after this. And better adding the entry inside 40_custom instead of 25_custom.)


Please update Boot-Repair , click the Recommended Repair, and indicate the new URL that will appear.
  
Goodmorning YannBuntu,

I report my tests:
1) I edited 25_custom file and then I updated grub. At the next reboot it showed properly the option "Windows Recovery UEFI" and it worked fine; after that I performed Boot-Repair (using the last version available) but its action is destructive: it erases the previous additional menuentry "Windows Recovery UEFI". Here u can read the Boot info: [http://paste.ubuntu.com/1472285/](http://paste.ubuntu.com/1472285/)
2) I edited 40_custom file and then I updated grub. At the next reboot it showed the option "Windows Recovery UEFI" and it ran smoothly.
3) After that I used the Boot-Repair tool and this is the  Boot script info: [http://paste.ubuntu.com/1472293/](http://paste.ubuntu.com/1472293/) At the next reboot, the grub menu showed the "Windows Recovery UEFI" option as before (and it works correctly)

So the bottom line seems to be: Boot-Repair acts on 25_custom file but not on 40_custom one. 
But the main result is that every option is available right now!

PS:
This is 25_custom file
```

#!/bin/sh
exec tail -n +3 $0

menuentry "Windows UEFI loader" {
search --fs-uuid --no-floppy --set=root 1E22-A9BC
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi.bkp
}

menuentry "Windows Boot UEFI bootx64.efi.bkp" {
search --fs-uuid --no-floppy --set=root 1E22-A9BC
chainloader (${root})/EFI/Boot/bootx64.efi.bkp
}

```and this is 40_custom file
```

#!/bin/sh
exec tail -n +3 $0

menuentry "Windows Recovery UEFI" {
search --fs-uuid --no-floppy --set=root D0FC-0E9B
chainloader (${root})/EFI/Asclepius/bootx64.efi 
}
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```Thanks again for ur precious help!!!

---

### Post by YannBuntu on 2012-12-28
Glad it helped, and thanks for your feedback.
I think the correct entry wasn't automatically added by Boot-Repair because sda6 also contains Legacy files (bootmgr). I updated Boot-Repair for this (boot-sav3.197~ppa12) in the PPA, please could you:
1) test this update and tell me if it adds the entry in 25_custom?

Also, please could you:
2) run Boot-Repair --> Advanced options --> untick "Backup and rename EFI files" --> tick "Restore EFI backups" --> Apply, then indicate the new URL , then reboot, and tell me if GRUB appears? 
3) if it doesn't, enter your BIOS and set up to boot Ubuntu (in the boot order), then tell me if the "Windows UEFI loader" now boot Windows ?

> **ugiulio said:**
> Boot-Repair acts on 25_custom file but not on 40_custom one.

Correct. (25_custom doesn't exist by default, it is created by Boot-Repair.)

---

### Post by ugiulio on 2012-12-29
Hello Yann!!!

> **YannBuntu said:**
> Glad it helped, and thanks for your feedback.
I think the correct entry wasn't automatically added by Boot-Repair because sda6 also contains Legacy files (bootmgr). I updated Boot-Repair for this (boot-sav3.197~ppa12) in the PPA, please could you:
1) test this update and tell me if it adds the entry in 25_custom?

Nope
> 
Also, please could you:
2) run Boot-Repair --> Advanced options --> untick "Backup and rename EFI files" --> tick "Restore EFI backups" --> Apply, then indicate the new URL , then reboot, and tell me if GRUB appears? 
U hit the mark!!!!! \\:D/ This sequence of commands adds the required entry in 25_custom file and at the next reboot grub showed correctly the new option: every entry works fine!!! Here u can read the Boot Info Script: paste.ubuntu.com/1475036/
Now 25_custom file is in this way:
```

#!/bin/sh
exec tail -n +3 $0

menuentry "Windows UEFI loader" {
search --fs-uuid --no-floppy --set=root 1E22-A9BC
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI bootx64.efi" {
search --fs-uuid --no-floppy --set=root 1E22-A9BC
chainloader (${root})/EFI/Boot/bootx64.efi
}

menuentry "Other UEFI bootx64.efi recovery" {
search --fs-uuid --no-floppy --set=root D0FC-0E9B
chainloader (${root})/EFI/Asclepius/bootx64.efi
}

```Then I took the freedom to erase the "Windows Recovery UEFI" entry in 40_custom file. After updating grub, I saw that everything works.

Congratulations for ur great work  =D>
Feel free to contact me again if I can help u out! Have a nice day

---

### Post by YannBuntu on 2013-01-01
Great! :)

Please don't forget to mark this thread [SOLVED] via the thread tools.

---

