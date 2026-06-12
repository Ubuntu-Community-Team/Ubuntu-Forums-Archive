---
title: "Upgrade lost Win 10, GRUB and BIOS"
date: 2018-08-31
forum: Installation &amp; Upgrades
---

### Post by hans12345 on 2018-08-31
I had a dual boot Win 10 / Ubuntu 16.04 system
This is my backup desktop, ACER Aspire XC-605, which I keep to run Win 10 - which happens rarely.
There have been no changes to the PC for some months.

I think I may have made a mistake in my upgrade to 18.04

Now on the ACER I cannot access Win 10, and GRUB has gone too.
More remarkably, I cannot access UEFI / BIOS.  The PC beeps correctly on startup.

When I try to get to the BIOS (F2 on the ACER) the desktop screen goes black and the disk light goes off. Cold boot does not help.
If I restart and do nothing, the ACER boots directly to Ubuntu. Nothing appears on the screen before Ubuntu.
I have looked at the logfile but there is nothing that appears abnormal. 

I imagine that I either overwrote the old UEFI or have managed to create a second new one if that is possible.

I cannot run Boot-Repair from the CD. It is not boot-able and of course I cannot access the BIOS to allow a CD boot.

I could run Boot-Repair from within Ubuntu, but is this the best thing to do?

Any advice?

---

### Post by yancek on 2018-08-31
> I could run Boot-Repair from within Ubuntu, but is this the best thing to do?

Only on the condition that you use the 2nd option on the page to use the ppa rather than the iso (more up to date) and when you run boot repair, do NOT try to make repairs but select the option to Create BootINfo Summary and post the link you are given here.  Members will then be able to see detailed information on your system and there are some members here who have extensive knowledge on Grub/Boot problems and should be able to make suggestions.  Again, do NOT try to make any repairs.

---

### Post by hans12345 on 2018-08-31
Thanks Yancek

I have done as you suggest.

The pasted BootINfo Summary file is Qbx9xgi7hK

---

### Post by oldfred on 2018-08-31
You need to paste the full address given, so we just need to click on it.
I tried to recreate it using mine & your posted data, but this did not work.
[http://paste.ubuntu.com/p/Qbx9xgi7hK/](http://paste.ubuntu.com/p/Qbx9xgi7hK/)

---

### Post by hans12345 on 2018-08-31
Sorry about the misplaced paste. I think it may have gone to pastebin.

I have repeated the process and sent it manually to:

[https://paste.ubuntu.com/p/ryhSpVg8Xq/]("https://paste.ubuntu.com/p/ryhSpVg8Xq/")

---

### Post by oldfred on 2018-08-31
I do not see much wrong.
The UEFI boot entry shows ubuntu. 
Acer requires the "trust" setting, so I assume you must have renamed an unknown setting to ubuntu?

You are showing Windows is hibernated. So then grub cannot boot Windows.
Windows on many updates turns fast start up back on.
You still should be able to directly boot Windows from UEFI boot menu, but need to press boot key often f10 or f12, check manual.
If not you need to use your Windows repair disk.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Also if UEFI fast boot is on, you have little or no time to press any key to get into UEFI. Cold boot usually work, but some have to totally reset UEFI. Most desktops have jumper pins on motherboard, or remove coin battery.
On my Asus system I tried cold boot, jumpering pins, removing coin battery, none worked. But I disconnected default drive and that reset something, but had to boot from flash drive and recreate UEFI boot entries.

---

### Post by hans12345 on 2018-08-31
Hi OldFred

Good to see you in my thread.

> **oldfred said:**
> I do not see much wrong.
The UEFI boot entry shows ubuntu. 
Acer requires the "trust" setting, so I assume you must have renamed an unknown setting to ubuntu?

You are showing Windows is hibernated. So then grub cannot boot Windows.


Please note, I have no Grub.

> 
Windows on many updates turns fast start up back on.


Tricky!

> 
You still should be able to directly boot Windows from UEFI boot menu, but need to press boot key often f10 or f12, check manual.
If not you need to use your Windows repair disk.



I cannot get to the UEFI
I cannot use a Windows repair disk, no UEFI means I cannot change boot sequence.

> 
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Also if UEFI fast boot is on, you have little or no time to press any key to get into UEFI. Cold boot usually work, but some have to totally reset UEFI. Most desktops have jumper pins on motherboard, or remove coin battery.
On my Asus system I tried cold boot, jumpering pins, removing coin battery, none worked. But I disconnected default drive and that reset something, but had to boot from flash drive and recreate UEFI boot entries.

Let me be clear about the various sequences. If I coldboot then I get a beep, then the screen remains black, then:
- I do nothing, after a while Ubuntu starts. Nothing shows before the purple of Ubuntu's first screen. No manufacturers banner page and no grub.
- If I keep shift depressed, same as above.
- If I press and other key Del, F2, F7, F12 (this is the key for the Win Boot menu on ACER), then no manufacturers banner page and no grub and the screen remains black with the disk light off. Nothing is happening.

From what you say, in this last case Windows is hibernating. How can I stop it hibernating? Or is the hibernation file corrupted?

How can I do a Win rescue? I see there is a rescue partition.

What is my next step?
- a Win rescue?
- open the box and look for jumper pins?
- somehow reset FastBoot?
- delete the hibernation file? (assuming I can find it)

---

### Post by oldfred on 2018-08-31
Do not run Win rescue as on some systems that totally erases everything & restores to as purchased. Other do a fix, but do not like having anything other than Windows.

Can you press escape when starting to boot? That should give you grub menu.
Or start to press down arrow key. If in grub menu (even if you cannot see it), it changes the default boot. Last in grub menu is boot into UEFI. But not sure how many down arrow presses required. But it may then show menu.

UEFI fast boot is probably booting so fast you cannot press keys to get into UEFI directly.

---

### Post by hans12345 on 2018-09-01
Thanks again OldFred

> **oldfred said:**
> Do not run Win rescue as on some systems that totally erases everything & restores to as purchased. Other do a fix, but do not like having anything other than Windows.

Can you press escape when starting to boot? That should give you grub menu.
Or start to press down arrow key. If in grub menu (even if you cannot see it), it changes the default boot. Last in grub menu is boot into UEFI. But not sure how many down arrow presses required. But it may then show menu.

UEFI fast boot is probably booting so fast you cannot press keys to get into UEFI directly.

Now I'm really lost.

I tried the escape, but it goes, as usual, into its black screen/no disk activity status. Just like when I use the F keys.

Then I tried the invisible grub idea.
After a cold boot, I hit the down arrow many times, waited, then hit enter.
The PC did something for about 10 minutes. Lots of disk activity. Still a black screen. What was it doing in this long period of disk activity?
Now it sits there, black screen but alive in as much as the disk light flashes on from time to time, not regularly. But after a while it peeps and I think it maybe goes into hibernation !


Some notes:
1. I looked on my other 2 PCs (this one, my main one and my little laptop) and both show “System settings” option on the bottom of the grub menu. But this should reboot the computer into the BIOS / UEFI options. It seems unlikely that this grub option has been chosen. What option was being followed?
2. My screen has a status light. Briefly when I start, the status is yellow = no video signal. 
When I coldboot and do nothing and after a while Ubuntu starts, the status is blue even though the screen is black until such time as the purple Ubuntu screen appears. 
When I coldboot and then a touch a key the system appears to turn off, no disk activity, yellow status light. Could this be a video problem? Unlikely since the status light and the disk activity seem to work (or not) together.

At least I still have Ubuntu.

Any ideas really appreciated.

---

### Post by oldfred on 2018-09-01
That is typical of graphic issues.
Most often now with nVidia, but then you need to get into grub menu to edit linux line and add nomodeset.
Without knowing how many down arrows or exactly when system is at grub menu so recognizing down arrow it is difficult to know where you are at.
Try down arrow, up arrow & e for edit? 

Some laptop/tablet systems have a reset pin on bottom, or desktops have jumper pins to reset system or remove coin battery for a bit to drain and fully reset everything in UEFI. You then have to redo some UEFI settings ( it has its own memory). With old BIOS it lost all settings.

---

### Post by hans12345 on 2018-09-01
Thanks for the input.

> **oldfred said:**
> That is typical of graphic issues.
Most often now with nVidia, but then you need to get into grub menu to edit linux line and add nomodeset.
.
This is a standard Intel PC, with Intel graphics, no graphics card

> 
Without knowing how many down arrows or exactly when system is at grub menu so recognizing down arrow it is difficult to know where you are at.
Try down arrow, up arrow & e for edit? 


I tried. Same failures as usual, black screen and yellow status, no disk activity.
But I did discover something new.
With this inactive state (eg black screen and yellow status, no disk activity) I can wake the PC up with multiple CTRL-ALT-DEL presses, then a ENTER. Then Ubuntu starts. This is repeatable. eg I reboot and hit F12 (the Win Boot menu normally) then the CTRL-ALT-DEL presses, then a ENTER and I still get Ubuntu.

So what inactive state is it in that allows CTRL-ALT-DEL presses, then a ENTER to wake it up and start Ubuntu?
> 
Some laptop/tablet systems have a reset pin on bottom, or desktops have jumper pins to reset system or remove coin battery for a bit to drain and fully reset everything in UEFI. You then have to redo some UEFI settings ( it has its own memory). With old BIOS it lost all settings.

Is this the best thing to try next?

---

### Post by oldfred on 2018-09-01
Is Ubuntu then working ok, once you get into it?

I might try a full reinstall of grub.
Often easier with Boot-Repair, but you can do it just from synaptic or command line.
UEFI version of grub is grub-efi-amd64.

Also this:
       Reboot into UEFI:
sudo systemctl reboot --firmware

---

### Post by hans12345 on 2018-09-02
> **oldfred said:**
> Is Ubuntu then working ok, once you get into it?

Yes, Ubuntu works fine.
> 
I might try a full reinstall of grub.
Often easier with Boot-Repair, but you can do it just from synaptic or command line.
UEFI version of grub is grub-efi-amd64.

Also this:
       Reboot into UEFI:
sudo systemctl reboot --firmware

The reboot into the firmware failed. Just black screen, yellow status, no disk activity.
This was a pity because I was hoping to do a full disk image copy with my CD of Clonezilla Live, but without access to the BIOS I cannot boot from CD.

I can try the grub re-install but would prefer to do the backup first.

BTW, I did some research on grub.cfg - the last entry was a system restore to an old version of Linux. The disk activity was apparently the system going into recovery mode. So it looks like Grub is working but just not talking to the screen.
Does Grub write to the log files?
Can I do anything useful by modifying the grub.config?

---

### Post by hans12345 on 2018-09-02
Here is the Grub Config:
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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

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
set root='hd0,gpt7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  ddf6bd8d-e247-4adf-bc2c-249a64cebf27
else
  search --no-floppy --fs-uuid --set=root ddf6bd8d-e247-4adf-bc2c-249a64cebf27
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ddf6bd8d-e247-4adf-bc2c-249a64cebf27' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  ddf6bd8d-e247-4adf-bc2c-249a64cebf27
	else
	  search --no-floppy --fs-uuid --set=root ddf6bd8d-e247-4adf-bc2c-249a64cebf27
	fi
        linux	/boot/vmlinuz-4.15.0-33-generic root=UUID=ddf6bd8d-e247-4adf-bc2c-249a64cebf27 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-4.15.0-33-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ddf6bd8d-e247-4adf-bc2c-249a64cebf27' {
	menuentry 'Ubuntu, with Linux 4.15.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-33-generic-advanced-ddf6bd8d-e247-4adf-bc2c-249a64cebf27' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		else
		  search --no-floppy --fs-uuid --set=root ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		fi
		echo	'Loading Linux 4.15.0-33-generic ...'
	        linux	/boot/vmlinuz-4.15.0-33-generic root=UUID=ddf6bd8d-e247-4adf-bc2c-249a64cebf27 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-33-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-33-generic-recovery-ddf6bd8d-e247-4adf-bc2c-249a64cebf27' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		else
		  search --no-floppy --fs-uuid --set=root ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		fi
		echo	'Loading Linux 4.15.0-33-generic ...'
	        linux	/boot/vmlinuz-4.15.0-33-generic root=UUID=ddf6bd8d-e247-4adf-bc2c-249a64cebf27 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-33-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-30-generic-advanced-ddf6bd8d-e247-4adf-bc2c-249a64cebf27' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		else
		  search --no-floppy --fs-uuid --set=root ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		fi
		echo	'Loading Linux 4.15.0-30-generic ...'
	        linux	/boot/vmlinuz-4.15.0-30-generic root=UUID=ddf6bd8d-e247-4adf-bc2c-249a64cebf27 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-30-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-30-generic-recovery-ddf6bd8d-e247-4adf-bc2c-249a64cebf27' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		else
		  search --no-floppy --fs-uuid --set=root ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		fi
		echo	'Loading Linux 4.15.0-30-generic ...'
	        linux	/boot/vmlinuz-4.15.0-30-generic root=UUID=ddf6bd8d-e247-4adf-bc2c-249a64cebf27 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-30-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-33-generic-advanced-ddf6bd8d-e247-4adf-bc2c-249a64cebf27' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		else
		  search --no-floppy --fs-uuid --set=root ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		fi
		echo	'Loading Linux 3.19.0-33-generic ...'
		linux	/boot/vmlinuz-3.19.0-33-generic.efi.signed root=UUID=ddf6bd8d-e247-4adf-bc2c-249a64cebf27 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-33-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-33-generic-recovery-ddf6bd8d-e247-4adf-bc2c-249a64cebf27' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		else
		  search --no-floppy --fs-uuid --set=root ddf6bd8d-e247-4adf-bc2c-249a64cebf27
		fi
		echo	'Loading Linux 3.19.0-33-generic ...'
		linux	/boot/vmlinuz-3.19.0-33-generic.efi.signed root=UUID=ddf6bd8d-e247-4adf-bc2c-249a64cebf27 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.19.0-33-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-F8E1-EA77' {
	insmod part_gpt
	insmod fat
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  F8E1-EA77
	else
	  search --no-floppy --fs-uuid --set=root F8E1-EA77
	fi
	chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
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

---

### Post by yancek on 2018-09-02
> Can I do anything useful by modifying the grub.config? 				

It is not recommended to do that as stated at the top of the file and the reason why just below.  The only situation where it could be useful to modify is to test. 

Your grub.cfg shows the primary Ubuntu menuentry, then the Advanced entry and finally the windows entry.  I'm not sure what the problem is here as you have the correct EFI files for windows and the menuentry for windows is correct.  As a guess, you might try rebooting and knowing that windows is the third entry, hit the down arrow twice when you initially see the black screen then hit the Enter key to try booting windows.  Not being able to access the BIOS would be a separate problem from Grub and I'm not sure what the problem would be there.

---

### Post by oldfred on 2018-09-02
I thought grub tries to use the video mode of your install.
But it does have some default video settings. But it also could be a video setting in you UEFI.
You want what monitor is, as long as video chip supports it.

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

I never have changed any grub video settings.
       sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
sudo nano /etc/default/grub 
    sudo update-grub

---

### Post by hans12345 on 2018-09-03
> **yancek said:**
> It is not recommended to do that as stated at the top of the file and the reason why just below.  The only situation where it could be useful to modify is to test. 

Your grub.cfg shows the primary Ubuntu menuentry, then the Advanced entry and finally the windows entry.  I'm not sure what the problem is here as you have the correct EFI files for windows and the menuentry for windows is correct.  As a guess, you might try rebooting and knowing that windows is the third entry, hit the down arrow twice when you initially see the black screen then hit the Enter key to try booting windows.  Not being able to access the BIOS would be a separate problem from Grub and I'm not sure what the problem would be there.

Thanks Yancek

I am a bit slow to answer, but Sunday is family day.

No, I was not going to edit the confog file. But maybe, with advice, I could change the settings in /etc/default/grub?

I tried your double down arrow idea.

After a cold boot, I hit the down arrow twice slowly, waited, then hit enter. (It is quite possible the first one failed by being too early)
The PC did something for about 2 minutes. Lots of disk activity. Still a black screen. What was it doing in this period of disk activity? Then the disk light will flash occasionally. Then a period of activity again.
Then I tried multiple CTRL-ALT-DEL presses, but nothing happened. Black screen with occasional disk light flashes.

(I should mention that to start Win 10 in the past, I did not use Grub. After the ACER screen, I would hit F12 and get the Windows Boot menu, from where I could enter Win 10)

---

### Post by oldfred on 2018-09-03
We may be down to a full cold boot & jumper pins on motherboard. You need to check your manual, they usually are near the coin battery. Alternative is removing coin battery. Wait a while for all power to drain.
I had to do that and it did not work recently. But unplugging a drive resets all UEFI boot entries, so I also did that and then when I plugged drive back in it worked. Not sure if I had to do both, or what issue was?

But back in BIOS days total reset or update to BIOS reset all settings. With UEFI it has its own memory, but some settings are still reset to defaults. I keep a list of 5 or 10 settings, some required & some optional that I change or verify not changed.

---

### Post by hans12345 on 2018-09-03
> **oldfred said:**
> I thought grub tries to use the video mode of your install.
But it does have some default video settings. But it also could be a video setting in you UEFI.
You want what monitor is, as long as video chip supports it.

I think a bad video setting in the UEFI could explain a lot.
> 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

I tried this GRUB_GFXMODE=640x480 and ran upgrade-grub
No change
> 
I never have changed any grub video settings.
       sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
sudo nano /etc/default/grub 
    sudo update-grub
I did also check that my monitor runs MODE=640x480, and it does.

Any more ideas?
If not, I think I will try to find the jumpers to reset the UEFI CMOS

---

### Post by oldfred on 2018-09-03
I am grasping at the last straw, or out of ideas.

---

### Post by westie457 on 2018-09-03
Hi, I have absolutely no idea if this will work, possibly some of your partitions are slightly corrupted.
The following will take a long time to complete. Do not attempt to take any shortcuts.
How do you feel about attempting to rewrite the partition table?
Reading through this thread you are able to boot Ubuntu. Is that correct?
Boot into Ubuntu, open a terminal```
sudo apt install testdisk
sudo testdisk
```Accept the default suggestions as they appear on the screen. Keep going through 'Quick Search' and finally run 'Deeper Search' until it finishes and shows a complete list of partition info found on the hard drive.
Now open another terminal```
sudo fdisk -l
```
Look through the testdisk list and any that match up with the list in 'fdisk' terminal change to a 'P',any that are duplicated take the newest one (this will be the lower in the list than the older ones}. The start points and end points must match exactly. When all partitions have been selected tab to 'Write' and hit Enter. Follow the prompts to Reboot.

Fingers, toes and everything else crossed you should be booting as you would normally.

---

### Post by hans12345 on 2018-09-04
> **westie457 said:**
> Hi, I have absolutely no idea if this will work, possibly some of your partitions are slightly corrupted.
The following will take a long time to complete. Do not attempt to take any shortcuts.
How do you feel about attempting to rewrite the partition table?
Reading through this thread you are able to boot Ubuntu. Is that correctly.

Thanks Westie

Yes, Ubuntu is working perfectly.

Just no banner screen on boot, no UEFI access, no Grub (and of course no Win 10).

I won't follow your idea for the moment, I still need to do a full backup.

The next step is to try to reset the UEFI BIOS.

Crossing my fingers ...

---

### Post by hans12345 on 2018-09-05
I will delay the jumper change to reset the UEFI BIOS.

I think now that this is not a Grub problem, and probably the key aspect is the failure of the ACER banner page to start.

So I am going to post to the PC hardware forums.

Rest assured, if I make progress there I shall report here.

And if I get no good ideas there, I shall consider again the jumper change to reset the UEFI BIOS.

---

### Post by oldfred on 2018-09-05
If you jumper pins or remove coin battery on motherboard be sure to reset all the UEFI settings you changed. 
With BIOS it always reset everything to defaults, now with UEFI, it has its own memory and will save some settings.

---

### Post by hans12345 on 2018-09-06
Breakthrough!

I focussed on the video aspect of the problem.

I noticed that the ACER comes with a HDMI connector to the ACER monitor.

So I tried an old monitor which will support VGA.

It works. Now I have one black screen and one working VGA screen.

The ACER banner appears only on the VGA monitor. And I can boot from a DVD. (It happens to be memtest, which is the one I normally start with when I have a problem)

Now how do I get the banner page and grub on the HDMI monitor (which was working a short time ago)?

---

### Post by oldfred on 2018-09-06
Is that a setting in UEFI, on which video out to use? Or configuration of grub/Ubuntu.
Acer banner is before grub, so would be an UEFI setting.

---

### Post by hans12345 on 2018-09-06
Breakthrough report #2:

Now I am back to a fairly normal problem (ignoring the HDMI monitor one for the moment) for this forum.

The ACER, using the VGA screen, now only boots into Win10. No grub, no Ubuntu.

BIOS / UEFI status
No secure boot (and I imagine no fastboot, but the option does not show, I suppose because I had already disable secure boot).
I had these 2 enabled in the BIOS, which I now have disabled:
- Quiet boot (I now get the POST messages)
- Deep Power Offf Mode - this could have been related to the earlier comment about the PC being in Windows hibernation.

So is it time for a boot-repair?

---

### Post by hans12345 on 2018-09-06
Hi OldFred
> **oldfred said:**
> Is that a setting in UEFI, on which video out to use? Or configuration of grub/Ubuntu.
Acer banner is before grub, so would be an UEFI setting.

There is no setting in the UEFI / BIOS setting as to which video to use.

The current sequence is Banner (or now, POST) screen, the straight to Windows.

---

### Post by oldfred on 2018-09-06
I know Acer has to have UEFI Secure boot on to let you enable "trust". Not sure what other settings having Secure Boot on or setting password then opens up.

My Asus motherboard has something called VT-D. But it says only if enabled, you then see graphic settings for primary display, audio, multi-monitor and others.
So often one setting may open lots of other settings. And UEFI Secure Boot can change all of that.

UEFI fast boot and Windows fast start up are two different settings. Did Windows updates turn fast start up back on. 
Or UEFI updates turn fast boot back on. My system does that whenever I update UEFI.

---

### Post by hans12345 on 2018-09-07
> **oldfred said:**
> I know Acer has to have UEFI Secure boot on to let you enable "trust". Not sure what other settings having Secure Boot on or setting password then opens up.

My Asus motherboard has something called VT-D. But it says only if enabled, you then see graphic settings for primary display, audio, multi-monitor and others.
So often one setting may open lots of other settings. And UEFI Secure Boot can change all of that.

I had UEFI Secure boot turned off. I put it back on to look for the Fast boot option. I cannot find it anywhere in the BIOS. Secure boot is now again turned off.
> 
UEFI fast boot and Windows fast start up are two different settings. Did Windows updates turn fast start up back on. 
Or UEFI updates turn fast boot back on. My system does that whenever I update UEFI.

I looked and found that Windows fast start was on. So I switched it off. But no change.
I still boot (on the VGA monitor), with a banner screen, straight to Win 10. No grub.

Shall I try boot-repair now?

---

### Post by hans12345 on 2018-09-07
Another breakthrough.

I was going through all the BIOS options looking for fast boot - which I could not find.
But under boot options I opened the parameter for the hard disk. Inside that, there were 2 options:
- 1st Win Boot manager
- 2nd Ubuntu
So I swapped them around.

Now I am almost home.

I have 2 monitors.
It starts on the VGA one. 
- If I quickly hit F12, I get the Win Boot manager. Then I get Win 10, but on the VGA.
- If I do nothing, it shows Grub in the VGA then the first Ubuntu screen, the one with ubuntu and underneath a line of 5 dots. Then, suddenly, the HDMI monitor starts and the VGA too.

So if I want the nice HDMI monitor, the only problem is that I need to use 2 monitors.

But if I disconnect the HDMI monitor, then everything seems to work with just the VGA one.

---

### Post by hans12345 on 2018-09-10
This is my 2nd desktop and if it only works with a VGA connected monitor, then it is no great loss to me.

I still wonder what happened, but it is time to move on.

Unless anyone has some last comments, I suggest we close this forum thread.

Thanks to everyone who contributed helpful ideas.

---

