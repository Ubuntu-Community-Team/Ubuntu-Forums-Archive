---
title: "Ubuntu freeze during loading on dual booted lenovo system"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by Meric2000 on 2013-01-19
Hi,

I am having trouble Dual booting Ubuntu 12.10 alongside windows 8 on my Lenovo Z580.

I made some space for Ubuntu in win 8 and then used a live stick to install Ubuntu. Of course things were broken so I ran a live session from a live-stick and used "boot repair" this seemed to fix everything however after a few uses of Ubuntu and then a few uses of windows 8 Ubuntu broke and would only give a blank purple screen for upwards of 10 minutes. 

I have been through this rigmarole before  and was hoping that recent advancements in boot-repair would solve my issues.  No such luck so far.  I have also turned off quickboot in windows 8 just in case. 

BTW If I turn of quiet splash I see where the system is not frozen but displaying some kind of command line like display where it shows that it has just initialized the usb ports and i can plug in a mouse or usb stick and it will display that it has found a mouse or a usb stick.   

UEFI is on; secure boot is off; and I am perplexed!
Any help would be much appreciated.
Sincerely,
Meric2000 

PS
here is the boot repair that temporarily fixed my system
[http://paste.ubuntu.com/1548309/](http://paste.ubuntu.com/1548309/)

and here is the one i tried after it broke to no avail
[http://paste.ubuntu.com/1548392/](http://paste.ubuntu.com/1548392/)

---

### Post by rickierich on 2013-01-28
Did you manage to solve this problem, I have the same system and the problem persists.

---

### Post by oldfred on 2013-01-28
Have you set UEFI/BIOS to boot from ubuntu entry?

Some systems only boot the Windows entry, but with secure boot off should boot anything and Ubuntu's shim is the same secure boot ID and should boot anyway.

Is fastboot also turned off. But UEFI boot, not secure bot on?

If your system will only boot from Windows entry, Boot-Repair can rename grub file to Windows file name and backup Windows file. Then from grub menu it chain loads back to the backup Windows file to boot Windows.

You may want to fully backup the efi partition just to be safe.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC and please tell us what you observe.

---

