---
title: "Install to SD Card broke my hard disk's MBR"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by Tim Legg on 2010-05-19
Hello,

I installed Ubuntu 10.04-Desktop last night on an EEEPC 1005HA.  Actually I installed it on a 16GB SD card, so the Windows partition can be preserved.

For the most part, the install went okay except for a couple minor problems.

 * When I tell at the BIOS level to boot from the SD Card, absolutely noting happens.

 * When I tell it to boot from the hard disk, it now requires the SD card to be present.  Apparently, even though I told the installer to not install onto the hard disk, it decided in it's best interest that it would do so anyway, or at least in part (which I find is a very disturbing issue with the installer).  If the SD card is not present, I get this error.

error: no such device: c27f3579-7ee0-431a-ab42-4471071ce4b4.
grub rescue> _


If the card is present, it seems that the MBR on the hard disk uses the SD card in some respect and will ask me which operating system to boot.  I want to make this decision at the BIOS level because there will be other SD cards with other operating systems such as FreeBSD, Linux From Scratch, Windows 95 (just kidding!)


I need to get an idea on how to fix this broken installation.   Since I don't trust installers to work right, I used dd to copy the entire 250GB /dev/sda to a file on a USB hard disk.  So there is a backup.


Tim Legg

---

### Post by snowpine on 2010-05-19
Hi there, all you need to do (assuming Windows is the only OS on the interal hard drive?) is restore your Windows MBR. You should be able to find a how-to on Google, if not let me know which Windows version you're using and I'll look it up for you.

To prevent this issue in future installs, you have two choices: 1) when you get to the final step of the Ubuntu installer, click Advanced, and then you'll be able to choose where to install GRUB, for example /dev/sdb if that's the name of your SD card; 2) if that sounds too confusing, you can physically remove or disconnect the internal drive so that the SD card is the only drive attached to the computer at the time of installation.

I agree that the Ubuntu installer should always prompt where to install GRUB; I guess they don't want to confuse the noobs. ;)

ps and then of course you will need to install GRUB to the SD card. ;) [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by DrMelon on 2010-05-19
Evidently you didn't go into the expert section of the installer and prevent the bootloader from installing to your main disk.

---

### Post by Tim Legg on 2010-05-19
It is Windows 7 Starter that he has installed.

I have a complete image of /dev/sda on a USB hard disk.  About how many bytes is needed to be dd'd back to recover the MBR?  Is that still 512 or has it grown a bit larger over the years

> **snowpine said:**
> Hi there, all you need to do (assuming Windows is the only OS on the interal hard drive?) is restore your Windows MBR. You should be able to find a how-to on Google, if not let me know which Windows version you're using and I'll look it up for you.

To prevent this issue in future installs, you have two choices: 1) when you get to the final step of the Ubuntu installer, click Advanced, and then you'll be able to choose where to install GRUB, for example /dev/sdb if that's the name of your SD card; 2) if that sounds too confusing, you can physically remove or disconnect the internal drive so that the SD card is the only drive attached to the computer at the time of installation.

I agree that the Ubuntu installer should always prompt where to install GRUB; I guess they don't want to confuse the noobs. ;)

ps and then of course you will need to install GRUB to the SD card. ;) [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by snowpine on 2010-05-19
You don't have to image the entire /dev/sda back, just fix the MBR. :)

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

