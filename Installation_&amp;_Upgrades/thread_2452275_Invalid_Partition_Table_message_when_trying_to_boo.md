---
title: "Invalid Partition Table message when trying to boot from USB"
date: 2020-10-19
forum: Installation &amp; Upgrades
---

### Post by roguejedi2 on 2020-10-19
I'm trying to install Ubuntu on a Dell Latitude E5440 that has Windows 10 on it.

The problem is I encounter the message I mentioned (Invalid Partition Table!) when I try to boot from the USB.

I tried updating the BIOS drivers, disabling Legacy boot options, enabling and disabling secure boot, and other tricks I found on other forums.
The thing is, most people who had this problem encountered it after installing the OS.

Much appreciated if you could help me out.

---

### Post by CelticWarrior on 2020-10-19
Welcome.

How exactly did you burn the USB?

And for the sake of accuracy and better understanding moving forward with the troubleshooting, you have **UEFI**, not BIOS. BIOS and UEFI are both firmwares but BIOS isn't used since almost a decade ago. UEFI replaced BIOS. Surely you can find even today mentions of "UEFI BIOS" by same vendors but it's only due to the familiarity of the old term.

Now that we have the terminology down the settings you mentioned - Legacy/CSM/"BIOS" mode and Secure Boot - are all characteristic of the new UEFI and absent of the old BIOS.
Start with the UEFI settings that should be and troubleshoot from there: UEFI only > disable Legacy/CSM with Secure Boot OFF; also disable Fast Boot.
In Windows disable Fast Startup (optional for Windows alone but any advanced Windows user actually recommends disabling it anyway and it must be disabled for dual-booting).

And now back to the beginning: Please describe how you did the USB media.

---

### Post by oldfred on 2020-10-19
The live installer is often a hybrid DVD/flash drive configuration that does not use a standard partition table. 
If from live installer then error can be ignored.
If from system, then have you changed to AHCI?

Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Older Dell seemed to need legacy on, but still select UEFI to boot (without secure boot). Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.
Windows AHCI driver install:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

---

### Post by roguejedi2 on 2020-10-20
> **CelticWarrior said:**
> Welcome.

How exactly did you burn the USB?



Turns out I wasn't burning the USB correctly.

Thanks for the tip. Problem solved. I managed to install Ubuntu but now have a different issue.
The laptop will connect to any other WiFi network except my home router's. Guess I'll have to open another issue thread :-( .

---

