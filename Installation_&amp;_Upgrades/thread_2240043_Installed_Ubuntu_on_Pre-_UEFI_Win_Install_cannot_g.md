---
title: "Installed Ubuntu on Pre- UEFI Win Install cannot get Win to boot"
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by robert71 on 2014-08-17
Hello All, 

          I have installed Ubuntu 14 on a pre-installed windows system with UEFI and disabled secure boot. I then used boot repair but cannot get windows to start can anyone help me please ?? 

thanks, 

ROb.

---

### Post by oldfred on 2014-08-17
What hardware, vendor, model, video card?

Does Ubuntu start ok?

Post link that Boot-Repair gives when you run the BootInfo Summary report.

---

### Post by robert71 on 2014-08-17
Hi Fred,

First its an acer aspire s7-392-9890 

Also here is the link from boot repair:

[http://paste.ubuntu.com/8072399/](http://paste.ubuntu.com/8072399/)

I tried rEFInd and the windows partition itself  is okay i just dont know how to make the grub 2 boot loader point ot windows as well.

So right now i can only boot ubuntu as that is the only option that comes up under grub 2.

---

### Post by grahammechanical on 2014-08-17
You did not allow boot repair to carry out the repair. That may be wise. Please run this command and report what is printed to the screen

```
sudo update-grub
```

Oh, by the way, you are limiting yourself to providing only the minimum of information. How many hard disks do you have? How many partitions? Where is windows installed. Where did you install Ubuntu? What version of windows do you have.

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If Windows is installed in EFI mode, then Ubuntu must be installed in EFI mode. To install Ubuntu in legacy mode when windows is installed in EFI mode is a certain way of getting the situation that you are experiencing.

Regards.

---

### Post by ajgreeny on 2014-08-17
I have never seen such an output with all those /dev/mapper partitions listed, and I wonder if you have either a raid setup, or encryption, or used LVM for managing partitions, none of which I use, nor understand how to use.

I do note, however, that you have no detected boot/grub/grub.cfg file which is needed for grub to work; perhaps that is because grub did not understand your partition setup any better than I did, though it is probably because sda could not be read according to the line > Error: Invalid argument during seek for read on /dev/sda that appears twice in your boot-info output file at lines 381 and 482

Regrettably, I have no idea how to help you more with this, but I suspect oldfred will be able to come up with more detailed assistance than I can.

---

### Post by oldfred on 2014-08-17
I do not know RAID, and am surprised you have Ubuntu/grub working. 

It used to be that the standard desktop installer did not support RAID at all, you had to use the alternative installer in 12.04 for RAID or LVM. They discontinued alternative installer and said eventually LVM & RAID may be in Desktop installer. I believe 14.04 now has LVM, but did not think it fully supported RAID, yet. Usually issues were not seeing partitions at all, then later not installing grub correctly for RAID boot.

I think I told this user that he had Intel SRT which is seen as a small SSD for faster booting. He then followed directions to temporary break the SRT (RAID), but since these systems are full RAID drives, he may never recovered the RAID? Or review this but do not follow it.
       Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)

If you have RAID driver installed, have you run sudo update-grub? 

Script did not open the /mapper and post the grub.cfg. Can you post both the grub.cfg in /efi/ubuntu, may be mounted at /boot/efi/EFI/ubuntu. That should be just three lines referring with configfile entry to the grub.cfg in your install. And then post the entire grub.cfg from your install.

I do not know if dmraid or mdadm is correct RAID driver. And there was some discussion of merging the dmraid driver into mdadm. And then there are many hardware RAID drivers each requiring its own install.

Is your RAID like this?
      
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

These are typical UEFI boot entries for Windows. 
But you have to use this UUID or path and probably add insmod entries for the RAID:

> /dev/mapper/isw_cgfdciieie_HDD0p2 [COLOR=#ff0000]64CD-1E74[/COLOR]                              vfat       ESP

I see a dm_nv.mod, several mdraid and several raid .mod files.
You may alread have a RAID entry in your other grub boot stanza. But it may be this?
insmod dm_nv

 Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)
menuentry "Windows 8 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt2)'
  search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]4f84-ee2e[/COLOR]
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

I think these assumes all the insmod or added grub driver entries are already loaded.
   menuentry "Windows bootmgfw.efi UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

   menuentry "Windows bootmgfw.efi " {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]18FE-69D8[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

---

### Post by robert71 on 2014-08-17
sorry for not giving enough info: 

here is the output from **sudo update-grub**: 

[sudo] password for tom: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found Ubuntu 14.04.1 LTS (14.04) on /dev/mapper/isw_cgfdciieie_HDD0p7
Adding boot menu entry for EFI firmware configuration

(Still doesnt show up) 

Other info:

I have two disks configured as RAID 0 and Using windows 8.1 pre-installed UEFI. 

Here is a screenshot of the disk manager in ubuntu (see attachment). 

[ATTACH=CONFIG]255558[/ATTACH]

And to answer [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747") the  /dev/mapper partitions i believe is a result of either Ubuntu reading the raid configuration badly or the many runs of the boot repair. 

Thanks for the help!!!

---

### Post by oldfred on 2014-08-17
Some want RAID 0 for extreme speed, but that was more popular with hard drives. Usually SSD gives enough speed anyway.

Be sure to have really good backups.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by robert71 on 2014-08-17
Hello [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"), 

Thank you very much for your reply, is it possible to break that down a little. i am not sure i understand what you mean by 

[COLOR=#0000ff]"Can you post both the grub.cfg in /efi/ubuntu, may be mounted at  /boot/efi/EFI/ubuntu. That should be just three lines referring with  configfile entry to the grub.cfg in your install. And then post the  entire grub.cfg from your install."[/COLOR] 

this is the output from here is the output from **sudo update-grub**: 

[sudo] password for tom: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found Ubuntu 14.04.1 LTS (14.04) on /dev/mapper/isw_cgfdciieie_HDD0p7
Adding boot menu entry for EFI firmware configuration

I rebooted but im still not seeing the windows entry in the menu. 


My Raid is not like 
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
I have a RAID 0 Striped with two 128 GB drives. Thats the factory config. 

I dont understand the rest of your post referring to the [COLOR=#ff0000]chainload entries[/COLOR] can you break that down a little more please. 

Thanks much.

---

### Post by robert71 on 2014-08-17
> **oldfred said:**
> Some want RAID 0 for extreme speed, but that was more popular with hard drives. Usually SSD gives enough speed anyway.

Be sure to have really good backups.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

Yeah that was just the factory config not my doing. I dont really care what setup the HD's use as long as i can get the dual boot working, i need windows as well as ubuntu for my school. But thanks for the info.

---

### Post by robert71 on 2014-08-17
Ok i figured you mean you wanted to see the grub file so here is the contents of the /boot/efi/EFI/ubuntu

"search.fs_uuid a8229ce3-81f9-4221-abfa-a8a42c7903d8 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg"

Thats it.

---

### Post by oldfred on 2014-08-17
I expected that grub.cfg to be similar to other UEFI configfile entries and it is. The UUID is the UUID of your ext4 partition inside the RAID. Just wanted to confirm it did not use something special for RAID.

What is full grub.cfg in your /boot/grub folder?
cat /boot/grub/grub.cfg

Or but do not make any changes. It will be longer, so post in code tags. Use  # icon in Advanced editor's top edit panel when posting.
gksudo gedit /boot/grub/grub.cfg

---

### Post by robert71 on 2014-08-17
The full grub.cfg is 

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
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
else
  search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
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
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
    else
      search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
    fi
    linux    /boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-34-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
    menuentry 'Ubuntu, with Linux 3.13.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-advanced-a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
        else
          search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
        fi
        echo    'Loading Linux 3.13.0-34-generic ...'
        linux    /boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-recovery-a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
        else
          search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
        fi
        echo    'Loading Linux 3.13.0-34-generic ...'
        linux    /boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
        else
          search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
        else
          search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 14.04.1 LTS (14.04) (on /dev/mapper/isw_cgfdciieie_HDD0p7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
    insmod part_gpt
    insmod ext2
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
    else
      search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
    fi
    linux /boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-34-generic
}
submenu 'Advanced options for Ubuntu 14.04.1 LTS (14.04) (on /dev/mapper/isw_cgfdciieie_HDD0p7)' $menuentry_id_option 'osprober-gnulinux-advanced-a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
    menuentry 'Ubuntu (on /dev/mapper/isw_cgfdciieie_HDD0p7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-34-generic.efi.signed--a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
        else
          search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
        fi
        linux /boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-34-generic (on /dev/mapper/isw_cgfdciieie_HDD0p7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-34-generic.efi.signed--a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
        else
          search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
        fi
        linux /boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-34-generic (recovery mode) (on /dev/mapper/isw_cgfdciieie_HDD0p7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-34-generic.efi.signed-root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro recovery nomodeset-a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
        else
          search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
        fi
        linux /boot/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (on /dev/mapper/isw_cgfdciieie_HDD0p7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-32-generic--a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
        else
          search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
        fi
        linux /boot/vmlinuz-3.13.0-32-generic root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode) (on /dev/mapper/isw_cgfdciieie_HDD0p7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-32-generic-root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro recovery nomodeset-a8229ce3-81f9-4221-abfa-a8a42c7903d8' {
        insmod part_gpt
        insmod ext2
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root  a8229ce3-81f9-4221-abfa-a8a42c7903d8
        else
          search --no-floppy --fs-uuid --set=root a8229ce3-81f9-4221-abfa-a8a42c7903d8
        fi
        linux /boot/vmlinuz-3.13.0-32-generic root=UUID=a8229ce3-81f9-4221-abfa-a8a42c7903d8 ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-32-generic
    }
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

### Post by oldfred on 2014-08-17
It is consistently using UUID, with no reference to device like /mapper/....
Changed example entry I posted above to include your efi partition's UUID.

 gksudo gedit /etc/grub.d/40_custom
sudo update-grub

menuentry "Windows bootmgfw.efi " {
search --fs-uuid --no-floppy --set=root [COLOR=#000000]64CD-1E74[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

But still am wondering why os-prober is not adding that type of entry automatically?

---

### Post by robert71 on 2014-08-17
Here is the file with the entry added and the terminal after the sudo grubupdate

[ATTACH=CONFIG]255562[/ATTACH][ATTACH=CONFIG]255563[/ATTACH]

Is it correctly edited?

---

### Post by robert71 on 2014-08-17
OMG IT WORKED !!!


THANK YOUUU SOOOO MUCH 

Is it possible to explain to me what caused that problem ??
And what we did to fix it ? 

Thanks .

---

### Post by oldfred on 2014-08-17
Something in os-prober is not working with RAID. Not sure what it is, or if it is just you or a bug that should be reported.

We just manually added the entry that os-prober should have created. Early UEFI versions did not have a working os-prober and we had to add entries like we just did all the time. 

Since you have the entry and it should never change, you should not have to do anything. 
I would expect at some update it may get fixed and then os-prober would add another similar entry, but that may be a version or two away.

Backup efi partition and 40_custom file in grub just to have that included in your normal backups.

---

### Post by robert71 on 2014-08-17
How can i tell what is the EFI Partition and how to back it up ? 

Thanks

---

### Post by oldfred on 2014-08-17
I am not sure with RAID how it is mounted.

 /dev/mapper/isw_cgfdciieie_HDD02        821,248     1,435,647       614,400 EFI System partition

It should already be mounted and you can see it here.

cat /etc/fstab

I like to use rsync and copy files periodically to another drive. And most important data I burn to a couple of DVDs about every quarter.

      
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I started with a real simple rsync file like this:
      
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
Discussion of issues on rsycn bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)

      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

I do not backup Ubuntu system as that is easy to reinstall. But want settings & my data well backed up.
But Windows makes it difficult to reinstall. A good image backup and then updates probably is better for Windwos.
      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by robert71 on 2014-08-17
Okay, i will.

Thanks very much for your help OlDFred. And everybody else as well.

---

