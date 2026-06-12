---
title: "Boot-Repair problems"
date: 2018-02-05
forum: MINT
---

### Post by adamhff on 2018-02-05
Hello! So i have an install of linux mint and I decided to install windows 8 next to it. It installed fine, but now I am getting into GRUB booting issues, so I started using "Boot-Repair" to make my life easier ([https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)) It works, but there are multiple instances of windows to boot into and after I select one and boot to windows - I then reboot and the boot list disappears completely! Am I just missing something important?

Thanks in advance!

---

### Post by oldfred on 2018-02-05
Moved to Mint sub-forum.

Post link that the Summary Report from Boot-Repair creates. You posted link to Boot-Repair.

Are both systems in UEFI boot mode or both in BIOS boot mode?
What brand/model system?

---

### Post by adamhff on 2018-02-07
Link: [http://paste.ubuntu.com/26536565/](http://paste.ubuntu.com/26536565/)

Both are in UEFI I believe.

Thanks!

Oops! The brand/model is HP Compaq 6300

---

### Post by oldfred on 2018-02-07
HP violates UEFI standard  that says NOT to use description as part of UEFI boot.
And only valid description with HP is "Windows Boot Manager". 
But various work arounds.

Most use a UEFI hard drive entry or "fallback" entry which for internal drives is the same as external drives or /EFI/Boot/bootx64.efi.
Since you now have bkpbootx64.efi, it looks like Boot-Repair already copied shimx64.efi to bootx64.efi. The backup is probably just a copy of Windows .efi boot file.
Some also use rEFInd as another way to boot which seems to work on HP and others with similar issues.

       Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds, same as link in my signature below:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019) 

    
       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 
            HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681) 
            HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

