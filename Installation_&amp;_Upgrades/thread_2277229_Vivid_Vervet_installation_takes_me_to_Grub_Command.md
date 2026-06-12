---
title: "Vivid Vervet installation takes me to Grub Command Line"
date: 2015-05-07
forum: Installation &amp; Upgrades
---

### Post by csete on 2015-05-07
I have an XPS 15 (9530) laptop that previously had Ubuntu 14.10 installed, booting in insecure UEFI mode.  I decided I wanted to do a scratch installation of 15.04 to that machine.  After installation on reboot, I was taken to the Grub command line rather than a menu.  Poking around a bit, I've found that I can boot into Ubuntu if I choose the legacy SSD option in the BIOS boot menu, but that requires me to jump into the BIOS.  I attempted to run boot-repair, but it can't help me because I am running in legacy mode at that point.  This is a Dual Boot system with Windows 8.1, which is still working if I boot from the UEFI menu in the BIOS.  

I haven't really lost anything, but I'd like to get this thing booting correctly.  I did make a full backup of all of the partitions using partclone before I did anything, so I should have a valid EFI partition backup.  What is my best option?  Should I restore the EFI partition?  Should I boot from a live USB of boot-repair?  Is there yet another better option I'm not considering?

Thanks for help.
Craig

---

### Post by Bucky Ball on 2015-05-07
If you have Win8 installed in UEFI and Ubuntu installed in legacy mode, that is not going to go. Could you run Boot Repair again and get the bootinfo and post a link to that here, please, so we can see how your drive is currently set up?

You need to install both OSs in the same mode. If you're not too far down the track and the EFI partition is still there, might be easier to simply reinstall Ubuntu in UEFI mode.

---

### Post by csete on 2015-05-07
I guess I didn't realize I was installing from a different mode when I booted off of my external DVD drive.  Given that this is literally a completely fresh install at this point, one option would be to just reinstall it "correctly".  If I did that, how would I make sure I booted into UEFI mode from external media?

The system information is here:  [http://paste.ubuntu.com/11012080/](http://paste.ubuntu.com/11012080/)

---

### Post by Bucky Ball on 2015-05-07
This:

> The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.

Read the whole section at the very end of your bootinfo output. Seems you might have things right and you have changed to boot in legacy instead of EFI. Please get into the BIOS and have a look around for how to boot in EFI mode and do so. Let us know what happens then (does it boot directly to Windows?).

---

### Post by Bucky Ball on 2015-05-07
This:

> The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.

Read the whole section at the very end of your bootinfo output. Seems you might have things right and you have changed to boot in legacy instead of EFI. Please get into the BIOS and have a look around for how to boot in EFI mode and do so. Let us know what happens then (does it boot directly to Windows?).

The good news is the EFI partition is still there and the Ubuntu info is in there, so looking good. A wiser head might be able to see a problem, but nothing stands out here (although no expert). That would indicate, though, that you did install Ubuntu in EFI, but changed the disk back to legacy to boot. Wherever you did that is where you would find the setting to boot in EFI mode.

---

### Post by csete on 2015-05-07
I thought I *was* booting properly.  I think what is happening is that there is a menu item in my BIOS menu that is about booting the "mini SSD".  Using that menu option, Ubuntu will boot, but it is in legacy mode.  There are two options under UEFI mode "ubuntu" and "Ubuntu".  With secure boot enabled, the first one takes me to the Grub command line and the second gives me a signature validation error.  If secure boot is disabled, they both take me to the Grub command line.  So as things stand, I can only boot via legacy mode, but can't fix anything from there.

---

### Post by csete on 2015-05-07
I managed to get this fixed.  I followed the instructions from this page [https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/](https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/) to boot the system from the Grub command line from UEFI boot.  Once booted in that way, I was able to run boot-repair to fix up the system to boot correctly.

One thing I noticed was that installation ended up creating new partitions and my EXT4 partition moved from /dev/sda8 to /dev/sda10.  Any idea why it would have done that?

---

### Post by oldfred on 2015-05-07
Your summary report shows sda8 as the bios_grub partition which is only used by grub in BIOS boot mode. You can actually delete that partition if only booting in UEFI mode.

And sda10 is your ext4 install in that summary report. Did you reinstall before posting report?

---

### Post by csete on 2015-05-08
As I said originally, I did a reinstall from 14.10 to 15.04.  The summary report was done after that reinstall.  Before that upgrade, my ext4 partition had been sda8 and after it was sda10... The installer had created two new partitions that are likely unused.  With that said, I'm unlikely to make any changes to the partitions at this point since things are working and I'd rather just leave it alone.

---

