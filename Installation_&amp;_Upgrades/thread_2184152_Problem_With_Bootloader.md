---
title: "Problem With Bootloader"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by outsidethetext on 2013-10-27
I have a Dell XPS 13. Which appears to be having problems with the bootloader.
I get the following error on boot
 file '/boot/grub/x86_64-efi/normal.mod' not found
I have spent most of the day trying to fix this, using the grub repair tool to no avail. The report that is now issued is at
[http://paste.ubuntu.com/6314982/](http://paste.ubuntu.com/6314982/)
Can anyone help with this?

---

### Post by outsidethetext on 2013-10-27
Update: I used gparted, then tried repairing grub and this is now my current status
[http://paste.ubuntu.com/6315842/](http://paste.ubuntu.com/6315842/)

---

### Post by oldfred on 2013-10-27
I do not see anything wrong. 
Do you get to grub menu and then error? Or before menu. With one system you may have to hold shift key from UEFI/BIOS boot until menu appears. And some with UEFI have to use escape key.

If at grub rescue does this work?
       configfile (hd1,gpt1)/efi/ubuntu/grub.cfg

    
Some other Dell. Many seem to be very similar even if different model. Only options like Ultrabooks then complicate it a lot.
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
[http://ubuntuforums.org/showthread.php?t=2179297](http://ubuntuforums.org/showthread.php?t=2179297)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
[SOLVED] Dual-boot Ubuntu/Windows8 on Dell XPS 8500, need just a few advices with info on UEFI settings
[http://ubuntuforums.org/showthread.php?t=2151494](http://ubuntuforums.org/showthread.php?t=2151494)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

---

### Post by outsidethetext on 2013-10-27
After playing around some more and doing some of the things above. I got it working. Although I am not sure what made it work this time. I do see the grub menu at boot though and have to select to boot to Ubuntu. Thanks.

---

