---
title: "Ubuntu only boots when manually selected in BIOS"
date: 2024-09-26
forum: Installation &amp; Upgrades
---

### Post by chrstphrknwtn on 2024-09-26
I'm a Mac person who has never owned a PC, but I'm familiar with unix-like systems as a developer. I have built a PC because I want to use NVIDIA cards.

My new system will only boot Ubuntu if I do a long-press reset and then select the Ubuntu installation via Boot Override in BIOS.

The system does not have any other OS installed, I do not have a copy of windows.

Here's the Boot Repair output: [https://pastebin.ubuntu.com/p/VRg5Zm5dsy/](https://pastebin.ubuntu.com/p/VRg5Zm5dsy/)

I appreciate any tips to get this system booting.

Hardware:
- Asus Proart z790 Creator WIFI
- Intel Core i7 12700k
- No GPU installed
- 64gb Crucial Pro RAM (2x32gb)

---

### Post by chrstphrknwtn on 2024-09-26
I should add that when restarting from BIOS or Ubuntu when manually selected, the system never gets past the "VGA" debug LED shown on the motherboard, the motherboard manual says this is indicative of an integrated graphics issue with the CPU, however the system works just fine when manually booted via BIOS.

I've tried disabling IOMMU:
[https://askubuntu.com/questions/814851/using-intel-iommu-on-keeps-system-from-booting](https://askubuntu.com/questions/814851/using-intel-iommu-on-keeps-system-from-booting)

However this has no effect.

---

### Post by oldfred on 2024-09-26
Is fast boot set in UEFI settings.
Full cold boot should reset system to recognize any changes.

Also UEFI may have setting on what video mode you use. CPU's or video card.
See graphics configuration, but not idea which setting is correct for your system.

Do you have latest UEFI firmware from Asus? And if SSD latest firmware for it?
Compare to vendors support site
sudo dmidecode -s bios-version
udisksctl status

---

### Post by chrstphrknwtn on 2024-09-26
Fast Boot is disabled.
Firmware is up-to-date (verified as directed)

I did switch the "Primary Display" setting BIOS which appeared to work the first time on reboot, however when the system is booted cold, or reset from Ubuntu, the motherboard debug LEDs get to RAM (2nd LED) and then go out, and nothing more occurs.

The only way the system is bootable is to do a long-press reset to force a Safe Boot into BIOS.

---

### Post by maintech123 on 2024-09-26
This may not be of any help to anyone else but originally I had the same issue. After several attempts I downloaded the iso for the prior release. Just to try it. It installed and worked correctly. I then did a full-upgrade. I'm now running the latest with no issues. Most likely I did something I was not aware of which made it work.

---

### Post by chrstphrknwtn on 2024-09-26
After pulling my hair out, where nothing worked... it ended up being a faulty RAM stick causing the system to not POST.

Like I mentioned above, I'm a life-long Mac user, so excuse this noob error.

Thanks for your help oldfred and maintech123.

For anyone else who lands here looking for answers for the Asus Proart z790 Creator WIFI motherboard, I removed the faulty RAM stick and it booted just fine into Ubuntu 24.10 with factory default settings (BIOS 2504).

---

### Post by yancek on 2024-09-27
>  it booted just fine into Ubuntu 24.10 

You are aware that by using 24.10 now you are volunteering to test it for Canonical.  Although this is not a software problem, any problems you have with the software should be reported to them so the developers can make changes.  Not sure if you are familiar with the release cycles for Ubuntu but ,24.10 will only be supported for 9 months.

---

