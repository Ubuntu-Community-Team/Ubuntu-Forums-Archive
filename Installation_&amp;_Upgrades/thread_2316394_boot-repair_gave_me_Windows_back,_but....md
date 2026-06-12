---
title: "boot-repair gave me Windows back, but..."
date: 2016-03-07
forum: Installation &amp; Upgrades
---

### Post by dawynn on 2016-03-07
I could use some help here.

[http://paste.ubuntu.com/15324155](http://paste.ubuntu.com/15324155)

I have three OS's on this computer.  Windows 10 + 2 installations of Linux.  Upgrade on one Linux system to 16.4 made Windows unavailable.  Used boot-repair and can now get into Windows, but grub is missing, so can't get into either Linux OS.  Any suggestions?

PC uses UEFI, but bios does not allow me to specify a specific partition for bootup.  Tried the admin command prompt trick in Windows with no luck.

Thanks!

---

### Post by yancek on 2016-03-07
You have mixed and MBR install with Grub code in the master boot record with an EFI install which has both windows and Ubuntu files on your EFI partition, sda3.  You are using GPT partitioning so you need windows installed UEFI.  If windows is installed UEFI then Ubuntu must be also.  You also have a BIOS boot partition for Ubuntu which is only needed if you use GPT and do not use UEFI so that isn't needed.  Unfortunately, that's about all I know but I'm sure someone will come along and explain how to repair.

---

### Post by oldfred on 2016-03-08
With Acer you have to set a supervisory password in UEFI and set trust.
Not sure if you then have to reset, on update to files.

       Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

There is only one /EFI/ubuntu and that uses a grub.cfg to find full grub.cfg in your install. Last install overwrites the /EFI/ubuntu. If you look at the /EFI/ubuntu/grub.cfg you will see it refers to last install. Boot-Repair's summary report does not show that file.

---

### Post by dawynn on 2016-03-09
I tried to follow what I could understand of that, but my bios did not completely match up.  Still booting into Windows, even after a couple more attempts at boot-repair.  Latest report: [http://paste.ubuntu.com/15333954/](http://paste.ubuntu.com/15333954/)

Any suggestions?

---

### Post by oldfred on 2016-03-09
Report does not show whether or not you have set password in UEFI and then set "trust" on grub/ubuntu files. 
Have you done that.
Many of the linked posts above discuss details on how to do that. 
Do not have Acer so can only repeat what users who have actually done it recommend.

---

### Post by dawynn on 2016-03-10
I want to thank both responders for their help.  However, my experience did not match that of previous users.  I was never able to find where in the bios I could specify a UEFI password, or "trust" the ubuntu files.

I went to the Acer site and found the latest Bios for my particular machine, and upgraded the machine.  I went into the Bios, and set up the machine to boot into the Windows boot manager.  That picked up the grub menu from my second Linux install and I now have access to all three systems.

I know there was some struggle when I first built this machine, and again with the 16.04 upgrade.  I'm not sure that my troubles are over, because the grub menu I found was from my 15.10 system (not the system I used during the last Boot Repair), but my system is functional for now.  At this point, I really can't provide any helpful how-to's for others as I'm feeling like my system is more cobbled together than really functioning correctly.

---

