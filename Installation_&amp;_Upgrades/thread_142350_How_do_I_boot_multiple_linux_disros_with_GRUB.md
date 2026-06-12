---
title: "How do I boot multiple linux disros with GRUB?"
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by ixus_123 on 2006-03-10
So Ubuntu detects Windows Xp fine & sets up a nice dual boot system.  The thing I want to do, however, is to have a small Windows partition, Ubuntu 5.10, /home, then other partitions for the likes of dapper, ubuntu hula / cms test system, or anyother distro I decide I want to try out.

I think I got the set up working once years ago with Windows 98, Suse & slackware but that was with Lilo & even so I can't remember how it was done.

Could someone please write a howto or guide me through the steps of installing more than on instance of linux on a PC?

Do I need a spearate boot partition & how large should it be to handle, say 4 flavours of Linux?

My current set up is as follows although I'm about to change everything with a clean install of Windows / Linux

hda1  -  57gb  -  Win NTFS
hda5  -  1gb  -  swap
hda6  -  18gb  -  / (ubuntu dapper) - ext3
hda7  -  1gb  -  swap
hda8  -  110gb  - /home -ext3

hdb1  -  115gb  -  /stuff (mp3 / video etc) fat32

---

### Post by retsaw on 2006-03-10
[Here](http://www.justlinux.com/forum/showthread.php?t=143973) is a very good guide to multi-booting with Grub, that was posted to the Justlinux forums.

---

### Post by ixus_123 on 2006-03-10
I can't see the wood for teh trees in that link.  Thanks but I was hoping for something explained in simpler terms.

ps - I don't have a floppy drive & would prefer to be able t this without the use of either liveCD or a grub boot CD


if anyone can help?

---

### Post by Irony on 2006-03-10
Its easy with grub to add operating systems. For example I had the following configuration;

[PHP]## ## End Default Options ##

title		Breezy 5.10, hda5
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash vga=0x31A
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Breezy 5.10, hda5 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Breezy 5.10, hda5 (memtest86+)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot

title		Breezy 5.10, moved hda3
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash vga=0x31A
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Breezy 5.10, moved hda3 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Breezy 5.10, moved hda3 (memtest86+)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry added by irony for an existing linux
# installation on /dev/hda9
title		Fedora Core 4, hda9
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.11-1.1369_FC4 root=/dev/hda9 ro quiet splash
initrd		/boot/initrd-2.6.11-1.1369_FC4.img
savedefault
boot

# This entry automatically added by the Debian installer for an existing linux
# installation on /dev/hda8
title		Zenwalk 2.01, hda8
root		(hd0,7)
kernel		/boot/vmlinuz root=/dev/hda8 ro
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		XP Home SP2, hda1
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/PHP]

Note I had 2 Ubuntus and FC4 and Zenwalk. I installed these operating systems but when it came to installing the bootloader I skipped that bit. I simply added in the entries above later. The key is looking at the kernel and initrd entries and noting the file paths - these are determined by first mounting the partitions from your main ubuntu partition and then simply navigating to the paths above.

For example the kernel files for FC4 is /boot/vmlinuz-2.6.11-1.1369_FC4, whereas the file for Breezy is /boot/vmlinuz-2.6.12-10-386 - you can navigate your way into Breezy to see this.

Note in this case grub is pointing at ubuntu in hda5, I have since pointed grub at hda3 - in other words grub looked at hda5 for a grub menu.lst but now looks at hda3 for a grub menu.lst

---

### Post by Irony on 2006-03-10
Note also that you have to alter the root entry.

---

### Post by ixus_123 on 2006-03-10
Thanks - I think I get that although the proof will come when I do a clean install.

Do you have a separate /boot partition or i your boot loader written to the MBR?

---

### Post by Irony on 2006-03-10
MBR's always worked fined for me. If instead you did it to a beginning of particular superblock then you would have to change the bootflag to that superblock.

---

### Post by jbennett on 2006-03-10
I would also like to multi-boot Windows XP with Ubuntu and Kubuntu.  My system currently dual boots XP and Ubuntu, but I would like to add Kubuntu.  If I boot the install CD for Kubuntu, do I create a new '/' partition for Kubuntu?  And, if I do that, will it install to the right place?  Does anyone know if someone has written a howto that explains specifically how to do this?

Any help is greatly appreciated.

Thanks:)

---

### Post by ixus_123 on 2006-03-11
hmm. . .

Just installed XP & Breezy.

There doesn't seem to be an option to skip installing GRUB but it says I can specify /dev/hda2 & so on.

That doesn't lopk like such a good option to me - surely that would mean grub would load up twice.

I'll just continue with the field left black & report back. . .

---

