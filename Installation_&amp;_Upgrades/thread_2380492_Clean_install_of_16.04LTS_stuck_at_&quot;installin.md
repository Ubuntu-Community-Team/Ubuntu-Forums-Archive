---
title: "Clean install of 16.04LTS stuck at &quot;installing grub2&quot;"
date: 2017-12-18
forum: Installation &amp; Upgrades
---

### Post by Rudolf_Fischer on 2017-12-18
Hi all
I am an ubuntu noob (coming from windows), so please bear with me, if I am asking something obvious.
I have an installation with two SSDs
- first one contains UEFI Windows Bootloader and two instances of Windows (Server 2012R2 and Windows 10 Home)
- second one contains Ubuntu 16.04LTS
This setup used to work, booting to either windows or ubuntu through Grub

After some problems I deleted the two ubuntu partitions on the second SSD (from Windows) and tried to reinstall ubuntu. However the install stops at "Installing Grub". I can then reboot the system by pressing the reset button. The system will boot through Grub to ubuntu. But obviously the installation did not finish and ubuntu does not work properly (i.e. sofware update gets stuck after a few seconds).
I tried running boot repair, but it also gets stuck on installing Grub.

How can I get rid of the obviously screwed up remenants of Grub to do a nice clean install of ubuntu?
Thanks a lot for any help

---

### Post by mastablasta on 2017-12-20
delete ubuntu, restore windows boot loader (this should overwrite GRUB), then try again.

---

### Post by kansasnoob on 2017-12-21
Are you sure you booted the Live DVD/USB in EFI mode? It's possible that you tried to reinstall in non-EFI mode and grub is freaking out. If booted in EFI mode the boot screen will look like a grub boot screen (black background w/white text) rather than the iso-linux boot screen.

---

### Post by Rudolf_Fischer on 2017-12-21
I am sure, I booted in EFi mode, otherwise I could not have started the ubuntu installation process.
Next I tried repairing the Windows Boot Sector using bootrec /fixmbr, but got an access denied message. I figure the whole installation was somehow screwed up.
My Windows acronis backup gave me a "the restore of this backup will not boot message".
So I ended up reinstalling Windows. In a few days I will pull a new backup and then try reinstalling ubuntu on the second disk and do a second backup.

---

