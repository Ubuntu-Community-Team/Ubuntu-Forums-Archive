---
title: "ASUS no ACHI available"
date: 2024-02-21
forum: Installation &amp; Upgrades
---

### Post by John_Rose on 2024-02-21
Hello,
I bought in 2020 an ASUS VivoBook 17" CPU X712FB. The motherboard has just been replaced by the constructor and all drivers are up to date.
I want to install Ubuntu 2022.04 LTS as dual boot with the installed Windows 11 Home Edition.
When I load my Live Boot USB and begin the installation, it says that RAID has been detected and has to be changed to AHCI to install Ubuntu.
I followed the instructions at [https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/) but when I make the Registry changes (or if not) the BIOS does not give me any choice but the installed Intel RST 17.00.3720 RAID Driver which it seems from the device manager depends on the Intel Chipset SATA/PCIe RST Premium Controller. There is apparently no AHCI available.
This is strange because I have two other approximately contemporary (one older 15", one younger 14") ASUS VivoBooks on which I installed Ubuntu in dual boot without difficulty.
I see one other question on ACHI issues preventing Ubuntu installation ([https://ubuntuforums.org/showthread.php?t=2475898&highlight=ASUS+ACHI](https://ubuntuforums.org/showthread.php?t=2475898&highlight=ASUS+ACHI)). It seems to be a different problem but the recommendation was to run Windows under WSL or alternatively run Ubuntu Virtual Machine under Windows. There seemed however to be some negative thoughts on this, and no feedback from the poster on what he did and how it worked. I do not know either of these tools, but the idea of depending on MicroSoft is not very enticing.
Could someone advise whether it is really impossible to install a dual booted Ubuntu on my machine, and if not the advantages and disadvantages of the above other options?
Thanks and best regards,
    John

---

### Post by #&amp;thj^% on 2024-02-21
Have you looked in your bios change>> "Rapid Storage Technology (Intel RST)" this to **AHCI**, Ubuntu will recognize your disk.

---

### Post by John_Rose on 2024-02-21
I have no choice in bios. It gives only the title "Intel RST 17.00.3720 RAID Driver" and allows you to click to see that characteristics of the single non-RAID drive "PCIe 1.0 INTEL model SSDPEKNW512G8, 476.0 GiB". By the way I have both FastBoot and SecureBoot turned off. When I make the two Registry changes specified in [https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/) (3 to 0 in Start and StartOverride for two Registry values) they are changed back to 3 when Windows reboots.

---

### Post by #&amp;thj^% on 2024-02-21
Yep I've heard this many times (resets those values)

I would try to boot windows

Then run via (admin) CMD:
```


bcdedit /set {default} safeboot minimal
```

You do have a Restore disk though right?
If not get one first.
Then when Windows see's ahci drives you can revert back with:
```
bcdedit /deletevalue {default} safeboot
```

---

### Post by tea for one on 2024-02-21
> **John_Rose said:**
> I have no choice in bios.
Do you have an option in the UEFI settings:-
Change SATA mode to AHCI where the default is RAID or Intel RST

---

### Post by John_Rose on 2024-02-21
I made a restore USB and Windows said that it terminated correctly, and also have created a restore point which might possibly help in case of a BSOD, but I guess I should note all of the info on the system and the OS in order to get another copy from ASUS or Microsoft if the worst happened.

My bios interface is called Aptio Setup Utility by American Megatrends Inc. I do not see "UEFI settings" there, but under "Advanced" I have "Intel Rapid Storage Technology" (already described above) and "SATA Configuration" which gives two choices: AHCI !!! and "Intel RST Premium with Intel Optane System Acceleration" (default). So I guess I should select AHCI, reboot and be ready with my restore USB in worst case? I guess that I should make the recommended Registry changes before going into bios.

I looked very quickly (as a technological kindergartner) at WSL and at virtualization tools like **VirtualBox**, **VMware** and **Microsoft Hyper-V**. WSL is a Windows application that will give only a Linux command line interface and thus a non-starter for me. The virtualization tools are complex to tune and will be slow sharing resources with the host OS in the case of a low-end system like mine (Core 5, 8 GB of RAM); I also wonder whether I would have access to the disk storage of the host OS (now I am keeping most of my data in ntfs partitions to ensure better compatibility with the real world of Windows users). The dual boot, which I have been using for a dozen years, seems despite its inherent risks to be the best bet for me - do others have a different take?

---

### Post by oldfred on 2024-02-21
My Dell is 11th Gen Intel.
I made a mistake when installing 22.04 as I forget to change to AHCI and turn off Secure Boot as we normally suggest.
But it installed.
I found it was using the Intel® VMD driver for the NVMe drive which is only drive in system.
But then when booting from my external USB3/NVMe adapter it seems to have added the AHCI driver.

From ixni, only one drive and not RAID, but using Intel RAID driver:
```
RAID:
  Hardware-1: Intel Volume Management Device NVMe RAID Controller driver: vmd
    v: 0.6 bus-ID: 0000:00:0e.0
Drives:
  Local Storage: total: 476.94 GiB used: 135.2 GiB (28.3%)
  ID-1: /dev/nvme0n1 vendor: Western Digital model: PC SN530 NVMe WDC 512GB
    size: 476.94 GiB temp: 40.9 C
```

---

### Post by tea for one on 2024-02-22
> **John_Rose said:**
> Intel RST Premium with Intel Optane System Acceleration
Intel Optane is no longer developed
[https://www.intel.com/content/www/us/en/support/articles/000091826/memory-and-storage.html](https://www.intel.com/content/www/us/en/support/articles/000091826/memory-and-storage.html)
> **John_Rose said:**
> do others have a different take?
Assuming that you have a separate Optane disk, it can be replaced with a larger one.
Plenty of info on the internet (both positive and negative)

Perhaps, explore the idea of dual booting with each OS on a separate disk?

---

### Post by John_Rose on 2024-02-22
Thanks **tea for one,** you are the one who gave me the hint to enable me to solve this problem. Dual boot installed without further problems. For my little home installation no need for better equipment or near-simultaneous access to Ubuntu and Windows. I am spending perhaps 99% of my log-in time on Ubuntu, Windows is just for rare legacy applications and to give the possibility to better understand and fix problems which may arise with ntfs.

---

