---
title: "Unable to boot after clean 24.04 install on Thinkpad"
date: 2024-09-30
forum: Installation &amp; Upgrades
---

### Post by jayjay2024 on 2024-09-30
Hi, I was on 22.04 on my Lenovo Thinkpad T420 and then decided to upgrade to 24.04. For some reason the upgrade failed in the middle of the process and then when I tried to boot I was just taken to a command prompt.

After searching for solutions I gave up and tried a live USB stick which appeared to work so I went ahead with a clean install erasing the old installation. However, now I can’t boot - it’s as though there is nothing to boot from. When I insert the live USB stick it is able to boot from that. I’ve tried to search for a solution but frankly all this stuff about grub, UEFI etc is beyond me. Anyway, I managed to run boot-repair from the live USB and the pastebin is here [https://paste.ubuntu.com/p/FRGzFK9pNR/](https://paste.ubuntu.com/p/FRGzFK9pNR/)

I would greatly appreciate any help.

---

### Post by oldfred on 2024-09-30
It looks like your system is after 2012, when Microsoft required vendors to install Windows in UEFI boot mode to gpt partitioned drives.

But you elected to install in the pre-2012 BIOS boot mode.
How you boot install media, UEFI or BIOS is then how it installs.

With UEFI you have to have an ESP - efi system partition FAT32 with boot,esp flags. You do not have that partition, so cannot easily convert to UEFI boot. Only real difference with UEFI & BIOS installs is whether you have an ESP or bios_grub partition when on gpt partitioned drives. You have bios_grub partition for BIOS boot in gpt drive.
(No one should be using the old MBR(msdos) partitioning unless old system that has to have Windows in BIOS boot mode.)

You may just need to go into UEFI settings & change settings to allow Legacy/BIOS/CSM boot mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

---

### Post by jayjay2024 on 2024-09-30
A lot of that went over my head but the key thing I took away was that “How you boot install media, UEFI or BIOS is then how it installs”. I guess I had booted the install media using BIOS when it should have been UEFI. So I changed a BIOS setting from something like ‘support UEFI and BIOS’ to UEFI only, inserted my live USB stick, and performed a fresh installation. Now I’m booting straight into the UI and everything is as expected &#128513;. Thanks!

---

