---
title: "No bootable devices found after BIOS update on Dell XPS 9370 (ubuntu preinstalled)"
date: 2021-05-06
forum: Installation &amp; Upgrades
---

### Post by per-wennman on 2021-05-06
After updating BIOS via the Software updater the system halt boot with the message "No bootable devices found". Tried BIOS utilites and run the BIOS update again, the update reported succesful both the problem remains. Downloaded and run Boot-Repair, but no success repairing. The Boot-Repair log is at [http://paste.ubuntu.com/p/JQDBbkTgMY/](http://paste.ubuntu.com/p/JQDBbkTgMY/)

I hope someone could give me some directions how to proceed trying to fix the problem.

---

### Post by oldfred on 2021-05-06
You show no drive, just USB flash drive.

Did UEFI update reset UEFI settings?
And then turn Intel RST/RAID back on. Check if still AHCI.
Otherwise check connections to make sure drive connected, both power & SATA port.

---

### Post by per-wennman on 2021-05-06
Checked that AHCI enabled, it is.  I'll check the connections tomorrow, but I had not tampered with any hardware before the BIOS update.

---

### Post by per-wennman on 2021-05-07
The connections to the sdd disk was also ok. I have tried a lot of tips how to solve this issue without success.  Maybe the only option is to reinstall Ubuntu but not sure if that will work since bios detects no disk?

Any tips on how to proceed would be appreciated.

---

### Post by tea for one on 2021-05-07
How does Software Updater update your BIOS (or is it UEFI)?

Is this some special Dell utility?

I've only ever seen UEFI updates via the UEFI set up pages themselves (although I understand that certain Lenovo devices can only update UEFI via Windows)

---

### Post by oldfred on 2021-05-07
If UEFI/BIOS cannot see drive, no software or operating system will see it. 
UEFI/BIOS scans system for drives & other hardware & writes that info to drive for operating systems to use.

I might also try a full cold boot, not warm reboot. That should get UEFI/BIOS to re-scan system.
Make sure system is totally shut down & all power removed, until restarting.

---

### Post by CatKiller on 2021-05-07
The other thing to check from having all your UEFI settings reset to defaults by the update is which mode you're booting in: UEFI or BIOS (also called "Legacy" or "Compatibility Support Module"). If you've installed in one and then try to boot with the other, the boot will fail with an error that it can't find the bootloader, since they are in different places in the different modes.

---

### Post by per-wennman on 2021-05-09
It´s a dell utility showing up in Software Updater. Therefore I thougt is was safe to up upgrade the BIOS.

---

### Post by tea for one on 2021-05-09
I would also have thought that a Dell utility appearing in the Ubuntu Software Centre would be safe.

This specific package is only available to Dell PC users i.e. it is not in any Canonical repository?

In effect, a Dell utility in Software Updater has compromised your Ubuntu OS pre-installed on a Dell XPS 9370.......???

Have you contacted Dell about this?

---

### Post by per-wennman on 2021-05-11
Since the computer was delivered with Ubuntu from factory I believe that there is a cooperation between Dell and Canonical as there is a repository at [http://dell.archive.canonical.com/updates/dists/bionic-dell/public/](http://dell.archive.canonical.com/updates/dists/bionic-dell/public/). I have never updated the computer by no other means than via the Ubuntu software update. Yes I have been in contact with Dell support, they could´t help me solve the issue, they  tried to sell me a support deal to send in the computer to fix it. Maybe signing a support agreement and sending the computer to Dell  is what I have to do to get this problem fixed.

---

### Post by tea for one on 2021-05-11
Can you not access the UEFI set-up pages with dedicated key for Dell?

If you cannot do this, then the alternative method is to boot into a live Ubuntu session and open a terminal:-

```
sudo systemctl reboot --firmware-setup

```
Hopefully, you may be able to double-check the UEFI settings?

---

