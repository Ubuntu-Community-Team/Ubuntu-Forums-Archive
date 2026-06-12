---
title: "Selected Boot Device Failed - E5550 - Ubuntu"
date: 2016-02-23
forum: Installation &amp; Upgrades
---

### Post by Geeko299 on 2016-02-23
Hi everyone,

I got a new laptop Dell E5550 with ubuntu install. After trying to install win7 and kali (Dual-Boot) without success, I would like to reinstall ubuntu or kali. I made the necessary changes in the BIOS (AHCI SATA, Legacy boot and no security boot) and installed ubuntu again with new partitions (with boot_grub partition first). Right now, I can't boot on Internal HDD I have this error message "Selected Boot Device Failed ...", I can only boot using usb install. Could you help please ? Thanks.

---

### Post by oldfred on 2016-02-23
Did you install in UEFI or BIOS mode? Flash drive usually can boot in either mode.  How you boot installer is how it installs.
Actually three boot modes, UEFI with Secure Boot, UEFI, or BIOS/Legacy/CSM. Secure boot is an option with UEFI boot.
And then have you set UEFI to boot by default in that same mode?

Best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by yancek on 2016-02-23
>  I would like to reinstall ubuntu or kali. 

If you are having trouble installing Ubuntu, I would suggest you forget about installing Kali to your drive.  First, I'm sure you are aware that it is not meant  as a Desktop computer for average users and is designed only and specifically for computer forensics testing.  If you are interested in testing Kali or learning computer forensics, you would be much better off putting it on a flash drive.  Detailed instructions at their site below.

[http://docs.kali.org/downloading/kali-linux-live-usb-install](http://docs.kali.org/downloading/kali-linux-live-usb-install)

---

### Post by Geeko299 on 2016-02-23
Thanks for your replay.

UEFI mode is off. I set BIOS/Legacy as option and I can boot and install ubuntu using the flash drive and new partitions.
The ubuntu install is successful but when I reboot using "Internal HDD" I have the error message "Selected Boot Device Failed ...".
I'll try to install win7 and check if it's iso image (failed download) or HDD connection issue. 
I don't want to open the laptop and check the device connection, it's still on warranty.

---

### Post by Geoffrey_Arndt on 2016-02-23
Ok Geeko299,    before you go off reinstalling Win7 etc., suggest you re-read OldFred's post - especially the part on boot-info summary report.

As you started off with a great advantage over many (Ubuntu pre-installed) . . . . perhaps it would have been better and safer to test Kali on a usb flash-stick or a Virtual Machine  . . in fact, why not install Win7 via Virtual Box?

---

### Post by Geeko299 on 2016-02-24
I'm not interested by win7, I am using ubuntu since 10 years.
I'm trying a clean ubuntu install then I'll use boot-repair if still have the same issue.
I'll let you know. Thanks

---

### Post by Geeko299 on 2016-02-25
Hi, I made a clean ubuntu install using flash drive and it works.
Thanks all of you for your support.

---

