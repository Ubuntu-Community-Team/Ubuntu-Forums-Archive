---
title: "Windows 10 hides grub after booting"
date: 2018-03-27
forum: Installation &amp; Upgrades
---

### Post by rubenstobbart on 2018-03-27
Hello, I am new to the forum. Greetings to all.

I have a Sony Vaio with UEFI bios (can be changed to Legacy) and dual boot Ubuntu 16.04 LTS/ Windows 10.

The problem is the following:


[LIST=1]
[*]If I boot Ubuntu from the grub, the next boot the grub is still there. 
[*]If I start Windows from the grub, the next boot the grub disappears and Windows starts without asking. 
[/LIST]


[LIST]
[*]With the grub gone and the boot forced to windows: 
[/LIST]

[LIST=1]
[*]I can use Super Grub2 Disk to boot Ubuntu: Boot Manually->Grub extract entries->Ubuntu. 
[*]Next boot, after turning off the computer after entering Ubuntu with Super Grub2 Disk, grub is back. 
[*]Again, If I boot Ubuntu from the grub, the next boot the grub is still there and if I start Windows from the grub, the next boot the grub disappears and Windows starts without asking. 
[/LIST]

Anybody knows how to repair it? I searched the internet and I can not find my specific case

Thanks

---

### Post by oldfred on 2018-03-27
Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[URL="http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789"]http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789
[/URL]
 One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589) 
    

But Sony violates UEFI standard that says NOT to use description as part of boot. And only valid description is "Windows Boot Manager".
That is for default setting. Some live with manually selecting as you are doing on each reboot.
You may be able to set hard drive or fallback boot entry as default in UEFI. But Ubuntu cannot be set as a default as description does not match.

---

### Post by rubenstobbart on 2018-03-28
I've used easyUEFI to deactivate Windows entry and now works fine.

Changing the Windows path to the GRUB (Obuntu's path) also works.

Moving the entries order is useless, Windows change it every time.

---

