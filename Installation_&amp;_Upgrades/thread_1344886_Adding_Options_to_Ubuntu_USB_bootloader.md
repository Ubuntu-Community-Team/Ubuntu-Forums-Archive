---
title: "Adding Options to Ubuntu USB bootloader"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by dublea on 2009-12-03
I've created a Ubuntu 9.10 boot USB disk.  I also like to use Hiren's USB applications.  Having to use both at my work causes me to carry two thumb drives.  I'd like to be able to put them on the same drive with one menu system.  From what I can tell, it looks as though the GUI loader for Ubuntu is grub based and Hiren's uses grub4dos with it's loader.  I've been able to modify and add menu choices to the Ubuntu menu but can't figure out how to get it to load the Hiren's menu.  

Here's what I've done to the text.conf of the Ubuntu Menu:

```
default live
label live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
label live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz
  append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --
label check
  menu label ^Check disc for defects
  kernel /casper/vmlinuz
  append  noprompt boot=casper integrity-check initrd=/casper/initrd.lz quiet splash --
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label Start Hiren's BootUSB 10.0
  menu lable Boot ^Hiren's 10.0
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80
```

Here is what the bootable choice menu for Hiren's looks like:
```
default /default

title Boot from Hard Drive - Windows XP (NTLDR)
fallback 1
find --set-root --ignore-floppies --ignore-cd /ntldr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /ntldr
chainloader /ntldr
savedefault --wait=2

title Boot from Hard Drive - Windows Vista/7 (BOOTMGR)
fallback 2
find --set-root --ignore-floppies --ignore-cd /bootmgr
map () (hd0)
map (hd0) ()
map --rehook
find --set-root --ignore-floppies --ignore-cd /bootmgr
chainloader /bootmgr
savedefault --wait=2

title --------------------
root

title Start Hiren's BootCD
find --set-root /HBCD/boot.gz
map --mem /HBCD/boot.gz (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)
map --floppies=1
boot

# If you have any problem loading the above grub4dos map commands then try using memdisk kernel
# title Start Hiren's BootCD
# find --set-root /HBCD/boot.gz
# kernel /HBCD/memdisk
# initrd /HBCD/boot.gz

title Mini Windows Xp
find --set-root /HBCD/XPLOADER.BIN
chainloader /HBCD/XPLOADER.BIN
```

As you can see, it points to a boot.gz file.  This file a menu system to utilities and applications for repairing computers.
The system also has a MiniXP on it for registry repairs and edits and it boots to an XPloader.BIN file.
I'd like to keep using this GUI based bootloader for Ubuntu.  Any suggestions would be great.

---

