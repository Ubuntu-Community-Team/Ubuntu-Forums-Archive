---
title: "Setting up a dual-boot"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by ThumbBumpkins on 2007-03-07
hey guys, I am brand new to Ubuntu and linux in general. I just established ubuntu and so far it seems really great. My problem is this: I split my boot drive in two, with ubuntu linux on one half and windows xp on the other. I installed ubuntu first, and after installing windows, my computer just boots straight to it. I can't change the boot order for different partitions of the same disk, so my linux installation is essentially inaccessible. I've heard of something called GRUB, but I have no idea how to set it up or configure it. any help would be extremely appreciated.

---

### Post by lacroserocks on 2007-03-07
should have installed Windows first because the Grub replaces NTLDR

---

### Post by Kateikyoushi on 2007-03-07
Nothing is lost except for a little time because now you have to set up grub manually one more time. Read on for more instructions. [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by ThumbBumpkins on 2007-03-07
ok, so now grub does appear, but barely. it says "starting grub..." and says "press esc to go to the menu." however, when i press esc absolutely nothing happens and instead i just boot back into ubuntu, so now my windows install is inaccessible. i am using a wireless keyboard that is connected through usb, which may be the problem, however, this keyboard does work in other parts of the BIOS. is there another step i need to take?

---

### Post by ThumbBumpkins on 2007-03-07
scratch that last problem, i have a new one. it was the keyboard after all. so now i can get into grub, however my windows xp install is not listed. any more help would be greatly appreciated.

---

### Post by mikewhatever on 2007-03-07
Can you please open the Terminal (Application->Accessories->Terminal) and post the output of the following:
> sudo gedit /boot/grub/menu.lst

at the very end, there should be a boot entry for Windows. If not there, try adding the following to the very end of the file, save and exit.
> # This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1

Edit: The Windows entry should not be there, since you reinstalled GRUB. Also, you may need to check for correct entry for Windows partition. I suspect it may be other then (hd0,0). If you do not know which one it is, post the output of > sudo fdisk -l

---

### Post by Kateikyoushi on 2007-03-07
That works if your windows partition is hda1.
 If not you can list your partition layout by typing fdisk -l in the terminal.

---

### Post by ThumbBumpkins on 2007-03-07
i typed sudo gedit /boot/grub/menu.lst , and here is what I saw:

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot


i then added what you told me to, and it did not work. it did add an entry for Windows XP in the OS list, but selecting it did nothing.

EDIT: i saw your edit, and typed fdisk -l results: 

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4589    36861111   83  Linux
/dev/sda2   *        4590       10010    43544182+   7  HPFS/NTFS

---

### Post by Kateikyoushi on 2007-03-07
Your ntfs partition is sda2 so change the root (hd0,0) to (hd 0,1) in the newly added windows entry.

---

### Post by ThumbBumpkins on 2007-03-07
nice, its working like a charm. thank you so much everyone.

---

