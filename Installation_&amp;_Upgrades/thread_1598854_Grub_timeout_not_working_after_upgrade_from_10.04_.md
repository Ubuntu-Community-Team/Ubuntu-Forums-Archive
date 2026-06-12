---
title: "Grub timeout not working after upgrade from 10.04 to 10.10"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by gwi on 2010-10-17
Yesterday I upgraded from 10.04 to 10.10 (x86_64). The upgrade itself succeeded, but now after booting I have to press enter in the grub OS list.
grub.cfg looks like this:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1920x1200

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Why do I have to press enter to have grub boot the default entry?
How can I get grub to start the default entry automatically, without showing the menu?

BTW: entries in the list are default:
```
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
```

---

### Post by pierocol on 2010-10-17
I experience exactly the same issue and I am not able to find a solution

---

### Post by gwi on 2010-10-18
Funny thing is: on another system (x86) I have 10.10 with an identical grub config, which starts automatically. Just like the x86_64 system did with 10.04.

---

### Post by sikander3786 on 2010-10-18
Your /etc/default/grub looks fine to me.

Please run

```
sudo update-grub
```

Reboot and see if it works now.

---

### Post by heatpumpcontrol on 2010-10-18
This is what I did... and now it's FIXED!!!

Go to Synaptic Package Manager

1- Completely remove 
[INDENT]grub-pc and grub-commom, if you have startupmanager, do it too.[/INDENT]

You will be asked if you want to keep the config files... say NO

2- Reinstall 

grub-pc, grub-common and startupmanager

upon reinstall... select the maintainers version... if prompted at all. (I had a blank window in the prompt so I clicked 'Forward').

3- After install

open startup manager in your Administrations Mmnu

Select the desired timeout
Select a Resolution that's good for you.. for me it was 1024x768
Select your color depth .. for me it was 24 bits

Select the Advanced Tab and choose a Bootloader menu Resolution.. for me it was 1280x1024 

I have a 24" monitor and those resolutions worked best for me.

Good Luck

---

### Post by gwi on 2010-10-19
I already ran update-grub several times, trying different timeout settings for grub.

Your steps for me did:
[LIST=1]
[*]mess up the splash screen (wrong resolution, instead of an Ubuntu logo the text "ubuntu 10.10" in a Courier-like font);
[*]mess up the tty resolution;
[*]NOT fix the original problem, I still have to press Enter to boot the default menu entry.
[/LIST]
Startupmanager is pretty useless. I does not contain the native resolution of my 24" display (1920x1200). And it looks like it messes directly with /etc/grub.d/00_header, instead of using /etc/default/grub. The line ```
set gfxmode=${GRUB_GFXMODE}
``` was replaced with ```
set gfxmode=1600x1200
``` (the closest to my preferred resolution I could select in startupmanager).

So the original question still stands: **why doesn't grub boot the default menu entry?**

(BTW: Using 1280x1024 on a 24" display... I used that resolution on a 17" CRT. If you have an LCD screen I think there is only one right resolution, and that is the native one, and I can't think of a 24" LCD with native 1280x1024.)

---

### Post by Elline on 2010-10-31
Hello folks.
I am first time at this forum and i am quite new to linux at all, but hope i can participate sometime.

Meanwhile i have same problems. Likewise i have x86_64 and upgraded to 10.10 recently. On demand i can provide my /etc/default/grub (which is quite simple as in first post) or "bootscript" output, etc. 

I hope this problem will be solved.

UPD:
So i just tried to reinstall it (grub) through synaptic (as been proposed early in this thread) and for first reboot countdown was shown again but for next it disappeared. It looks very strange.

---

### Post by ridetheteapot on 2010-11-04
I am having this problem as well - though i didn't upgrade, i am still running 10.04.
what i did was - install a new harddrive - booted a live cd, copied most of the partitions from old drive to new one, then fixed the new drives fstab. mounted the new drive's / and then the boot partition to /media/root/boot and installed grub to the mbr of the new drive.

it all booted fine after i swapped the drives. but now my /etc/default/grub seems not to honor my timeout settings.
what i have read is that osprober will override any hidden timeout. i have a windows partition so i commented the hidden options out and set GRUB_TIMEOUT=4
updating grub is not doing it for me though ---- i still have to select manually

---

### Post by alan77ss on 2010-11-14
Ditto, same problem. Installed 10.10 and timeout worked at first, then stopped working. editing and updating grub.cfg doesn't make a difference. annoying.

---

### Post by drs305 on 2010-11-14
Edit: Solved in post # 32.

@ gwi,

I just noticed this thread with the recent additions. One thing that could cause Grub not to boot is the screen resolution you have set. You can check the available resolutions from the grub prompt (press "c" from the Grub menu) by typing "vbeinfo".  If the resolution isn't supported, Grub will await input.

I don't know if either your original or the new one you tried is supported, but I'd just comment out all resolutions and let Grub use the default (which is 640x480 even when that line is commented out). At least you will find out whether or not it's a resolution problem. 

Note: there have been several posts lately about the counter not working. Most likely a 'recordfail' is being generated for some reason. To see if it's a recordfail issue, you can temporarily edit grub.cfg and force 'recordfail' to be ignored:
```
gksu gedit /boot/grub/grub.cfg
```

Add the line in dark red, save the file, do NOT run update-grub and reboot.
> 
insmod gettext
**[COLOR="DarkRed"]recordfail=0[/COLOR]**
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi


The line will be removed once you run "sudo update-grub" the next time.

---

### Post by alan77ss on 2010-11-15
I tried adding recordfail=0 to grub.cfg, but no joy. 

Checked the resolutions available in the grub prompt and my 1900x1200 resolution wasn't supported. So, tried a different resolution and commented out all resolutions in /etc/default/grub to get the default - but again no change, still no timeout.

---

### Post by alan77ss on 2010-11-16
Well my problem is solved, turns out it wasn't grub at all but the extra buttons on my mouse were kicking in when the grub menu loaded and disabling the automatic boot.

thanks to drs305 for the help.

---

### Post by Elline on 2010-11-19
Thank for your advice.
I tried to add "recordfail=0" in the place you point on. Still it don't work for me. I don't see any clues what may cause it. :(

---

### Post by drs305 on 2010-11-19
> **Elline said:**
> Thank for your advice.
I tried to add "recordfail=0" in the place you point on. Still it don't work for me. I don't see any clues what may cause it. :(

If you would like to either post or attach your /etc/default/grub and /boot/grub/grub.cfg files I'd be happy to take a look and see if I can determine the reason. 

Please also confirm your problem is that at the end of the timeout the default does not automatically boot?

---

### Post by Elline on 2010-11-22
Thank you very much for your assistance!

Here I attach the /etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=4
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

I must note I am aiming at use of custom menu entries with my own boot menu entries but now i am with almost default settings.

And here the /boot/grub/grub.cfg
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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 232d0c5e-158a-4e85-8ddc-c0e250a8a53c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 232d0c5e-158a-4e85-8ddc-c0e250a8a53c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 232d0c5e-158a-4e85-8ddc-c0e250a8a53c
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=232d0c5e-158a-4e85-8ddc-c0e250a8a53c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 232d0c5e-158a-4e85-8ddc-c0e250a8a53c
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=232d0c5e-158a-4e85-8ddc-c0e250a8a53c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 232d0c5e-158a-4e85-8ddc-c0e250a8a53c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=232d0c5e-158a-4e85-8ddc-c0e250a8a53c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 232d0c5e-158a-4e85-8ddc-c0e250a8a53c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=232d0c5e-158a-4e85-8ddc-c0e250a8a53c ro single 
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 232d0c5e-158a-4e85-8ddc-c0e250a8a53c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 232d0c5e-158a-4e85-8ddc-c0e250a8a53c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 06c0bfc0c0bfb471
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod reiserfs
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 56de3168-935a-4a2b-9f28-2ce2490f6f6f
	linux /boot/vmlinuz-2.6.24-28-generic root=UUID=56de3168-935a-4a2b-9f28-2ce2490f6f6f ro quiet splash
	initrd /boot/initrd.img-2.6.24-28-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod reiserfs
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 56de3168-935a-4a2b-9f28-2ce2490f6f6f
	linux /boot/vmlinuz-2.6.24-28-generic root=UUID=56de3168-935a-4a2b-9f28-2ce2490f6f6f ro single
	initrd /boot/initrd.img-2.6.24-28-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (on /dev/sda6)" {
	insmod part_msdos
	insmod reiserfs
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 56de3168-935a-4a2b-9f28-2ce2490f6f6f
	linux /boot/vmlinuz-2.6.24-26-generic root=UUID=56de3168-935a-4a2b-9f28-2ce2490f6f6f ro quiet splash
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sda6)" {
	insmod part_msdos
	insmod reiserfs
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 56de3168-935a-4a2b-9f28-2ce2490f6f6f
	linux /boot/vmlinuz-2.6.24-26-generic root=UUID=56de3168-935a-4a2b-9f28-2ce2490f6f6f ro single
	initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.4 LTS, memtest86+ (on /dev/sda6)" {
	insmod part_msdos
	insmod reiserfs
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 56de3168-935a-4a2b-9f28-2ce2490f6f6f
	linux /boot/memtest86+.bin 
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 3d3a5c72-cb07-48d7-9586-99616c1b0937
	linux /boot/vmlinuz-2.6.35.6-45.fc14.x86_64 root=/dev/sda7
	initrd /boot/initramfs-2.6.35.6-45.fc14.x86_64.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
#menuentry "mymenu" {
#configfile /boot/grub/mymenu.cfg
#}
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

Yes, I am confirming that at end of (imaginary, without any marks) timeout default boot entry doesn't loads. Though I can choose the default.

---

### Post by drs305 on 2010-11-22
Elline,

I used your grub file (/etc/default/grub) and on my system it booted automatically after the timeout. This isn't surprising as you have a default file except for the 4 second timeout.

We can try to figure out what is causing the problem by isolating what is included in the menu.

1,  First, let's try removing Windows and memtest. They are included in the menu by the scripts in /etc/grub.d/ folder. We will make those scripts non-executable and then update grub and see if the problem remains. After checking, we can turn them back on again.

```
sudo chmod -x /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober
sudo update-grub

```
Reboot and see if it still freezes.


2. If it still doesn't work, return the scripts to their original state and open /boot/grub/grub.cfg for editing:
```
sudo chmod +x /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober
sudo update-grub
gksu gedit +56 /boot/grub/grub.cfg

```
Normally we don't edit grub.cfg, since any time update-grub is run it gets rewritten. But we want to see if the 'recordfail' check is causing the problem, so we will amend it so it doesn't stop the boot process.

Find this line and change the **[COLOR="DarkRed"]-1[/COLOR]** to **[COLOR="DarkRed"]10[/COLOR]**. Gedit should have opened on or near the line we are going to change.
> 
if [ "${recordfail}" = 1 ]; then
  set timeout=**[COLOR="DarkRed"]10[/COLOR]**
else
  set timeout=4
fi

DO NOT UPDATE GRUB or the change will be overwritten.
Reboot and check to see if it automatically boots after a delay. Please note whether the countdown is 4 seconds or 10 seconds.

3. The third thing we can try is to automatically boot the 'saved' OS. This will be the one you booted last. 

Once you boot, open /etc/default/grub for editing and change the DEFAULT=0 setting to "saved and add the additional line.
```
gksu gedit +4 /etc/default/grub
```
> 
DEFAULT=saved
GRUB_SAVEDEFAULT=true

Next set the saved entry. From the next boot, it will always highlight the last one you booted (hopefully with a timeout followed by an auto-boot). Finally update grub:
```

sudo grub-set-default 0
sudo update-grub
```
Reboot.


Stop when any of these procedures produce an automatic boot after the timeout. Please let us know what happens.

---

### Post by Elline on 2010-11-23
1) Doesn't made a thing. Only main ubuntu maverick stays.

2) Countdown appeared! With 10. What should I do now? I guess it's not a normal state nevertheless.

Afterwards thank you very much for all the time wasted and all your detailed directions. In addition if it will be supposed to make more you can skip so in-detailed command line instructions (e.g. chmod, gedit, etc.) so I can handle it.
Furthermore a big thanks for all yours assistances.

---

### Post by drs305 on 2010-11-23
Elline,

I am not sure if you didn't want commands or if you just didn't need the explanations. If you didn't want commands, sorry  - here they come again!  ;-)

For reasons I can't determine, the 'recordfail' check is finding an error. If everything seems to work normally (besides the timeout), we can make the change permanent (so you can also run update-grub). This *bypasses* the problem and lets the system boot after a countdown.

Open two files:
```
gksudo gedit /etc/default/grub /etc/grub.d/00_header
```
In /etc/default/grub, add these 2 lines. Change the '10' to the number of seconds you want to see the menu. My suggestion would be to make it different than "4". "4" is the number of seconds it *should* delay. If you start seeing "4", your problem has gone away. Until then, it will display for whatever time you put as the RECORDFAIL_TIMEOUT.
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
**[COLOR="DarkRed"]# My additions:[/COLOR]**
**[COLOR="DarkRed"]RECORDFAIL_TIMEOUT=10[/COLOR]**
**[COLOR="DarkRed"]export RECORDFAIL_TIMEOUT[/COLOR]**
In /etc/grub.d/00_header, change:
> 
if [ "\${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=${2}
fi


to:
> 
if [ "\${recordfail}" = 1 ]; then
**[COLOR="DarkRed"]# set timeout=-1[/COLOR]**
  **[COLOR="DarkRed"]set timeout=${RECORDFAIL_TIMEOUT}[/COLOR]**
else
  set timeout=${2}
fi


Update grub and you should be done:
```
sudo update-grub
```

Happy Ubuntu-ing !

---

### Post by Elline on 2010-11-24
It works! Thank you very much!

I'm not native English, I meant you would skip the explanations, just say open this and that, here.

I hope this "workaround" could no case any serious injuries in the future. Moreover thank you very very very much!
Now I am going to create my custom menu.

One humble question: what is that recordfail? Where it comes from? You can just drop the reference link.

---

### Post by drs305 on 2010-11-24
> **Elline said:**
> One humble question: what is that recordfail? Where it comes from? You can just drop the reference link.

It won't do any damage.

I haven't yet found the reference or documentation - other than my own experiments with it.  ;-)

I will try to go through the Grub executables and find out what exactly triggers a 'recordfail'. I've tried before when Grub2 first came out but at the time there wasn't much documentation. Maybe there is now. If I find the specifics, I'll post them here. 

In general though, if there is a problem during the actual booting (after a selection is made manually or automatically), it generates a 'recordfail' marker and tells itself to require a manual selection on the next boot. Once the system successfully boots, that marker is removed. So in your case it may not be removed after a successful boot for some reason ("grub-editenv list" will show if the 'recordfail' marker still exists after a successful boot. If it does, that is part of the problem.)

The 'recordfail' is recorded in /boot/grub/grubenv, but you can normally never see it because once you have booted the 'marker' is removed. 

I know one way to generate a 'recordfail' - halt the boot (power off, CTRL-ALT-DEL, etc) after a selection is made but before the system completely boots.

This is probably more than you really wanted (and certainly need) to know about it. The main thing is that changing the 'recordfail' behavior in the way we did it won't harm your system - it just changes it from a full stop at the menu to a timed stop at the menu before it continues.

Update: The 'recordfail' marker is set any time a menuentry with a 'recordfail' line is booted (normally in 10_linux). The value is placed in /boot/grub/grubenv until an /etc/rc2/3/4/5.d grub-common script is run, at which time it is removed. An unsuccessful boot will leave a recordfail which will be seen by Grub during the next event. A successfull boot will have removed the recordfail marker.

---

### Post by Elline on 2010-11-25
Thank for your broad explanation. I hope I don't bother you very much.

"grub-editenv list" gives me "recordfail=1" as assumed.

Yes it's probably more than I need to know but it's curious a bit. I'm really have nothing more to say above. :)

---

### Post by drs305 on 2010-11-25
If you would like to try to do manually what the rc2.d grub-common file is *supposed* to do, a terminal command might give you an error message as to why it isn't working:

```
sudo /etc/rc2.d/S99grub-common start
```
which runs this command:
```
grub-editenv /boot/grub/grubenv unset recordfail
```

---

### Post by Elline on 2010-11-25
I'll try it at my leisure.
Thank for your attention!

---

### Post by chidu.nadig1 on 2010-12-02
@drs305

Thanks lots!! It worked!!

---

### Post by gwi on 2010-12-10
@drs305:

I just noticed your post from 3 weeks ago (for some reason I was not receiving notifications any more).
I tried your options:

[LIST=1]
[*]Default resolution: did not solve the problem. My resolution (1920x1200) is in the list shown by vbeinfo (and was working in 10.04).
[*]Change the timeout in case of a recordfail from -1 to a positive number. That solves the problem, or more exactly: it is a workaround for the problem.
[/LIST]

It is strange that the second option works.
/boot/grub/grubenv only contains a block of # characters.
"grub-editenv list" shows nothing.

With 10.04 everything was OK. So why did the upgrade to 10.10 cause the recordfail problem?

---

### Post by drs305 on 2010-12-10
> **gwi said:**
> With 10.04 everything was OK. So why did the upgrade to 10.10 cause the recordfail problem?

There are a number of things that may cause the problem - scripts not running, etc. If you would like to take the time to find the cause we *might* be able to do it by backing up the boot sequence and seeing what is failing to run. There is more chance of success if you have played with the power management settings or have other things that are failing to start such as ssh.

Of course, you can also just leave it as it is with the recordfail timeout overwritten. 

If you wanted a reminder, we could even make a new entry in /etc/default/grub that exports a recordfail value which you could change in the file normally used for changing G2 settings.

---

### Post by gwi on 2010-12-20
If you can tell me the steps to perform, I am willing to help.

You mentioned power management settings and ssh. I am not using ssh, and have not done anything with power management.

---

### Post by klausb on 2010-12-26
Last hope, to post myself after struggling with grub2 since 3 days. 

I have installed Ubuntu 10.10 on my server (Dual processor AMD 1800+). This machine has 3 hard disks:
- SCSI with OS/2 (I sometimes still use it)
- Ubuntu 8.something running quite stable mainly containing my svn
- Ubuntu 10.10

Each hard disk contains a boot-manager (the SCSI boots first, showing a selection for OS/2 or the 2 GRUBs), the second a GRUB legacy because I cannot get rid of it, the third GRUB 2.

I have exactly the same problems as the others posting here on this thread - the system starts through the "XOSL bootmanager" and then shows GRUB2. And waits for input forever  My /etc/default/grub is quite standard:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5

I tried all the steps described in this thread: 
- reinstalling grub-pc, grub-common, startupmanager
- testing video resolution
- adding the recordfail=0 to grub.cfg
- following steps 1...3 of drs305

My grub doesn't seem to be impressed by all these attempts. It still wants me to press a button, which is quite difficult, because I am usually starting my maching from 600km away.

Are there any other ideas I could still try?

---

### Post by Bobhuber on 2010-12-27
> **klausb said:**
> Last hope, to post myself after struggling with grub2 since 3 days. 

I have installed Ubuntu 10.10 on my server (Dual processor AMD 1800+). This machine has 3 hard disks:
- SCSI with OS/2 (I sometimes still use it)
- Ubuntu 8.something running quite stable mainly containing my svn
- Ubuntu 10.10

Each hard disk contains a boot-manager (the SCSI boots first, showing a selection for OS/2 or the 2 GRUBs), the second a GRUB legacy because I cannot get rid of it, the third GRUB 2.

I have exactly the same problems as the others posting here on this thread - the system starts through the "XOSL bootmanager" and then shows GRUB2. And waits for input forever  My /etc/default/grub is quite standard:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5

I tried all the steps described in this thread: 
- reinstalling grub-pc, grub-common, startupmanager
- testing video resolution
- adding the recordfail=0 to grub.cfg
- following steps 1...3 of drs305

My grub doesn't seem to be impressed by all these attempts. It still wants me to press a button, which is quite difficult, because I am usually starting my maching from 600km away.

Are there any other ideas I could still try?
If you updated the system as I did you will find some extra grub files that contain your answer .They changed some of the grub load sequence,wording etc. Have a look at /etc/default/grub.ucf-dist to see what I am talking about. You will also find different header files for your splash screen entries /etc/grub.d/00_header.dpkg-dist. This drove me crazy until I really looked at the files the system created as a hint during the upgrade. Make sure the /etc/default/grub file matches the format you will find in /etc/default/grub.ucf-dist  (using your screen resolution etc.) and then run update-grub. Hope this helps.

---

### Post by drs305 on 2010-12-27
Grub 1.98 has made some changes, and Grub 1.99 is making more. To see the current options available to /etc/default/grub for your version:
```
strings /usr/sbin/grub-mkconfig | grep "export GRUB" -A 30
```

For instance, in Grub 1.98 and earlier, the /etc/default/grub entry was "GRUB_DISABLE_LINUX_RECOVERY=true", however in G2 1.99 it is currently "GRUB_DISABLE_RECOVERY=true".

---

### Post by gwi on 2010-12-28
> **Bobhuber said:**
> If you updated the system as I did you will find some extra grub files that contain your answer .They changed some of the grub load sequence,wording etc. Have a look at /etc/default/grub.ucf-dist to see what I am talking about. You will also find different header files for your splash screen entries /etc/grub.d/00_header.dpkg-dist. This drove me crazy until I really looked at the files the system created as a hint during the upgrade. Make sure the /etc/default/grub file matches the format you will find in /etc/default/grub.ucf-dist  (using your screen resolution etc.) and then run update-grub. Hope this helps.

Since this is your first post in this thread, I do not know what you mean with "If you updated the system as I did".

In /etc/default I have a file grub and a grub.ucf-old, which are equal (except for a commented line with a setting GRUB_BADRAM). In /boot/grub I only have a grub.cfg, no grub.cfg.old or whatever.

Attached are the contents of /etc/default/grub.

And, to make things clear, my original question: I want to boot my system without having to press Enter, without the Grub menu being shown, just like it did with the previous 9 distributions (if I count correctly starting with Dapper Drake).

---

### Post by drs305 on 2010-12-29
> **gwi said:**
> I want to boot my system without having to press Enter, without the Grub menu being shown, just like it did with the previous 9 distributions (if I count correctly starting with Dapper Drake).

I only notice two things that might be affecting the boot (other than the most complex partitioning I've seen for a single OS ;-) ):

Does your computer support a resolution of 1920x1200 during boot? You can check the supported modes by typing "vbeinfo" at a grub prompt (press 'c').

Also, your RESULTS.txt shows entries for 00_header, which is normal, but also 
> ### BEGIN /etc/grub.d/00_header.lucid ###
which is probably a backup script which is still executable. Remove the executable bit so it isn't run when you update-grub.

The non-auto boot problem is not with your /etc/grub/default settings. I used your file settings and my system counted down and booted normally.

---

### Post by gwi on 2010-12-29
> **drs305 said:**
> Does your computer support a resolution of 1920x1200 during boot? You can check the supported modes by typing "vbeinfo" at a grub prompt (press 'c').

Yes, it does.

> **drs305 said:**
> Also, your RESULTS.txt shows entries for 00_header, which is normal, but also 
### BEGIN /etc/grub.d/00_header.lucid ###
which is probably a backup script which is still executable. Remove the executable bit so it isn't run when you update-grub.

That was it! I removed 00_header.lucid, ran update-grub, and the problem is solved.

Many thanks!

---

### Post by locoHost on 2011-01-06
So for those of us who don't have the 00_header.lucid script (in /etc/grub.d/) to delete and our grub.cfg was never touched and therefore still the default, what is the fix?

Thanks for helping :-)

---

### Post by drs305 on 2011-01-06
> **locoHost said:**
> So for those of us who don't have the 00_header.lucid script (in /etc/grub.d/) to delete and our grub.cfg was never touched and therefore still the default, what is the fix?

Thanks for helping :-)

You can try to override the 'recordfail' as discussed in post # 18. There is a bit more troubleshooting in post # 10.

---

### Post by locoHost on 2011-01-06
Yep Post #18 did the trick!

Thank you!!! \\:D/

---

### Post by James Little on 2011-02-22
I still can't get the timeout working whatever I try. I've fixed the recordfail logic in 00_header, and these are the non-commented lines from my default grub file: 

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

and I've also tried different combinations of these settings with no joy. I'm thinking it must be bios/USB related and I enabled "Legacy USB" devices in there which made no difference. 

I've removed and reinstalled grub2 and still no luck. 

Any ideas? 

Thanks.

---

### Post by drs305 on 2011-02-22
> **James Little said:**
> I still can't get the timeout working whatever I try. 
Any ideas? 


We can determine if it's a recordfail problem if you manually edit /boot/grub/grub.cfg. Find this section and change "-1" to "5".
> if [ "${recordfail}" = 1 ]; then
  set timeout=**[COLOR="DarkRed"]5[/COLOR]**
else
  set timeout=10
fi
Save the file but do NOT run "update-grub".
Also clear "/boot/grub/grubenv" with this command, just in case there is something odd in it:
```
sudo grub-editenv create
```

---

### Post by James Little on 2011-02-22
Already have that section set to timeout=10 regardless of recordfail value: 
```
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi

```

Ran the 'grub-editenv create' command and rebooted, but still no luck.

---

### Post by drs305 on 2011-02-22
> **James Little said:**
> Already have that section set
Ran the 'grub-editenv create' command and rebooted, but still no luck.

If you want to run the boot info script and post the contents of RESULTS.txt perhaps we can see something out of the ordinary. Slim chance perhaps but I'm willing to take a look.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by mw4jet on 2011-03-07
> **gwi said:**
> Yes, it does.
 
 
 
That was it! I removed 00_header.lucid, ran update-grub, and the problem is solved.
 
Many thanks!
 
 
Please anyone tell me how to do this, the /boot/grub/grub.cfg is a read only file, post #32 drs305 said to remove the executable bit from 
 
>  
### BEGIN /etc/grub.d/00_header.lucid ### 
.
 
I can boot into OS after letting the boot fail prompt, "Gave up waiting for root device" I let it sit 30-40 seconds, type exit at [initramfs] prompt and it boots normally, can't deal with that as this pc is going to be a headless server!
 
Any information would be greatly appreciated!!

---

### Post by drs305 on 2011-03-08
> **mw4jet said:**
> Please anyone tell me how to do this, the /boot/grub/grub.cfg is a read only file, post #32 drs305 said to remove the executable bit 

If you have a script you want to disable in the /etc/grub.d folder, you can do it via a file browser opened as root (such as "gksu nautilus /etc/grub.d") or via command line.

Via a file browser, right click on the file, select Properties > Permissions and untick the "Execute" tick box.

In a terminal, you can make the script un-executable with:
```
sudo chmod -x /etc/grub.d/<filename>
```
Example: sudo chmod -x /etc/grub.d/20_memtest86+

To make a file executable, change "-x" to "+x".

---

### Post by mw4jet on 2011-03-08
Thank you so much for your reply drs305, that makes sense, I'm learning, sometimes I get discouraged, as there is so much, but thank you! Will try and post results.
 
Mark

---

### Post by lindomsd on 2011-07-13
all the suggestions are not working

---

### Post by drs305 on 2011-07-13
> **lindomsd said:**
> all the suggestions are not working

If you will post the contents of RESULTS.txt after running the boot info script perhaps we can see the problem. Click on the "BIS" link in my signature line to go to the script site.

---

### Post by ihatewindoze on 2011-07-18
heatpumpcontrol, 

After upgrading from 10.10 to 11.04, I had the same grub problem, i.e., had to hit return on the menu entry for grub to boot instead of it automatically selecting entry 0 after 10 seconds. I followed your advice (removing grub-pc, grub-common, startupmanager and then reinstalling these, using the maintainer's version) and this corrected the problem.

---

### Post by dub4u on 2012-03-14
... deleted ...

---

### Post by Senacharim on 2012-05-17
> **drs305 said:**
> Edit: Solved in post # 32.

@ gwi,

I just noticed this thread with the recent additions. One thing that could cause Grub not to boot is the screen resolution you have set. You can check the available resolutions from the grub prompt (press "c" from the Grub menu) by typing "vbeinfo".  If the resolution isn't supported, Grub will await input.

I don't know if either your original or the new one you tried is supported, but I'd just comment out all resolutions and let Grub use the default (which is 640x480 even when that line is commented out). At least you will find out whether or not it's a resolution problem. 

Note: there have been several posts lately about the counter not working. Most likely a 'recordfail' is being generated for some reason. To see if it's a recordfail issue, you can temporarily edit grub.cfg and force 'recordfail' to be ignored:
```
gksu gedit /boot/grub/grub.cfg
```Add the line in dark red, save the file, do NOT run update-grub and reboot.


The line will be removed once you run "sudo update-grub" the next time.
I did the one step outlined, and now my headless Ubuntu server once again boots without requiring human intervention.

Thank you.

---

### Post by rickyrockrat on 2013-01-02
> **drs305 said:**
> Elline,

I am not sure if you didn't want commands or if you just didn't need the explanations. If you didn't want commands, sorry  - here they come again!  ;-)

For reasons I can't determine, the 'recordfail' check is finding an error. If everything seems to work normally (besides the timeout), we can make the change permanent (so you can also run update-grub). This *bypasses* the problem and lets the system boot after a countdown.

Open two files:
```
gksudo gedit /etc/default/grub /etc/grub.d/00_header
```
In /etc/default/grub, add these 2 lines. Change the '10' to the number of seconds you want to see the menu. My suggestion would be to make it different than "4". "4" is the number of seconds it *should* delay. If you start seeing "4", your problem has gone away. Until then, it will display for whatever time you put as the RECORDFAIL_TIMEOUT.

In /etc/grub.d/00_header, change:


to:


Update grub and you should be done:
```
sudo update-grub
```

Happy Ubuntu-ing !

This happens in Precise, as well.

None of that header modification is necessary. Do not change the exe bits or remove 00-header. Just add:
GRUB_RECORDFAIL_TIMEOUT=10 
to /etc/default/grub
then sudo update-grub

I have despised grub2 since it's inception. grub was so much simpler, but now we have to read scripts to figure out what the heck to do. I used to be able to create my own menu entries in a initramfs shell.

What is happening, for those who care to know, is that some error is occurring, likely at boot (mine is a degraded raid array, i.e. raid1 with 2 out of 4 drives).  If  GRUB_RECORDFAIL_TIMEOUT is not set, it gets set to -1, which means it waits forever for user input. Not that I have any man pages on it.

---

### Post by drs305 on 2013-01-05
rickyrockrat,

Thanks for the input.   :-)

I am not visiting these forums often in my retirement, and I'm also not viewing the updates to GRUB 2 very closely any longer. The additional option for /etc/default/grub is a welcome one.

I'll make a few observations while I'm here for those who stumble upon this thread.

You can view the current options available for input into the /etc/default/grub file by running this command:
```
grep -A50 DEVICE /usr/sbin/grub-mkconfig 
```
You may be able to find an explanation in the GRUB 2 help file:
```
info -f grub -n 'Simple configuration'
``` 

GRUB 2 is constantly being improved. This thread is several years old. When I search for any threads on Ubuntu, I generally use an Advanced option that limits the returns to 6 months or less. This helps me get the most current solutions and help eliminate older entries which may no longer be relevant or optimal.

Happy Ubuntu-ing !

---

### Post by mwhidden on 2013-01-27
Just thought I'd add my own experience, in appreciation for the help this thread gave me: If you follow some (perhaps outdated) advice that you should not mount your /boot partition, you will run into this issue as the rc2.d script that resets the recordfail flag won't work if /boot is not mounted.

---

### Post by adejones on 2013-04-24
> **rickyrockrat said:**
> This happens in Precise, as well.

None of that header modification is necessary. Do not change the exe bits or remove 00-header. Just add:
GRUB_RECORDFAIL_TIMEOUT=10 
to /etc/default/grub
then sudo update-grub

I have despised grub2 since it's inception. grub was so much simpler, but now we have to read scripts to figure out what the heck to do. I used to be able to create my own menu entries in a initramfs shell.

What is happening, for those who care to know, is that some error is occurring, likely at boot (mine is a degraded raid array, i.e. raid1 with 2 out of 4 drives).  If  GRUB_RECORDFAIL_TIMEOUT is not set, it gets set to -1, which means it waits forever for user input. Not that I have any man pages on it.

After an update on Ubuntu Server 12.04, Grub no longer timed out and waited for input before boot.
Adding this to /etc/default/grub fixed my problem 
```
GRUB_RECORDFAIL_TIMEOUT=10
```

Thanks rickyrockrat

---

