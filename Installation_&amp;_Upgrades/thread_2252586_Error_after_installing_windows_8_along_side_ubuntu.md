---
title: "Error after installing windows 8 along side ubuntu 14.04"
date: 2014-11-12
forum: Installation &amp; Upgrades
---

### Post by wbf0007 on 2014-11-12
Hi, I am getting an error after installing windows 8 onto a separate hard drive and then trying to update the grub to have win 8, win 7, and ubuntu on the boot menu. After installing windows 8, i was allowed to go to ubuntu once, and then i tried boot-repair to fix the menu, but afterward it gave me this error: error: file '/boot/grub/i386-pc/normal.mod' not found, and then proceeds  to go to grub rescue (don't know any options to type into it). i looked into the url it gives in case of an error, and found this in it (i can post the whole paste.ubuntu.com link if you need it): 

/boot/efi detected in the fstab of sdb3: UUID=2269-4592	 (sda2)
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sdb3/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sdb3/boot/efi/EFI/Boot/bootx64.efi
grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.
,.

Reinstall the grub-efi of sdb3
grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.
grub-install : exit code of grub-install :1
Error: no grub*.efi generated. Please report this message to [email]boot.repair@gmail.com[/email]

as of right now the only os i can get onto is win 8, and i'd like to be able to go back to win 7 or ubuntu if possible 
(while keeping win 8 since it's a 64 bit version and win 7 is only 32), but if i have to delete it to get the others back
i can as a last resort. i've tried emailing the paste url to [email]boot.repair@gmail.com[/email] but i haven't gotten a response back so 
after talking to microsoft and my mobo manufacturer i was directed to talk on here.

---

### Post by oldfred on 2014-11-12
If your Windows 7 is 32 bit then it also is BIOS boot on a MBR drive.
And UEFI uses gpt partitioning, Windows installed in UEFI boot mode will only boot from gpt drives.
And UEFI and BIOS are not compatible. You may be able to boot from UEFI boot menu or one time boot key. Some systems required you to turn on/off UEFI or CSM settings, others auto switch.

Best to see details as it can get complex. Do not run auto fix with multiple drives.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

