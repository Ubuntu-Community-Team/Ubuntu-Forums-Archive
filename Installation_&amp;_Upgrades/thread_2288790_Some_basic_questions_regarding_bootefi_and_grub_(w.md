---
title: "Some basic questions regarding boot/efi and grub (windows, ubuntu and lenovo)"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by hearts2 on 2015-07-29
Hi all,

I use a Lenovo laptop, and duel installed Windows 8.1 & Ubuntu. Everything works fine.

My questions are as follows, I just need some brief answers to grasp the concept, in case it's too troublesome to answer them in details.

1) My /boot/efi structure:

/boot/efi/BOOT/boot.sdi                  <-- what is this for?
/boot/efi/EFI/Boot/bkpbootx64.efi    <-- what is this for?
/boot/efi/EFI/Boot/LenovoBT.efi      <-- what is this for?

/boot/efi/EFI/Boot/bootx64.efi

<-- After some comparison, I found that this one is the same as /boot/efi/EFI/ubuntu/shinmx64.efi, this file should run by default? So how does this file invokes /boot/efi/EFI/ubuntu/grub.cfg, which in turn invokes /boot/grub/grub.cfg?

/boot/efi/EFI/Lenovo/Boot/memtest.efi    bootmgfw.efi  bootmgr.efi       <-- what are these for?

/boot/efi/EFI/Microsoft/Boot/memtest.efi    bootmgfw.efi  bootmgr.efi       <-- what are these for?

/boot/efi/EFI/ubuntu/Boot/grub.cfg grubx64.efi MokManager.efi shimx64.efi  <-- I know the basic difference between grubx64.efi and shimx64.efi, just don't know too much about MokManager.efi


2) /boot/efi/EFI/ubuntu/Boot/grub.cfg 

search.fs_uuid 4ee4f119-b0da-4f43-b3ae-814d7b54a257 root hd0,gpt7

May I assume that gpt7 is the same as /dev/sda7, and gtpn is the same as /dev/sdan?

3) /boot/grub/grub.cfg

The top 2 are linux entries and not fancy to me

I can see all these following options on grub menu (very messy one isn't it?), but I dare not to select any of them because I don't know what they do (will they reinstall /recover the whole disk ?)

menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root D206-F1B4
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root D206-F1B4
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root D206-F1B4
chainloader (${root})/EFI/ubuntu/MokManager.efi
}

menuentry "EFI/Lenovo/Boot/bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root D206-F1B4
chainloader (${root})/EFI/Lenovo/Boot/bootmgfw.efi
}

The following is good, I know it will boot into Windows, I am not sure how to make it boot to windows by default (the grub.conf says do not modify it directly...)

menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-D206-F1B4' {
        insmod part_gpt
        insmod fat
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  D206-F1B4
        else
          search --no-floppy --fs-uuid --set=root D206-F1B4
        fi
        chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10at
fi


And the last one, what is it?

menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
        fwsetup
}


4) And lastly, since I just upgraded Windows 8.1 to Windows 10 which will activate the reinstallation of Windows by motherboard, it seems that there's no need to leave Lenovo recovery partition (14.4GB) and Lenovo OEM partition (7GB). I would like to delete them using gparted. I will then resize the linux partition and the swap partition to make them larger. See the picture.

I am not sure whether this will affect the current boot. And I need to knowledge myself on the above basic questions so that I can fix any problems if there will be.

Thanks.


[ATTACH=CONFIG]263481[/ATTACH]

---

### Post by oldfred on 2015-07-29
Some users have specific issues with new Windows 10. I would want a full backup of Windows so I could restore it if the issue happens to be something that is essential to me.

I do not know details of each vendor's efi files.
The bootx64.efi is the drive boot entry. That same file name is always used by external drives to boot in UEFI mode.  Some systems call it fallback or have a specific fallback.efi file also.
Some systems also will not boot the /EFI/ubuntu files like shimx64.efi or grubx64.efi. So sometimes they are copied into /EFI/Boot and renamed to bootx64.efi to enable booting. 

bkpbootx64.efi is normally created by running Boot-Repair. It backs up certain essential files just in case. I normally suggest a full backup of the efi partition. It is not large and then you have all the files needed to boot.

Grub uses a slightly different convention than Ubuntu. Boot drive is always hd0. partitions now are numbered the same as Ubuntu/Linux but since partitioning can be msdos(MBR) or gpt(GUID) then it also may show which type of partition. Or (hd0,gpt7) would usually be sda7. But not always, if you boot directly from sdb or sdc.

The grub.cfg in /EFI/ubuntu is used by any copy of grub or shim anywhere in the efi partition and is just a configfile entry to tell it where to find your install and its grub.cfg that has all your boot entries.

System Setup is to get you into UEFI, some systems boot so fast with UEFI fast boot on that you cannot press a key to get into UEFI to make changes.

Mokmanager.efi is a key manager. That would be if you created your own UEFI keys or needed to add another key. Currently Ubuntu uses Microsoft's key so no new keys are now required.

---

### Post by Simon_Tomoko on 2015-07-29
Well  I for one don't dig around in the root and boot directory too much, but I do "tinker" a bit.  ;)

When making any changes to the grub you have to take care and I only mess with /etc/default/grub and here is the extent of my limited knowledge;

My comments are in **BOLD** below everything else is self explanatory.
```

# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

**#This option will select the first item on the grub menu. Changing it to 3 would be the 4th item listed.**
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**#Grub count down time default is 10, I like a bit more time when rebooting.**
GRUB_TIMEOUT=30
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
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



```

Sorry I don't have all the answers, but then if I did have "all the answers", I would have been a programmer and not gone into medicine.

---

