---
title: "No Windows 7 Listing in Boot After 12.10 Install"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by arsenic_creed on 2012-10-29
I just installed Ubuntu 12.10 on my new computer alongside my  previous Windows 7 installation. Upon booting for the first time (post  install) my boot menu only lists Ubuntu. 
  I installed using a liveCD, I had to set up my partitions myself  because my Windows wasn't being detected (I set up the new partition out  of free space on the drive.). I know Ubuntu did not overwrite my  Windows because I can mount the Windows drive and access the files from  here.
  I tried running **boot-repair**, as was recommended  for people who didn't have Ubuntu showing up in the menu over on the Ask Ubuntu website, but now I  just have two different Ubuntu options. Still no Windows.
After running boot-repair with advanced options I was knocked back down to one Ubuntu option, still no Windows.
Following instructions on another thread where someone had the same problem I updated grub through the terminal. It ran fine and now I have two options, Ubuntu and Windows Boot Manager, both of which take me into Ubuntu. 
I've tried putting in my Windows disk to boot off of so I could put in something like EasyBCD but my (factory) Windows disk just freezes on the language selection menu and I can't do anything.
If all that wasn't bad enough, every time I try to run my software updater now it says to check my internet (which I know is working because I was on the internet at the time).
I'm beginning to think it'd be easy to start putting my stuff on externals and disks and such and just redoing the whole thing. It's a new computer so it's not customized all that much yet but I wanted to check here as well before I do anything really drastic.

  (If you require any additional data [logs, etc.], could you tell me how to find it, I am a bit new to this.)
  Any help is greatly appreciated.
(P.s. If you think I should just redo the whole thing, how would I go about that? I can't take Ubuntu off while on it, can I? But I can't install my Windows just overtop of it because the disk isn't working right now... :()
(P.p.s. Because I just noticed that it's in the thread prefix but I can't pick two prefixes, my computer is running 64 bit version of both [or not running, as the case may be] operating systems.)

---

### Post by oldfred on 2012-10-29
Boot-Repair can run a BootInfo report so we can see the details of your install.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by darkod on 2012-10-29
Probably you have a different issue, but take a look here for a guidance:
[http://ubuntuforums.org/showthread.php?t=2077278](http://ubuntuforums.org/showthread.php?t=2077278)

Note, from ubuntu you can find the win7 partition that has the boot flag, and then try the manual commands from the grub command prompt. That way you can see if win7 boots correctly or not.

In any case, posting the link that the boot-repair makes is recommended. You don't even need to run anything yourself, just run boot-repair and create the bootinfo.

---

### Post by arsenic_creed on 2012-10-29
Okay, this should be the link to the boot info you asked for. For the linked thread, did you mean to follow the 'chainloader' thing that is says about?
[http://paste.ubuntu.com/1316419/](http://paste.ubuntu.com/1316419/)

---

### Post by darkod on 2012-10-29
You are using UEFI boot, so the thread I linked doesn't apply to your case. I have no experience with uefi, maybe oldfred will have some idea.

In general, boot entires for uefi are done from within the bios, there should be something like uefi boot manager or what ever it's called. UEFI boots differently from the old style bios boot. Your computer or motherboard manual might have instructions how to add boot entries for UEFI.

---

### Post by oldfred on 2012-10-29
In Boot-Repair did you check off the UEFI options.

Grub2's os-prober has been adding a Windows BIOS/MBR type entry not a UEFI type entry to chainload Windows. But Yann updated Boot-Repair to add the correct type of chainload entry.

---

### Post by YannBuntu on 2012-10-30
Hello

> **arsenic_creed said:**
> Okay, this should be the link to the boot info you asked for. For the linked thread, did you mean to follow the 'chainloader' thing that is says about?
[http://paste.ubuntu.com/1316419/](http://paste.ubuntu.com/1316419/)

This case is rare. You have no original /EFI/Microsoft/Boot/bootmgfw.efi . (presence of /EFI/Microsoft/Boot/bootmgfw.efi.grb indicates that B-R created a dummy /EFI/Microsoft/Boot/bootmgfw.efi ).
I will update B-R for this case. Meanwhile, you can do this:

Please :
1) boot an Ubuntu CD, choose "Try Ubuntu"
2) open a terminal and type the following commands one by one:
```
sudo mount /dev/sda1 /mnt
```

Press Enter

```
sudo rm /mnt/EFI/Microsoft/Boot/bootmgfw.efi*
```

Press Enter

```
sudo cp /mnt/EFI/Boot/bootx64.efi.bkp /mnt/EFI/Microsoft/Boot/bootmgfw.efi
```

Press Enter

3) run Boot-Repair --> Recommended Repair , indicate us the new URL that will appear
4) then reboot the pc without CD, and tell us what you observe

---

### Post by arsenic_creed on 2012-10-30
Okay, I ran those commands and here is the new boot repair link thing (what are these called?) . I'll update with observations in a minute after I restart. (Just wanted to make sure I didn't loose the link!)
[http://paste.ubuntu.com/1319339/](http://paste.ubuntu.com/1319339/)

---

### Post by arsenic_creed on 2012-10-30
I haven't booted into Ubuntu yet but it list both the Ubuntu option and a Windows Boot Manager option now that boots into my Windows correctly. 
Thank you!

(Actually, as for the update problem I mentioned in the original post, it only seems to have the problem if I try to open the software updater myself. It came up with updates today on it's own and installed them without problems. I still miss 12.04's update manager though.)

---

### Post by YannBuntu on 2012-10-30
Good job :)

For my information, please could you attach your /boot/grub/grub.cfg file ?
( in order to fix this bug: [https://sourceforge.net/apps/trac/bootinfoscript/ticket/15](https://sourceforge.net/apps/trac/bootinfoscript/ticket/15) )

---

### Post by arsenic_creed on 2012-11-01
You might notice that I marked this as unsolved again. While the previous solution worked and lets me boot into my Windows, it doesn't stay like that. As soon as I shut down or restart from Windows the GRUB window goes back to the way it was before and the Windows option is gone again (if you still want that .cfg file, I can get it but I wasn't sure if you would since this is still causing problems.
Do you think getting it into Windows and using something like EasyBCD might work?

(If you reply today, my own replies might be weirdly spaced and I apologize if anything doesn't make sense, I'm home sick so I'm really not feeling great.)

---

### Post by oldfred on 2012-11-01
It was my understanding that EasyBCD did not work with UEFI. And with UEFI I really do not see any reason for it. 

You just should have two UEFI entries that you can boot or from the grub entry be able to chain load back to the Windows efi entry.

If booting directly from UEFI menu do both work or not. Or is it the grub menu entry that does not work?

---

### Post by arsenic_creed on 2012-11-01
I wasn't sure it it would, just thought I'd as as someone over on Ask Ubuntu had asked about using it before Yannubuntu replied here but I couldn't get into Windows to even try it.
I'm not exactly sure what you're asking, sorry. 
Basically what happens is when I start my computer it shows the alienware loading logo then goes to the GRUB boot menu. The menu has an Ubuntu entry and a 'Windows EFI Memory Test' option (that one is new and possibly says something slightly different than that). The only Windows option just gives me an error (can't remember what it says now but I can restart and write it down if you like) thought the Ubuntu one works just as it's supposed to.
Immediately after using Yannubuntu's suggestion (exactly), I get a GRUB menu with Ubuntu and Windows Boot Manager. Ubuntu still works and the Windows one take me into Windows but the menus change back as soon as I restart/shut down again.
Hope that made sense.

---

### Post by oldfred on 2012-11-01
Grub2's os-prober writes an incorrect Windows chain boot entry or one that is really for BIOS based systems that does not work with UEFI systems. 

Yann's Boot-Repair will add correct entries which are the one's you have to use. 

As Yann asked post your grub.cfg.

---

### Post by arsenic_creed on 2012-11-01
I found the file you were asking for but when I try to attach it it says that its an invalid file?
(On a [slightly] random note, thank you all for taking so much time to help me sort this out. I really appreciate it.)

---

### Post by oldfred on 2012-11-01
It should let you copy & paste the file. Then highlight again and click on code tags to preserve formatting and make it easier to scroll thru.

Alternatively post a link to a new BootInfo report.

---

### Post by Mc P on 2012-11-01
Just want to report, Im suffering from the same fate. I can boot into Windows and Ubuntu, by going through the BIOS, but Grub only offers ubuntu.

I may leave this unresolved for now. If theres any thing specific you want to look at let me know.

Thanks

---

### Post by oldfred on 2012-11-01
@Mc P
If you want some help, start a new thread and post your link to BootInfo report from Boot-Repair. See post #2 for link.

---

### Post by arsenic_creed on 2012-11-01
Oh! I was trying to upload it, not copy-paste the contents (that might be why I was having trouble).
Lets try this again, shall we?
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
set default="Windows UEFI memory test"

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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  583df04c-5052-4225-9b95-66502a6f197a
else
  search --no-floppy --fs-uuid --set=root 583df04c-5052-4225-9b95-66502a6f197a
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-583df04c-5052-4225-9b95-66502a6f197a' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  583df04c-5052-4225-9b95-66502a6f197a
    else
      search --no-floppy --fs-uuid --set=root 583df04c-5052-4225-9b95-66502a6f197a
    fi
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=583df04c-5052-4225-9b95-66502a6f197a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-583df04c-5052-4225-9b95-66502a6f197a' {
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-583df04c-5052-4225-9b95-66502a6f197a' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  583df04c-5052-4225-9b95-66502a6f197a
        else
          search --no-floppy --fs-uuid --set=root 583df04c-5052-4225-9b95-66502a6f197a
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=583df04c-5052-4225-9b95-66502a6f197a ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-583df04c-5052-4225-9b95-66502a6f197a' {
    recordfail
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  583df04c-5052-4225-9b95-66502a6f197a
        else
          search --no-floppy --fs-uuid --set=root 583df04c-5052-4225-9b95-66502a6f197a
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=583df04c-5052-4225-9b95-66502a6f197a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI memory test" {
search --fs-uuid --no-floppy --set=root 6CC8-E1E7
chainloader (${root})/EFI/Microsoft/Boot/memtest.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
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

### Post by oldfred on 2012-11-01
I see a UEFI memory test but not the typical Windows chain entry? Maybe Yann knows.

If you want you can manually add the boot entry. These both should work, one loads more grub modules, but most are loaded by default.

#Add menu entry to 40_custom, change example from sda13 to your partition.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub
sudo dpkg-reconfigure grub-pc


Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)

Copy & paste these into 40_custom

gksudo gedit /etc/grub.d/40_custom

# after updating 40_cusotm to update grub menu
sudo update-grub


```
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt2)'
  search --fs-uuid --no-floppy --set=root 4f84-ee2e
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```

---

### Post by arsenic_creed on 2012-11-04
Okay, I did that and now I have a working Windows entry, thank you.
I also have another identical entry that doesn't work and a Windows UEFI Memory Test entry that gives an error, is there a way to get rid of those?

[Edit to Add Quick Note: I figured out why my updates weren't working. There were a couple invalid sources in there and I've unchecked them in Software Sources and it's working now.]

---

