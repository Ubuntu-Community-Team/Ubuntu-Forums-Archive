---
title: "&quot;can't access tty&quot; error using multiboot"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by mel2000 on 2010-04-03
I used MultibootISOs.exe to create a multiboot USB consisting of the following apps. All their Live CDs work fine on my computer but a couple of them had trouble with the transition to USB booting.

Ophcrack Vista 2.3.1 - OK
Ophcrack XP 2.3.1 - OK
Partition Wizard 4.2 - OK
Puppy Linux 4.3.1 - OK
UBCD4Win 3.5 - OK
Paragon Backup & Recovery 10.1 - OK
YLMF 1.0 (Ubuntu) - Error: "can't access tty; job control turned off"
Dr. Web CureIt 5.0.2 - Same as YLMF

I configured menu.lst entries for booting from the ISO or from ISO files extracted to a folder, but the errors are the same.

title YLMF Linux 1.0 (ISO)
find --set-root /YlmF_OS_EN_v1.0.iso
map /YlmF_OS_EN_v1.0.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title YLMF Linux 1.0 (extracted folder)
find --set-root /ylmf/casper/vmlinuz
kernel /ylmf/casper/vmlinuz file=/ylmf/preseed/ylmf.seed boot=/ylmf/casper ramdisk_size=1048576 root=/dev/ram looptype=squashfs loop=/ylmf/casper/filesystem.squashfs
initrd /ylmf/casper/initrd.lz

Googling only turned up old posts with no definite resolutions. Any help finding a solution will be greatly appreciated. Thanks.

---

### Post by mel2000 on 2010-04-04
Problem solved. Turns out it was due to a misconfiguration of my menu.lst entry for YLMF. I changed the entry as follows and now YLMF boots up to its interface properly.
 
BEFORE:
title YLMF Linux 1.0 (ISO)
find --set-root /YlmF_OS_EN_v1.0.iso
map /YlmF_OS_EN_v1.0.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
 
AFTER:
title YLMF Linux 1.0 (ISO)
find --set-root /YlmF_OS_EN_v1.0.iso
map /YlmF_OS_EN_v1.0.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
kernel /casper/vmlinuz file=/preseed/ylmf.seed boot=casper iso-scan/filename=/YlmF_OS_EN_v1.0.iso
initrd /casper/initrd.lz
 
Sorry for the interruption.;)

---

