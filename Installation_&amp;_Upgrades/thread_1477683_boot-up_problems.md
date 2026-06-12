---
title: "boot-up problems"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by nintendude794 on 2010-05-09
Alright, so.... On my Dad's Windows 7 laptop, I had installed Ubuntu 9.10 next door.  Tonight when I went to update it to 10.4, the update process got stuck with twelve minutes remaining in the installation process.  So I did upper right and clicked shut down... Bad idea, apparently.  So I tried installing Netbook Edition 10.4 over that partition - at least I think it was that partition.  Now whenever I turn on the laptop, it has a list with a few different Ubuntu options, Windows 7, and Vista.  His laptop never had ANYTHING to do with Vista......  When I select 7, it takes me to a selection between 7 and Ubuntu - the old, corrupted installation that got stuck updating and won't boot.  So now, if my Dad wants to access his normal computer stuff, when he turns it on he's gonna have to select 7 twice.  Unless...

How do I fix this?

Thanks.

---

### Post by bcbc on 2010-05-09
You installed grub to the master boot record... just replace this with an alternative booloader, either windows (use the install dvd to repair) or you can use lilo (you can install lilo from your working ubuntu). Boot up and go to terminal.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Note: lilo used like this works exactly like the windows boot loader, it boots the partition with the boot flag set (this is always windows)

Note - after you do this you won't be able to boot your 'new' ubuntu install. Choosing 'Ubuntu' from the windows menu most likely won't do much of anything as your wubi install is what will be booting and unfortunately it is most likely corrupt now. 

Also, when you installed your new ubuntu you likely wrote over whatever was on that partition. 

PS that 'vista' is probably a recovery partition.

---

### Post by nintendude794 on 2010-05-09
so doing that command in Netbook Edition will essentially undo whatever installing Netbook Edition over that old Ubuntu partition did to my BIOS/grub/bootloader/............[clueless] interface?

how about installing 10.4 Desktop fresh, back where 9.10 was?  How might I go about doing that?

---

### Post by bcbc on 2010-05-09
> **nintendude794 said:**
> so doing that command in Netbook Edition will essentially undo whatever installing Netbook Edition over that old Ubuntu partition did to my BIOS/grub/bootloader/............[clueless] interface?

how about installing 10.4 Desktop fresh, back where 9.10 was?  How might I go about doing that?

Not sure really what you're asking here. The commands I mentioned (fixmbr and lilo) just replace the bootloader, so you won't see the 1st grub menu (I thought you just wanted to get the boot back to the way it was before). There is no 'undo' over that partition - it contains ubuntu if you installed it there.

You could install 10.04 but I don't recommend it - it has some confusing instructions about grub that is a newbie killer for many (kills windows). You can always upgrade from 9.10 at a later date when it's safer.

What do you want to do? If you are OK with the first grub menu, then you could boot windows and uninstall the wubi. Then you have to hit windows only once. You can even set grub to boot windows quietly (no prompt) and then you just use the SHIFT key when booting if you want ubuntu.

What I'd do, is state clearly what you want to achieve, and also post the results of the [bootinfoscript]("bootinfoscript.sourceforge.net").

---

### Post by nintendude794 on 2010-05-09
> **bcbc said:**
> Not sure really what you're asking here. The commands I mentioned (fixmbr and lilo) just replace the bootloader, so you won't see the 1st grub menu (I thought you just wanted to get the boot back to the way it was before). There is no 'undo' over that partition - it contains ubuntu if you installed it there.

You could install 10.04 but I don't recommend it - it has some confusing instructions about grub that is a newbie killer for many (kills windows). You can always upgrade from 9.10 at a later date when it's safer.

What do you want to do? If you are OK with the first grub menu, then you could boot windows and uninstall the wubi. Then you have to hit windows only once. You can even set grub to boot windows quietly (no prompt) and then you just use the SHIFT key when booting if you want ubuntu.

What I'd do, is state clearly what you want to achieve, and also post the results of the [bootinfoscript]("bootinfoscript.sourceforge.net").

Sorry if my wording is confusing.  Yes, I'd like to restore it so that I only have to select Windows once, as it was before, without affecting the actual Windows installation.

But also, I'd like the Ubuntu option to actually work and boot into something.  9.10, you recommend.  But trying to upgrade 9.10 to 10.4 is what led me to this issue in the first place.  Perhaps this time it won't freeze in mid-upgrade process.  What I am asking is how to re-associate that Ubuntu option with a non-corrupted, fresh Ubuntu installation.

Perhaps it would be easiest if there might be a way for me to just undo that partition, to restore its space back to the rest of the harddrive.  And then try installing 10.4 with the "Install Inside Windows" option, like I had done previously.

As I do not want to screw anything up, I have waited until we've discussed my issue and solutions more thoroughly, as to leave me with the best route possible.  Thanks so much for the help.

---

### Post by bcbc on 2010-05-09
> **nintendude794 said:**
> Sorry if my wording is confusing.  Yes, I'd like to restore it so that I only have to select Windows once, as it was before, without affecting the actual Windows installation.

But also, I'd like the Ubuntu option to actually work and boot into something.  9.10, you recommend.  But trying to upgrade 9.10 to 10.4 is what led me to this issue in the first place.  Perhaps this time it won't freeze in mid-upgrade process.  What I am asking is how to re-associate that Ubuntu option with a non-corrupted, fresh Ubuntu installation.

Perhaps it would be easiest if there might be a way for me to just undo that partition, to restore its space back to the rest of the harddrive.  And then try installing 10.4 with the "Install Inside Windows" option, like I had done previously.

As I do not want to screw anything up, I have waited until we've discussed my issue and solutions more thoroughly, as to leave me with the best route possible.  Thanks so much for the help.

Tell me more about the partition. Did you create it or was it there before? Did you use windows 7 to create it or do it as part of the install?

You can restore its space back by going into windows 7 and using the disk tools there. However, if you have a working bootable ubuntu on it, you might consider just leaving it there as well (it's considered more stable than a wubi install). You can fix your menu problems by a) [customizing the grub menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu") and b) removing the wubi install from within windows. This will leave you with one menu to select either Ubuntu or windows (which you can default to windows) and then that will boot straight into windows. 

If you don't want to do this, and rather go back to wubi, then replace the bootloader as I mentioned in my first post (lilo will do it), reclaim the partition from windows, and uninstall and reinstall ubuntu. In this case, I'd definitely recommend 9.10 with [this bug fix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10").

Finally, a warning - never install grub to a partition e.g. /dev/sda1 (only ever the MBR e.g. /dev/sda). For wubi you shouldn't install grub at all, not even to the MBR.

---

### Post by bcbc on 2010-05-09
Also, regarding 9.10 vs 10.04. Yes your problems were caused by upgrading, but that doesn't mean going with a clean 10.04 is without risk. It's just been released, so I'd recommend waiting a few weeks, maybe a month. That's just my opinion.

---

### Post by nintendude794 on 2010-05-09
> **bcbc said:**
> Tell me more about the partition. Did you create it or was it there before? Did you use windows 7 to create it or do it as part of the install?

You can restore its space back by going into windows 7 and using the disk tools there. However, if you have a working bootable ubuntu on it, you might consider just leaving it there as well (it's considered more stable than a wubi install). You can fix your menu problems by a) [customizing the grub menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu") and b) removing the wubi install from within windows. This will leave you with one menu to select either Ubuntu or windows (which you can default to windows) and then that will boot straight into windows. 

If you don't want to do this, and rather go back to wubi, then replace the bootloader as I mentioned in my first post (lilo will do it), reclaim the partition from windows, and uninstall and reinstall ubuntu. In this case, I'd definitely recommend 9.10 with [this bug fix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10").

Finally, a warning - never install grub to a partition e.g. /dev/sda1 (only ever the MBR e.g. /dev/sda). For wubi you shouldn't install grub at all, not even to the MBR.

The partition was created as part of the installation process.  "Install inside Windows" with a 9.10 disk created it.

And oh yeah... The partition has a working Netbook 10.4 install on it.  Perhaps if I remove the wubi install from within windows, the Windows or Ubuntu options will be there and maybe the Ubuntu one will boot what's on the partition it was associated with.  Do you think it would boot the 10.4 installation when selected?

---

### Post by bcbc on 2010-05-09
> **nintendude794 said:**
> The partition was created as part of the installation process.  "Install inside Windows" with a 9.10 disk created it.

And oh yeah... The partition has a working Netbook 10.4 install on it.  Perhaps if I remove the wubi install from within windows, the Windows or Ubuntu options will be there and maybe the Ubuntu one will boot what's on the partition it was associated with.  Do you think it would boot the 10.4 installation when selected?

The menu you are referring to is the windows boot menu. Wubi adds an entry in there, and it's for the wubi install. So, if you uninstall wubi, you won't get that menu anymore (* sometimes the uninstall fails to remove this and you have to do it manually). It will not work at all if the wubi install is fubared.

So, first off if you haven't already done this, confirm you can boot the 10.04 version make sure it's working fine. Then boot windows 7 and see if it's happy - windows doesn't like you splitting it's partition, but it might run a chkdsk and then be happy.

Then if it all works, customize the grub menu as per the link I gave previously and uninstall wubi, making sure it removes that second boot menu. Then you should be sorted.

If unsure of anything, post the results of [bootinfoscript]("bootinfoscript.sourceforge.net/") so I have a better idea of what's going on.

---

### Post by nintendude794 on 2010-05-11
> **bcbc said:**
> The menu you are referring to is the windows boot menu. Wubi adds an entry in there, and it's for the wubi install. So, if you uninstall wubi, you won't get that menu anymore (* sometimes the uninstall fails to remove this and you have to do it manually). It will not work at all if the wubi install is fubared.

So, first off if you haven't already done this, confirm you can boot the 10.04 version make sure it's working fine. Then boot windows 7 and see if it's happy - windows doesn't like you splitting it's partition, but it might run a chkdsk and then be happy.

Then if it all works, customize the grub menu as per the link I gave previously and uninstall wubi, making sure it removes that second boot menu. Then you should be sorted.

If unsure of anything, post the results of [bootinfoscript]("http://bootinfoscript.sourceforge.net/") so I have a better idea of what's going on.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   599,564,287   599,154,688   7 HPFS/NTFS
/dev/sda3         599,564,288   625,139,711    25,575,424  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       c1a1d36a-1e11-41bc-b031-69e3b0a29b3e   ext4                                     
/dev/sda1        A452407452404CEC                       ntfs       SYSTEM                        
/dev/sda2        205C04FD5C04D008                       ntfs                                     
/dev/sda3        ffe507d9-e1e7-427c-b966-ed749e4c19a2   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set ffe507d9-e1e7-427c-b966-ed749e4c19a2
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
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set ffe507d9-e1e7-427c-b966-ed749e4c19a2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ffe507d9-e1e7-427c-b966-ed749e4c19a2
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ffe507d9-e1e7-427c-b966-ed749e4c19a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ffe507d9-e1e7-427c-b966-ed749e4c19a2
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ffe507d9-e1e7-427c-b966-ed749e4c19a2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ffe507d9-e1e7-427c-b966-ed749e4c19a2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ffe507d9-e1e7-427c-b966-ed749e4c19a2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a452407452404cec
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 205c04fd5c04d008
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1

=================== sda3: Location of files loaded by Grub: ===================


 311.5GB: boot/grub/core.img
 311.5GB: boot/grub/grub.cfg
 312.2GB: boot/initrd.img-2.6.32-22-generic-pae
 312.0GB: boot/vmlinuz-2.6.32-22-generic-pae
 312.2GB: initrd.img
 312.0GB: vmlinuz
```

---

### Post by bcbc on 2010-05-12
Edit your previous post and put the bootinfoscript results between code tag. (highlight the text and hit the # sign above). It makes it easier to browse the thread.

So did you confirm that Win 7 and the new ubuntu install are booting ok? 

What I can see from the bootinfoscript is that you already have 10.04 installed and the wubi install is broken ("wrong fs type, bad option, bad superblock").

That "vista" is the actual windows 7 install - windows 7 seems to have a separate boot partition (which is on sda1). It's just grub2 getting confused and calling it vista. You probably can't boot it directly anyway.

Option 1: keep the 'side by side' install of windows7 and ubuntu...it's just that the grub2 menu doesn't 'look right'. I recommend creating a custom menu with [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu) 
Add two options to the custom menu: Windows and Ubuntu - as per the instructions on the link. The Windows one will look like this:
> menuentry "Windows 7" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set a452407452404cec
chainloader +1
}

You can set the default to be "Windows 7" or you could even have it boot directly into Windows 7 unless you hold down the shift key - that way no one else has to deal with ubuntu.

Then once booted into windows7 uninstall the wubi ubuntu using add/remove programs. That takes care of the double menu.

Option 2: If you really want to undo that partition (sda3), adding it back to windows, and go with a new wubi install. Then do this:
1. boot the current working ubuntu (on sda3)
2. install lilo as per the instructions shown elsewhere on the thread (after this you won't be able to boot ubuntu except with the live cd)
3. Reboot, and select windows
4. Use the disk manager to reclaim the ubuntu partition - delete it, reformat to ntfs, merge it - whatever options it gives you
5. Uninstall and reinstall wubi.

Backup any files data that are critical before doing the above.

---

### Post by nintendude794 on 2010-05-12
> **bcbc said:**
> Edit your previous post and put the bootinfoscript results between code tag. (highlight the text and hit the # sign above). It makes it easier to browse the thread.

So did you confirm that Win 7 and the new ubuntu install are booting ok? 

What I can see from the bootinfoscript is that you already have 10.04 installed and the wubi install is broken ("wrong fs type, bad option, bad superblock").

That "vista" is the actual windows 7 install - windows 7 seems to have a separate boot partition (which is on sda1). It's just grub2 getting confused and calling it vista. You probably can't boot it directly anyway.

Option 1: keep the 'side by side' install of windows7 and ubuntu...it's just that the grub2 menu doesn't 'look right'. I recommend creating a custom menu with [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu) 
Add two options to the custom menu: Windows and Ubuntu - as per the instructions on the link. The Windows one will look like this:


You can set the default to be "Windows 7" or you could even have it boot directly into Windows 7 unless you hold down the shift key - that way no one else has to deal with ubuntu.

Then once booted into windows7 uninstall the wubi ubuntu using add/remove programs. That takes care of the double menu.

Option 2: If you really want to undo that partition (sda3), adding it back to windows, and go with a new wubi install. Then do this:
1. boot the current working ubuntu (on sda3)
2. install lilo as per the instructions shown elsewhere on the thread (after this you won't be able to boot ubuntu except with the live cd)
3. Reboot, and select windows
4. Use the disk manager to reclaim the ubuntu partition - delete it, reformat to ntfs, merge it - whatever options it gives you
5. Uninstall and reinstall wubi.

Backup any files data that are critical before doing the above.

If I go with Option 1, then selecting Ubuntu will boot into the working installation of Netbook 10.4?

If not, Option 2 seems best.

---

### Post by bcbc on 2010-05-12
> **nintendude794 said:**
> If I go with Option 1, then selecting Ubuntu will boot into the working installation of Netbook 10.4?

If not, Option 2 seems best.

Yes, option 1 boots the working 10.04 on the new partition.

---

### Post by nintendude794 on 2010-05-13
> **bcbc said:**
> Yes, option 1 boots the working 10.04 on the new partition.
Cool, I'll try that later.

---

