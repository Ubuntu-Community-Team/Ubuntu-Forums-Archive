---
title: "Removing Ubuntu - cannot remove GRUB and computer insists on booting from USB"
date: 2012-04-16
forum: Installation &amp; Upgrades
---

### Post by mju4t on 2012-04-16
I decided I no longer wanted Ubuntu, and wanted to remove it from my system.  

Here is what I did (and I realize now after doing research that this was not the best way to go about it).

I wiped the Ubuntu partition and then combined the new free space with my Windows partition.  That messed up GRUB, and when I boot, the GRUB Rescue Error prompt appears saying "no such disk".  I believe this is because GRUB is looking for the grub files that I deleted.

I researched online and found that this is fairly common, and all I had to do was create a windows recovery disk and boot from that.  I booted into the windows recovery, and it said that I had errors that were causing my PC from starting up, and wanted to repair it.  I accepted, it attempted to repair.  Upon finishing, I restarted, and the GRUB rescue is still there.

I then tried booting back into windows recovery , navigated to command prompt, and tried the /FixMBR, /FixBoot, /ReBuildBCD commands.  They all completed successfully, and my computer STILL will not boot normally.

The only way that it boots is if I have my USB stick inserted.  I can see the recovery option at the bootload screen, but also my main windows partition.  I cannot use the computer without having the stick in.  Once the computer is running, I can remove the stick - but I need it to boot, because I cannot get rid fo the grub recovery.

Does anybody know what I can do?  I am at a loss!  Thank you in advance for your help!

---

### Post by darkod on 2012-04-16
I am not sure how windows recovery exactly works, because in most cases the restore partitions are designed to wipe the hdd and do the factory state restore.

Since you can boot with the usb stick, boot into your win7 and make the rescue cd. That cd is bootable and can do the bootloader restore. I think the option is in Backup & Restore tool.

After that boot from that cd and try the command line procedure again, if that doesn't work, try the auto repair process that the cd should offer.

See if that can install the windows bootloader. This is in reality windows issue, it hasn't got much to do with ubuntu.

---

