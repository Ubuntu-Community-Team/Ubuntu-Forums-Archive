---
title: "Lenovo error 1962: no operating system when installing ubuntu (single OS)"
date: 2016-07-20
forum: Installation &amp; Upgrades
---

### Post by rinehartm on 2016-07-20
I inherited several Lenovo m91p machines that currently have Ubuntu installed: I can log into one, but the others are all locked and so I am trying to reinstall a fresh copy of ubuntu on each of the others.  The machines are identical, so I know that ubuntu *can* be installed successfully.

Issue: I keep getting Error Code 1962: No operating system found whenI try to boot

Attempting: Ubuntu 14.04 LTS 64-bit install
Partition settings: I have tried several based on forum posts I have found, but the most "vanilla" is probably what I have included here in the pastebin.  One single partition on the HDD: /dev/sda1

Attempted solutions:
1) wiped out the HDD partition and fresh installed Ubuntu
2) after fresh install, I tried booting from live USB (works) and running boot-repair (tried recommended repair settings)
3) tried turning off "quick mode" in the BIOS boot settings
4) tried changing boot options in BIOS from [AUTO] to [EFI] to [LEGACY] ... still the same error

[http://paste.ubuntu.com/20107757/](http://paste.ubuntu.com/20107757/)

I really don't know what's going on here, but somewhere between the BIOS and GRUB, something is not working.  Any help would be greatly appreciated!

Thanks!

---

### Post by oldfred on 2016-07-20
In UEFI boot mode, grub only installs to ESP - efi system partition on sda.
I have put second/third installs on sdb and flash drive and no matter what I say it overwrites my main working install's /EFI/ubuntu on sda. The installer even says installing to sdb, but overwrites sda. (I quickly learned to back up the ESP.)

So create a 300 to 500MB FAT32 partition with boot flag on sda. UEFI wants if first but Windows makes it second or even third partition, but still nearer the beginning of drive.
Then use Boot-Repair to reinstall grub completely using advanced options.

Some Lenovos also need /EFI/Boot/bootx64.efi to really be a copy of shimx64.efi. Boot-Repair can also do that if you tick/check the "use the standard EFI file" in advanced options.
 [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by rinehartm on 2016-07-27
No luck.  I set up a 1GB FAT32 partition with a boot flag (/dev/sda1/) and then installed ubuntu 14.04 onto /dev/sda2 (ext partition format).  Then I used boot-repair and went into advanced options as recommended.

I'm still getting the 1962 error :(

Any ideas?

Here's the most recent pastebin after the above installation attempt: [http://paste.ubuntu.com/21161662/](http://paste.ubuntu.com/21161662/)

---

### Post by oldfred on 2016-07-27
Have you tried turning off Secure Boot in UEFI?

In Boot-Repair run it with this:
       
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options.

---

