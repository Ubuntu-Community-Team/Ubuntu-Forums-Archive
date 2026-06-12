---
title: "Several crashes &amp; no boot (Ubuntu 10 &amp; 11)"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by Pieter VW on 2011-05-23
Hello everyone, quite new here but with a lot of issues ...

A few years back I set up a dualboot system with Vista and Ubuntu 8. Computer has been that way for a long time and I didn't have an internet connection for about a year. A few days back, system asks if I want to update from Ubuntu 8 to 10, I click yes, run the installer and after installing, the system shuts down but doesn't start up again (grub does load but system crashes before the startup screen for every Ubuntu version listed). 

Easy solution: Picked up a Ubuntu 11.04 live cd and started the install. Wrote the boot sector to "/dva" and formatted the old Ubuntu partition and gave it extension "/". System installs, reboots and ... nothing. If I hold shift, I just get a massive list of "GRUB GRUB GRUB GRUB GRUB" and no other options. Did some googling, seems it helps to turn hd autodetect off in the bios, unfortunately I don't have that option (HP system). 

All a bit vague and no clear info as I haven't been able to gather all data and needed to find a computer that could access the internet. So any wild ideas or data requests?

Just need to get grub to load again, because now my computer can't be used for anything.

Thanks!

---

### Post by AgentZ86 on 2011-05-23
The newer versions have Grub 2 so I forgot how to fix this for upgrades it's been a while

But for new installs I would not turn off the autodetect hd 
I have never heard any problems with having it on that I know of

And from the Grub,grub,grub sound like it didn't install and I'm not sure what /dva is ? 

You mean /hda ?
And did you format to ext4, and what OS are you installing 11.04 32 or 64bit and to what type of machine a 32 or 64bit

You can't install the 64bit OS to a 32bit machine just FYI incase you are not aware.

---

### Post by Pieter VW on 2011-05-23
Sorry, meant "sda" io "dva". 

Installed a 32 bit version on a 32 bit machine, file system used is btrfs.

---

### Post by Pieter VW on 2011-05-24
Ok ... Am now running on the live cd so here's some more info. I've tried to retrieve the boot info script, but the terminal window told me "no such file or directory".

Grub was installed on sda, the / directory on sda3, other partitions belong to Windows. Did some googling and came up with the following: [http://www.mail-archive.com/plug-discuss@lists.plug.phoenix.az.us/msg05618.html](http://www.mail-archive.com/plug-discuss@lists.plug.phoenix.az.us/msg05618.html)

Seems to be a BIOS error ... I have a HP computer running BIOS version 5.23 which doesn't allow me to autoselect HD's. I've checked and they are already sitting in the correct order to boot. Any ideas?

GRUB.CFG:

> ### BEGIN /etc/grub.d/00_header ###
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
insmod btrfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 3f29bc03-14e7-406c-9c51-e940748b2e67
if loadfont /@/usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod btrfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 3f29bc03-14e7-406c-9c51-e940748b2e67
set locale_dir=($root)/@/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod btrfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 3f29bc03-14e7-406c-9c51-e940748b2e67
    linux    /@/boot/vmlinuz-2.6.38-8-generic root=UUID=3f29bc03-14e7-406c-9c51-e940748b2e67 ro rootflags=subvol=@   quiet splash vt.handoff=7
    initrd    /@/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod btrfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 3f29bc03-14e7-406c-9c51-e940748b2e67
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /@/boot/vmlinuz-2.6.38-8-generic root=UUID=3f29bc03-14e7-406c-9c51-e940748b2e67 ro single rootflags=subvol=@ 
    echo    'Loading initial ramdisk ...'
    initrd    /@/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod btrfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 3f29bc03-14e7-406c-9c51-e940748b2e67
    linux16    /@/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod btrfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 3f29bc03-14e7-406c-9c51-e940748b2e67
    linux16    /@/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 484A8A404A8A2AB0
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2C88743C8874071C
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

---

### Post by Pieter VW on 2011-05-25
FWIW - Solved the issue.

I did yet another fresh install but since the computer always froze at restart, I decided not to reboot after installation but just "continued trying on the live cd" and shut the system down completely. Left it off for a minute or so, started the computer ... and everything worked! Not sure why, but it does.

---

