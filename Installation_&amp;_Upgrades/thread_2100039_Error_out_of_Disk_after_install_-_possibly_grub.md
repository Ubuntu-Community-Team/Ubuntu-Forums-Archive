---
title: "Error out of Disk after install - possibly grub?"
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by Wednesday on 2012-12-31
Hi Ginger Graham, I have just installed Ubuntu 12.04 onto a Compact Flash Card and have a 500MB /boot partition follwed by a 3.1MB unmounted partition, followed by a 20GB / pertition and a 11 GB /home partition. I get a very similar message. The only difference is that  after the screen:
error: out of disk
error: no suitable mode found
error: no video mode activated 

I then get what may be the same message in funny unreadable characters and then a normal start.

Did you find the source of the problem?

---

### Post by oldfred on 2012-12-31
You were in this unsolved old thread, better to have your own.
[http://ubuntuforums.org/showthread.php?t=1963660](http://ubuntuforums.org/showthread.php?t=1963660)

Out of disk is often a grub error, and a total reinstall of grub may fix it. The other errors may be related to the grub video mode and a display of the grub menu. But then grub still started the boot and Ubuntu loads??

If you can boot, you can run this from you install, or  an Ubuntu  live CD/DVD/Flash or download a full repair ISO.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Wednesday on 2013-01-02
Yes - after I get the error messages the UBUNTU system comes up. 
I installed the boot-repair as identified in the link.
HOWEVER, I was given the option to install dmraid and I said yes - bu then was given the futher option of removing MDraid as this may conflict with dmraid. I decided this was a bad idea and declined to remove MDraid as I beleive this may be cricial to my raid. I hope this was the right thing to do.
I have boot disk sdc (CF card) and a pair of WD drives for data (and a swap partition). The WD drives are mirored.
When I ran boot-info I had a pendrive in the USB port which was orginally used to install UBUNTU. This is not in my USB when I boot. Please ignore this.
boot-repair seemd to create two directory structures: /mnt/Bootinfo andf /mnt/boot-sav
The output of boot-repair is:
[http://paste.ubuntu.com/1487517/](http://paste.ubuntu.com/1487517/)
I hope you can help. Thanks in advance

---

### Post by oldfred on 2013-01-02
I do not know RAID and there seem to be a lot of versions, fake-RAID or BIOS based, hardware RAID & software RAID, so I have not tried to keep track.

But you are just booting from your CF disk and that is separate. I do not see anything wrong. and most that have an out of disk error do not boot?

Grub does scan system when booting, so perhaps it cannot see RAID so that is the error? And then since it did not really matter then it worked?

Grub has a lot of add-in drivers which it needs for various things. If installing in RAID I think grub adds a raid.mod or one of the other raid add ins if in RAID.

Is error before or after grub menu. If after use e and add to boot stanza this.
insmod raid
Or perhaps one of the other raid drivers listed in /boot/grub with .mod extension.

If before menu  we need to add the insmod raid to grub.cfg to test. Of course we are never supposed to edit grub.cfg but for a test that should be ok. It will not be saved beyond the next sudo update-grub.

       gksu gedit /boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /boot/grub/grub.cfg

Add to same area near top where other insmod files are like insmod ext2.

---

### Post by Wednesday on 2013-01-02
Thanks for the reply. 
I am a bit confused. But maybe I can clarify:
The error: out of disk etc started to occur as soon as the Ubuntu system was installed onto the CF disk (without raid). Once installed and with the error there I ignored the error and  ploughed on despite this to set up the software raid on the two WD disks for data (and also swap). So I do not think the error out of disk) is related to the raid.
The grub should not have been installed in the raid.

I do not get the grub menu normally - only after hitting the shift key. Then the sequence I see it "GRUB loading" then:
"error: out of disk
error: no suitable mode found
error: no video mode activated"
This is immediately replaced by the GRUB menu. Once seeing the grub menu I can select any of the system options and it continues to boot normally. 

I hope this helps. 
I am not sure I understand why adding "insmod raid" will make a difference - but I am happy to try. I do see that I only have insmod ext2 in more than one place in grub.cfg. Can you let me know where to put it? 

below is my boot.cfg
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
set root='(hd2,msdos3)'
search --no-floppy --fs-uuid --set=root 23961a52-c4de-4091-bc84-95a1c649eefb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos1)'
  search --no-floppy --fs-uuid --set=root acdeb001-d06a-4774-a362-1399fd458286
  set locale_dir=($root)/grub/locale
  set lang=en_GB
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
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root acdeb001-d06a-4774-a362-1399fd458286
    linux    /vmlinuz-3.2.0-35-generic-pae root=UUID=23961a52-c4de-4091-bc84-95a1c649eefb ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-35-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root acdeb001-d06a-4774-a362-1399fd458286
    echo    'Loading Linux 3.2.0-35-generic-pae ...'
    linux    /vmlinuz-3.2.0-35-generic-pae root=UUID=23961a52-c4de-4091-bc84-95a1c649eefb ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-35-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root acdeb001-d06a-4774-a362-1399fd458286
    linux    /vmlinuz-3.2.0-29-generic-pae root=UUID=23961a52-c4de-4091-bc84-95a1c649eefb ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root acdeb001-d06a-4774-a362-1399fd458286
    echo    'Loading Linux 3.2.0-29-generic-pae ...'
    linux    /vmlinuz-3.2.0-29-generic-pae root=UUID=23961a52-c4de-4091-bc84-95a1c649eefb ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-29-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root acdeb001-d06a-4774-a362-1399fd458286
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root acdeb001-d06a-4774-a362-1399fd458286
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

---

### Post by oldfred on 2013-01-02
Added code tags. Hightlight and click on # in edit panel to auto add them.

I think the issue still may be that grub scans drives when loading. Not sure if it really should or not. But if it cannot scan RAID drives then it gives the error message. But RAID drive is not required for booting so it does not really matter that it cannot scan it anyway.

---

### Post by Wednesday on 2013-01-03
Thanks for showing me how to show the file as code.

Can you show me where to put the insmod raid?

Thanks.

---

### Post by oldfred on 2013-01-03
You have these lines part way down.

> insmod part_msdos
insmod ext2


So either before or after should work, if it does work that is.

---

### Post by Wednesday on 2013-01-06
Thanks for the last reply. I have inserted insmod raid in all the locations where I find insmod ext2 but this has no effect.
I suspect that this must be an issue with the current software not being compatible with my hardware system. I will search for similar reports.

---

