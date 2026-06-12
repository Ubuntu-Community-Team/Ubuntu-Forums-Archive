---
title: "32-bit UEFI - after install bootia32.efi must be chosen manually in EFI menu to boot"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by ronniepinsky on 2014-11-26
Edit:  Problem solved.  The trouble was with "efibootmgr".  Apparently when Linux is installed to a disk on an EFI system, "efibootmgr" is run to update EFI configuration in some flash memory on the motherboard.  This particular EFI system will also auto remove any "links" to non-working OS specific folders in the EFI partition and also auto remove "links" that do not point to the right GPT partition.  When "efibootmgr" is ran correctly, you should see the OS entry in your EFI menu.  This was the correct command for this system:
```

sudo efibootmgr -c -w -l \\EFI\\ubuntu\\bootia32.efi -p 1 -d /dev/mmcblk0

```

-c is for create
-l is for the loader file
-p is the partition number
-d is the full device
I don't know why or if the -w option is needed but there you go.

-----------

I have installed Ubuntu 14.10 64-bit on an internal disk.  The only thing I have changed in the startup files is adding bootia32.efi to the ubuntu folder in the EFI partition.  Without it, the system won't boot because it is 32-bit UEFI.  Unfortunately, I have to choose bootia32.efi on every boot from the EFI boot menu.  To boot from USB I have to add the bootia32.efi file but I don't have to specify it on startup.

Is this a firmware bug or an installation problem somewhere?

---

### Post by grahammechanical on 2014-11-26
From the little I know about this I would say it is common practice to boot Linux from the EFI boot menu. It is not so long ago that it was impossible to run Linux on a machine where the EFI was 32 bits and not 64 bits. I am not referring to the CPU, here but the size of the boot system firmware So, the fact that this is at all possible is a marvel in itself even if it is not as we would wish it to be.

I suspect that the issue is something to do with bootia32.efi and Grub not being connected in some way. But I am out of my depth here. I have just done a little research and am now even more confused.

Regards.

---

### Post by oldfred on 2014-11-26
Do not know much about 32 bit UEFI.
It seems it was a version to try to prevent Linux from installing to keep it as a Windows only system. Linux did not have a working 32 bit UEFI. 
But even though UEFI was 32 bit, hardware was still 64 bit so a kludge by the vendor to cripple a system to make it less usable by the owner. And trap them into Windows.

 Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)
Packard Bell ENME69BMP InsydeH2O  or Gateway LT41P04u
32-bit UEFI Support Proposed For Ubuntu Linux
[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE)
Bay Trail -The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
But someone has it partially working:
[URL="http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html"]http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html
[/URL] Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)
Some new 64 bit low cost systems with 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

[URL="http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html"]
[/URL]

---

### Post by ronniepinsky on 2014-11-26
I suppose I should clarify further.  More specifically, when I choose the "ubuntu" option in the EFI boot menu then Windows just boots.  I have to choose "load an EFI file" from the EFI boot menu, then navigate the to the ubuntu folder in the EFI partition and manually choose bootia32.efi.  This is tedious, but normally would not be a problem but this is a tablet.  The EFI options work with touch ** except ** in the "load an EFI file" portion.  This means I would need to attach a USB keyboard just to boot ubuntu and on every restart.

As far as the reasoning for the 32-bit firmware, officially it is because these devices ship with 1-2 GB of RAM and cannot make much use of 64-bit Windows and also because 64-bit Windows actually uses more RAM than 32-bit Windows.

Also, I have already read most of the links mentioned but will look through them again.

---

