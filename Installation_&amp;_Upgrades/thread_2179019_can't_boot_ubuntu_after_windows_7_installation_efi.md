---
title: "can't boot ubuntu after windows 7 installation efi"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by sigend on 2013-10-06
Hey there,just installed win7 uefi to my system.Then i used boot-repair(one click repair ) to restore grub menu.but when i try to boot ubuntu (13.04) i end up with black screen.Windows boot just fine.
secure boot is disabled.Ubuntu were uefi installed.
[http://paste.ubuntu.com/6200368/](http://paste.ubuntu.com/6200368/)
here is boot-repair review.

What i did is not so smart since i havent really fully understand mbr vs gtp grub etc  :D:D

---

### Post by oldfred on 2013-10-06
You did run the rename which may or may not be required. I think Boot-Repair suggests that fix for some systems that do not need it, but that is not related to your main issue. Line 977 in your report:
       Save and rename /mnt/boot-sav/sdb3/boot/efi/EFI/Boot/bootx64.efi (/mnt/boot-sav/sdb3/boot/efi/EFI/Boot/bkpbootx64.efi)

If you want to undo that.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

If you are not booting Ubuntu that may be a video issue. If you get grub menu have you tried nomodeset.
What video card/chip do you have for video?
I have to add nomodeset with my nVidia. At grub menu press e for edit, scroll to linux line and replace the quiet splash with nomodeset.
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[URL="https://help.ubuntu.com/community/BootOptions"]https://help.ubuntu.com/community/BootOptions

      [/URL]
 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Editing the GRUB 2 Menu During Boot
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

     [URL="http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it"]http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it

[/URL]

[URL="https://help.ubuntu.com/community/BootOptions"]
[/URL]

---

