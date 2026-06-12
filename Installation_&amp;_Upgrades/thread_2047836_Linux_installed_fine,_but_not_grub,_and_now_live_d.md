---
title: "Linux installed fine, but not grub, and now live distributions won't boot either!"
date: 2012-08-25
forum: Installation &amp; Upgrades
---

### Post by Seadog01 on 2012-08-25
Hello everyone,

I'm a longtime linux user and evangelist, but installation (grub2 in particular) is not, shall we say, my forte.  So if you have any advice about the following, give it to me slow...

I'm trying to install ubuntu on my new computer.  Important features of it include 128GB OCZ Vertex 4 SSD, and an Asus Z77 Sabertooth motherboard.

Windows 7 was installed and is working perfectly, so all my hardware and connections and so forth seem to be working properly.  I next tried to dual-boot with linux.  I put 12.04 on a flash drive, did the whole repartitioning and install thing, rebooted, and tried to set up the windows bootloader with EasyBCD.  I now have an option to boot linux in the windows bootloader, but it just dumps me to the grub commandline.

The usual fix for that seems to be to fire up the live version again, and reinstall grub manually.  Trouble is, both the live versions I've tried (Lubuntu and Mint -- I'm embarrassed to say I've lost the original drive) won't boot, and also dumps me to the grub commandline.

So, any idea why a live flash drive won't boot properly?  It sometimes complains about a missing init file, but you'd think that problem wouldn't be the same across distributions...  I should also add that throughout this adventure, windows continues to work fine.  Thanks!

---

### Post by Old_Grey_Wolf on 2012-08-25
How did you create the Live USB, on Windows or Linux, using pendrivelinux, unetbootin, etc.?

---

### Post by Seadog01 on 2012-08-25
In windows, with pendrivelinux.  It generally works pretty well.

---

### Post by Old_Grey_Wolf on 2012-08-26
Do the live USBs boot on another computer?

---

### Post by oldfred on 2012-08-26
With a Z77 motherboard you have the additional complication of UEFI or BIOS modes. Which mode is Windows installed in & then you have to install Ubuntu in the same mode. Which mode you boot installer USB/CD in, is how it will install. Both Windows and Ubuntu from  the UEFI menu should show UEFI/efi or BIOS/legacy/AHCI or something other than UEFI as the two choices.

If first partition is efi then you are installed in UEFI mode. And if drive is gpt and you can boot, it has to be UEFI as that is the only way Windows will boot from a gpt partitioned drive.

Post this:

sudo parted /dev/sda unit s print

---

