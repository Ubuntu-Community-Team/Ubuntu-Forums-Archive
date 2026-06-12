---
title: "Kernel Issues from the upgrade"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by megaman2000 on 2009-10-12
When I first upgraded to 9.10 from 9.04 I had no idea why I lost support for audio, my trackpad, and graphics intensives like compiz fusion. I then realized that it was because Grub 2 was booting with kernel 2.6.28-15 and not 2.6.31-15.

When I edited the parameters in Grub 2 to the new kernel everything was running fine. But then when I tried editing /boot/grub/menu.lst from 2.28 to 2.31 and saved it, restarted...It still booted in to 2.28

I've tried using update-grub and that didn't help anything. I logged in to root and tried physically removing all the 2.28 files from /boot and the only thing that did was make it so I can't boot up at all without first editing the boot parameters to boot from 2.31.

Any help/suggestions?

---

### Post by ranch hand on 2009-10-12
Well that is confusing.

Let us see, you changed something in grub2 and you edited the /boot/grub/menu.lst.

Ah, the source of the confusion is that in grub2 there is no /boot/grub/menu.lst.

So what is going on?

---

### Post by ajgreeny on 2009-10-12
I recall reading about this problem of the grub change to grub2 elsewhere in the forum.  It seems that a distro upgrade from 9.04 with legacy grub, to 9.10 with grub2 can cause the system a bit of a headache.  Maybe you need to consider a separate /boot partition, or something similar, but how you can add that to an existing OS, I am afraid I don't know.

---

### Post by rippin on 2009-10-12
> **megaman2000 said:**
> When I first upgraded to 9.10 from 9.04 I had no idea why I lost support for audio, my trackpad, and graphics intensives like compiz fusion. I then realized that it was because Grub 2 was booting with kernel 2.6.28-15 and not 2.6.31-15.

When I edited the parameters in Grub 2 to the new kernel everything was running fine. But then when I tried editing /boot/grub/menu.lst from 2.28 to 2.31 and saved it, restarted...It still booted in to 2.28

I've tried using update-grub and that didn't help anything. I logged in to root and tried physically removing all the 2.28 files from /boot and the only thing that did was make it so I can't boot up at all without first editing the boot parameters to boot from 2.31.

Any help/suggestions?

Before you Borked it by removal of items, you likely needed to choose the kernel you wanted to boot either manually or by making it the first (default) option. See you after the re-install ! <g>.

---

### Post by ranch hand on 2009-10-12
You are also going to have trouble booting intl 2.6.31-15, at least I think so.
```

krap@krap-desktop:~$ uname -a
Linux krap-desktop 2.6.31-13-generic #44-Ubuntu SMP Sat Oct 10 15:27:14 UTC 2009 x86_64 GNU/Linux

```
All of my 9.10 installs are running on that except for one that I have left on 31-12 just in case of problems.

---

### Post by megaman2000 on 2009-10-12
> **rippin said:**
> Before you Borked it by removal of items, you likely needed to choose the kernel you wanted to boot either manually or by making it the first (default) option. See you after the re-install ! <g>.

I saved all the old kernel files to a folder on the desktop. If I replace them have I averted borking, or is it too late?

---

### Post by rippin on 2009-10-12
> **megaman2000 said:**
> I saved all the old kernel files to a folder on the desktop. If I replace them have I averted borking, or is it too late?

Good on you! You smartly saved your rear ;) With the right permissions, you can likely bail yourself out. Can you post your menu.1st?

---

### Post by megaman2000 on 2009-10-12
> **rippin said:**
> Good on you! You smartly saved your rear ;) With the right permissions, you can likely bail yourself out. Can you post your menu.1st?

Did you mean menu.lst? that's the only one I can find :l

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=463ec3fe-d467-4213-84d4-c46c2a79072d

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu karmic (development branch), kernel 2.6.31-13-generic
uuid        463ec3fe-d467-4213-84d4-c46c2a79072d
kernel        /boot/vmlinuz-2.6.31-13-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-13-generic
quiet

title        Ubuntu karmic (development branch), kernel 2.6.31-13-generic (recovery mode)
uuid        463ec3fe-d467-4213-84d4-c46c2a79072d
kernel        /boot/vmlinuz-2.6.31-13-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro  single
initrd        /boot/initrd.img-2.6.31-13-generic

title        Ubuntu karmic (development branch), kernel 2.6.28-15-generic
uuid        463ec3fe-d467-4213-84d4-c46c2a79072d
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu karmic (development branch), kernel 2.6.28-15-generic (recovery mode)
uuid        463ec3fe-d467-4213-84d4-c46c2a79072d
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Chainload into GRUB 2
root        463ec3fe-d467-4213-84d4-c46c2a79072d
kernel        /boot/grub/core.img

title        Ubuntu karmic (development branch), memtest86+
uuid        463ec3fe-d467-4213-84d4-c46c2a79072d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1

---

### Post by VMC on 2009-10-12
Your going to have to output your grub2 menu. Found at "/boot/grub/grub.cfg", so we can see what's what and where its booting from.

---

### Post by megaman2000 on 2009-10-13
This?
> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,6)
search --fs-uuid --set 463ec3fe-d467-4213-84d4-c46c2a79072d
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
set root=(hd0,6)
search --fs-uuid --set 463ec3fe-d467-4213-84d4-c46c2a79072d
menuentry "Ubuntu, linux 2.6.28-15-generic" {
    linux    /boot/vmlinuz-2.6.28-15-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro  quiet splash
    initrd    /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, linux 2.6.28-15-generic (single-user mode)" {
    linux    /boot/vmlinuz-2.6.28-15-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro single 
    initrd    /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic" {
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro  quiet splash
    initrd    /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic (single-user mode)" {
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro single 
    initrd    /boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    set root=(hd0,2)
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    set root=(hd0,3)
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

---

### Post by ranch hand on 2009-10-13
Well, if you are still there and going to work on this, here is what you better do;

Rename the /boot/grub/menu.lst to menu.OLD and move it to your Desktop to be safe.  Do the same thing with your grub.cfg file.

Go to synaptic and reload it.  Find grub.  Remove anything you find in synaptic related to grub (.97 or 1.97).

Staying with synaptic, install Grub2 (meta package for grub2), grub-common, and grub-pc.  Be sure that you are watching the :"details" when this is being installed to see if update grub is run and to see if it is installed on your drive.

I would, if that happened (and I am sure it would), update your machine while you are in synaptic.

This should get you a kernel update and should run update-grub again.

Repost your /boot/grub/grub.cfg contents.  Do not reboot until this is straight.

---

### Post by megaman2000 on 2009-10-13
Am I doin it right?

> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 463ec3fe-d467-4213-84d4-c46c2a79072d
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-13-generic" {
        recordfail=1
        save_env recordfail
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 463ec3fe-d467-4213-84d4-c46c2a79072d
    linux    /boot/vmlinuz-2.6.31-13-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-13-generic
}
menuentry "Ubuntu, Linux 2.6.31-13-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 463ec3fe-d467-4213-84d4-c46c2a79072d
    linux    /boot/vmlinuz-2.6.31-13-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro single 
    initrd    /boot/initrd.img-2.6.31-13-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        save_env recordfail
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 463ec3fe-d467-4213-84d4-c46c2a79072d
    linux    /boot/vmlinuz-2.6.28-15-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 463ec3fe-d467-4213-84d4-c46c2a79072d
    linux    /boot/vmlinuz-2.6.28-15-generic root=UUID=463ec3fe-d467-4213-84d4-c46c2a79072d ro single 
    initrd    /boot/initrd.img-2.6.28-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set e8bc3d20bc3ceb28
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set d8b26317b262fa00
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by ranch hand on 2009-10-13
Oh boy, that looks really good.

Now, there has been some problem with booting and the complete menuentry generated by 10_linux.

If this happens to you, you will need to get back to your menu and hit e.  Edit the first to lines;
```

recordfail=1
        save_env recordfail

```
out.  That should do it.

If you want to have an entry that will never need to change you could do this with the Ubuntu entry in your /etc/grub.d/40_custom file;
```

echo "Adding Ubuntu9.10 on sda6" >&2
cat << EOF
menuentry "Ubuntu9.10 on sda6" {
        set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 so quiet splash
        initrd /initrd.img
}
EOF

```
You need to check the drive numbers to make sure I got them right.  Drop that into the 40_custom file and I would save it as 06_custom.  This will put that entry at the top of the menu you see on the screen.  If you leave it as 40 it will be at the bottom.

The stuff between the " " is what you see for the title.

The stuff between the { } is what you boot from.

Note that this entry just refers to the partition and basically says boot anything found there.

You can put your entries for Win Jerry Lewis Pro in that file the same way, add your title between the " " and cut and paste the working part of you entry between the { }.

You need to go to preferences on your editor (I used gedit or screem) and make sure that text wrapping is NOT enabled.

The { }s need to be exactly where they are above.  Well every thing needs to be that way or it just won't work.

The Ubuntu title you may want to change too.  That will never need to be updated for kernels or anything else.

If you put that in you need to run "sudo update-grub" to write it to the /boot/grub/grub.cfg file.

Reboot.  Try the 10_linux generated entry first.  Hopefully it works.  That way you will know you can get to the recovery mode.  I would reboot again and try the custom entry (if any).

Then I would go and just remove (synaptic is your friend) the Jaunty kernels.  This will run update-grub and remove them from the menu.

It would be great if you would post back your grub.cfg file no matter what the out come.  Note that I am assuming success.

---

### Post by megaman2000 on 2009-10-13
> **ranch hand said:**
> Oh boy, that looks really good.

Now, there has been some problem with booting and the complete menuentry generated by 10_linux.

If this happens to you, you will need to get back to your menu and hit e.  Edit the first to lines;
```

recordfail=1
        save_env recordfail

```out.  That should do it.

If you want to have an entry that will never need to change you could do this with the Ubuntu entry in your /etc/grub.d/40_custom file;
```

echo "Adding Ubuntu9.10 on sda6" >&2
cat << EOF
menuentry "Ubuntu9.10 on sda6" {
        set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 so quiet splash
        initrd /initrd.img
}
EOF

```You need to check the drive numbers to make sure I got them right.  Drop that into the 40_custom file and I would save it as 06_custom.  This will put that entry at the top of the menu you see on the screen.  If you leave it as 40 it will be at the bottom.

The stuff between the " " is what you see for the title.

The stuff between the { } is what you boot from.

Note that this entry just refers to the partition and basically says boot anything found there.

You can put your entries for Win Jerry Lewis Pro in that file the same way, add your title between the " " and cut and paste the working part of you entry between the { }.

You need to go to preferences on your editor (I used gedit or screem) and make sure that text wrapping is NOT enabled.

The { }s need to be exactly where they are above.  Well every thing needs to be that way or it just won't work.

The Ubuntu title you may want to change too.  That will never need to be updated for kernels or anything else.

If you put that in you need to run "sudo update-grub" to write it to the /boot/grub/grub.cfg file.

Reboot.  Try the 10_linux generated entry first.  Hopefully it works.  That way you will know you can get to the recovery mode.  I would reboot again and try the custom entry (if any).

Then I would go and just remove (synaptic is your friend) the Jaunty kernels.  This will run update-grub and remove them from the menu.

It would be great if you would post back your grub.cfg file no matter what the out come.  Note that I am assuming success.

Thanks alot! It worked fine the first time!

---

### Post by ranch hand on 2009-10-13
Better mark this as Solved then (top of page under Thread Tools).

Glad it worked.  I think that grub2 is going to be great if it ever gets out of beta.

---

### Post by kansasnoob on 2009-10-13
> **ranch hand said:**
> Better mark this as Solved then (top of page under Thread Tools).

Glad it worked.  I think that grub2 is going to be great if it ever gets out of beta.

Good job ranch hand! Thought I'd share something just as an "FYI" regarding mixed legacy-grub and grub2 files in the same grub directory. 

Of course my /boot directory is modified from playing with changing from legacy-grub to grub2 and vice versa, but note the commands in **[COLOR="Red"]bold red[/COLOR]**, you'll notice in [COLOR="Blue"]blue[/COLOR] that /boot has three grub directories (two of which I renamed), and my current /boot/grub is a legacy-grub whereas /boot/grub_backup is a typical grub2: 

> lance@lance-desktop:~$ **[COLOR="Red"]ls ~ /boot[/COLOR]**
/boot:
abi-2.6.31-11-generic         initrd.img-2.6.31-13-generic
abi-2.6.31-12-generic         memtest86+.bin
abi-2.6.31-13-generic         System.map-2.6.31-11-generic
config-2.6.31-11-generic      System.map-2.6.31-12-generic
config-2.6.31-12-generic      System.map-2.6.31-13-generic
config-2.6.31-13-generic      vmcoreinfo-2.6.31-11-generic
[COLOR="Blue"]grub                          vmcoreinfo-2.6.31-12-generic
grub_backup                   vmcoreinfo-2.6.31-13-generic
grub_legacy                   vmlinuz-2.6.31-11-generic[/COLOR]
initrd.img-2.6.31-11-generic  vmlinuz-2.6.31-12-generic
initrd.img-2.6.31-12-generic  vmlinuz-2.6.31-13-generic

/home/lance:
Desktop    Downloads         Music     Projects  reward.ps  Ubuntu One
Documents  examples.desktop  Pictures  Public    Templates  Videos
lance@lance-desktop:~$ **[COLOR="Red"]ls ~ /boot/grub[/COLOR]**
/boot/grub:
default        grubenv            menu.lst~          splashimages
device.map     installed-version  menu.lst.backup    stage1
e2fs_stage1_5  jfs_stage1_5       minix_stage1_5     stage2
fat_stage1_5   menu.lst           reiserfs_stage1_5  xfs_stage1_5

/home/lance:
Desktop    Downloads         Music     Projects  reward.ps  Ubuntu One
Documents  examples.desktop  Pictures  Public    Templates  Videos
lance@lance-desktop:~$ **[COLOR="Red"]ls ~ /boot/grub_backup[/COLOR]**
/boot/grub_backup:
915resolution.mod  efiemu64.o     lspci.mod       reboot.mod
acpi.mod           efiemu.mod     lua.mod         reiserfs.mod
affs.mod           elf.mod        lvm.mod         scsi.mod
afs_be.mod         ext2.mod       mdraid.mod      search.mod
afs.mod            extcmd.mod     memdisk.mod     serial.mod
aout.mod           fat.mod        memrw.mod       setjmp.mod
ata.mod            font.mod       minicmd.mod     sfs.mod
ata_pthru.mod      fs_file.mod    minix.mod       sh.mod
at_keyboard.mod    fshelp.mod     mmap.mod        sleep.mod
befs_be.mod        fs.lst         moddep.lst      tar.mod
befs.mod           fs_uuid.mod    msdospart.mod   terminfo.mod
biosdisk.mod       gfxterm.mod    multiboot.mod   test.mod
bitmap.mod         gptsync.mod    normal.mod      tga.mod
blocklist.mod      grub.cfg       ntfscomp.mod    true.mod
boot.img           grubenv        ntfs.mod        udf.mod
boot.mod           gzio.mod       ohci.mod        ufs1.mod
bsd.mod            halt.mod       part_acorn.mod  ufs2.mod
bufio.mod          handler.lst    part_amiga.mod  uhci.mod
cat.mod            handler.mod    part_apple.mod  usb_keyboard.mod
cdboot.img         hdparm.mod     part_gpt.mod    usb.mod
chain.mod          hello.mod      partmap.lst     usbms.mod
cmp.mod            help.mod       part_msdos.mod  usbtest.mod
command.lst        hexdump.mod    part_sun.mod    vbeinfo.mod
configfile.mod     hfs.mod        parttool.lst    vbe.mod
core.img           hfsplus.mod    parttool.mod    vbetest.mod
cpio.mod           iso9660.mod    password.mod    vga.mod
cpuid.mod          jfs.mod        pci.mod         vga_text.mod
crc.mod            jpeg.mod       play.mod        video_fb.mod
datehook.mod       kernel.img     png.mod         video.mod
date.mod           keystatus.mod  probe.mod       videotest.mod
datetime.mod       linux16.mod    pxeboot.img     xfs.mod
device.map         linux.mod      pxecmd.mod      xnu.mod
diskboot.img       lnxboot.img    pxe.mod         xnu_uuid.mod
dm_nv.mod          loadenv.mod    raid5rec.mod    zfsinfo.mod
drivemap.mod       loopback.mod   raid6rec.mod    zfs.mod
echo.mod           lsmmap.mod     raid.mod
efiemu32.o         ls.mod         read.mod

/home/lance:
Desktop    Downloads         Music     Projects  reward.ps  Ubuntu One
Documents  examples.desktop  Pictures  Public    Templates  Videos

Never mind the old /boot/grub_legacy it's just an older legacy-grub leftover from playing around, and I don't have a "mixed" legacy-grub and grub2 /boot/grub to display right now, but from that output (given your knowledge) it's fairly easy to see if you're dealing with a "mixed" /boot/grub directory.

I've found that such a "mixed" directory can result in strange "grub" behavior (like breakage), whether it's legacy-grub or grub2, especially following distribution updates to grub, grub-common, or grub-pc.

Of course I'm as new to this as everyone else, but thought you and others might want to put the **[COLOR="Red"]ls ~[/COLOR]** command to good use.

Just another tool to use:)

---

### Post by ranch hand on 2009-10-13
That is really cool.  Wow, I have got to try that.

I put a link to that post on the Grub2 Introduction page.

---

