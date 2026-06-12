---
title: "Install of KUBUNTU on HP Envy 17-j130ea Laptop"
date: 2014-03-18
forum: Installation &amp; Upgrades
---

### Post by archcynic on 2014-03-18
I've just installed Xubuntu 13:10 on an new HP Envy Laptop (UEFI with 'secure mode'). There were a few stumbles along the way so I thought I'd record the issues / solutions for google to find...
[B]
Issue: Could not access 'BIOS' menu to adapt boot order[/B]
Description: With Live USB inserted, reboot and press ESC, F1 F9, F10. The following texts were shown and process stalls/hangs (no BIOS menu shown)

[LIST]
[*]ESC...pause startup 
[*]F9... Change Boot Device Order 
[*]F10...BIOS setup options, 
[/LIST]
Solution: Remove USB drive. On reboot & F<key> press, message shown briefly before BIOS menu appears.

**Issue: Install from Live CD - Screen Blank**
Description: Boot into live CD. Select 'Install' from Grub menu. Screen goes black and does not 'return'.
Solution: Increase brightness by pressing appropriate key (F3). Screen was not really 'black' just shown with zero brightness.

**Issue: Win 8.1 not detected**
Description: No option given to install in dual boot config. 
Solution: Use Win partitioner to shrink Win 8.1 partition (min 450GB). Manually partition. Create EXT4 partition for linux from remaining space allowing Swap partition of 20GB. No option to change the /boot/efi partition so leave as is.

**Issue: Message "grub-efi-amd64-signed" failed to install into /target"**
Description: Installation without network connection. At end of installation, process is aborted with above message. No grub installed.
Solution: Repeat installation with network connection and install completes. Message seems due to missing dependencies which would be downloaded automatically if done with network connection. 

**Issue: Grub-efi not present. **
Description: No Grub shown on boot. Boots to Win 8.1
Solution: Needed boot-repair - told to switch out of secure boot mode. Installing with the BIOS setting for 'secure mode' active must have screwed up the grub-efi install though no message/warning shown. Needed to (1) switch off secure mode in BIOS menu. (2) Run Live CD in 'try UBUNTU' mode. (3) sudo apt-get install boot-repair (4) run boot-repair and reboot.

After all that Xubuntu is installed in dual boot mode and it flies.

Thanks to all who put effort into keeping the (X)Ubuntu show on the road. This stuff is not simple.

---

