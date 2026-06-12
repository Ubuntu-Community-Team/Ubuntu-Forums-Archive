---
title: "Acer Laptop - Ubuntu 16.04/Win8.1 Dualboot always launching into win"
date: 2016-06-14
forum: Installation &amp; Upgrades
---

### Post by ricoow on 2016-06-14
Hello everybody,

I am getting desperate now. I am trying to make a Dualboot on one HDD on my Acer Aspire V3-772G laptop.
Disabled all the Win 8 fast boot and hibernation settings, have the Bios in UEFI mode (not legacy), bios safe mode disabled and installed Ubuntu 16.04 using the following settings:

100MB ext4 /boot
100MB BiosBoot
20GB ext4 /
8GB swap
remaining ~76GB ext4 /home

I assume having these two 100MB boot things might be overkill but it was the only way I managed not to crash grub installation during the Ubuntu install.
However I never get an option to choose Ubuntu or Windows whilst booting.
I have ran a boot-repair using my USB live disk and it errored. ([Pastebin]("http://paste2.org/9pEKkbf")) Also note worthy that it said Locked-ESP detected.
It also shot me an error after entering the fourth command that you have to execute in the terminal during br.
```
Errors were encountered while processing:
 grub-efi-amd64-signed
 shin-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
If you require more information, just let me know!

Question is: How can I get the dual boot to work? I've tried multiple tutorials but none has worked what so ever and I can't seem to find a good answer to the Locked-ESP problem
Many big thanks in advance to the golden answer!

Edit: Additional Info - F12 during boot brings me to the selection of bootables, only shows Windows Boot Manager (live usb was unplugged)

---

### Post by oldfred on 2016-06-14
In UEFI boot mode, you must have the ESP - efi system partition FAT32 300 to 500MB with boot flag. (You can get by with 100MB as that is what Windows has used).
If in BIOS boot mode you need a 1 or 2 MB unformatted partition with bios_grub flag.

I normally configure both on new drives as first two partitions

Most desktops do not need the separate /boot partition. That is used by some server or server type installs with RAID or LVM or full drive encryption with LVM.

I would convert your first two partitions to one FAT32 with boot flag as ESP and reinstall in UEFI boot mode.

But Acer is one vendor that requires you to set a supervisory password and enable "trust" on the efi boot files.
Some threads mention downgrade of UEFI, but newer ones say newest Acer UEFI works, so make sure you have newest UEFI from Acer.

       Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

### Post by ricoow on 2016-06-14
Thanks oldfred, I think I have found what I need to get this trust thing fixed. I will try this now and comeback here with the result.
Does the fat32 partition need to be on the very first 300MB of the HDD? Or does any 300MB suffice?

---

### Post by ricoow on 2016-06-14
Question:
What is the situation with the third-party software?
It tells me to turn off UEFI Secure Boot, but then I would be unable to follow the steps to get my efi trusted.

Can I install 3rd party software and disable secure boot later on? Or will that screw up my trusted efi file?

---

### Post by ubfan1 on 2016-06-14
Usually any 300M partition should suffice, but I'd put it near the beginning of the big terrabyte disks, just in case.
You should be able to enable/disable secure boot any time, but since the Acer "trust" business is vendor specific, who know what interaction it has.  Third party software, unless it is a bootloader should not be affected.

---

