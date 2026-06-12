---
title: "No root file system is defined install error freezes install"
date: 2020-09-23
forum: Installation &amp; Upgrades
---

### Post by goggins on 2020-09-23
Trying to install 20.04.1 LTS from a thumb drive onto a new Dell XPS running Windows 10 512 G SDD and 1T HDD. Once I got it to boot thr thumb drive I ran it off of the thumb for a while and then said install.  On Screen 5 it says it will install on /dev/sda and then, when I hit continue it says "No file system is defined please correct from partitioning menu and freezes.  There is no functining partitioning menu on that or any prior screen  What's up and what can I do about it?

nothing on that screen seems amenable to change except the box marked change. If I click on it, the screen rapidly collapses into nothingness.

---

### Post by oldfred on 2020-09-23
Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Older Dell seemed to need legacy on, but still select UEFI to boot (without secure boot). Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

What model XPS?

---

### Post by goggins on 2020-09-23
Not planning on dual boot, never liked windows, XPS 8940.  Install screens say need secure boot for third party drivers, which will be unavailable later -- is that true, that it's now or never for them? I'm still running from the thumb, so I guess I have to reboot and look for updates, hoped for a work around, oh well.

---

### Post by oldfred on 2020-09-24
Many later come back and want Windows to play game or run a required app that is not available in Linux. Or want to later sell system and buyer only wants Windows.
Best to then make a full backup of Windows if totally erasing it.

If you really want UEFI Secure Boot and need proprietary driver for video or Wi-Fi, then you have to provide your own UEFI Secure Boot key. Ubuntu cannot verify that third party drivers are secure. A user can if they believe it is secure.
Most turn off UEFI Secure Boot, for now. In future that may change.

---

### Post by goggins on 2020-09-26
Made brand new thumb drive using start-up disk creator and 20.04 LTS iso. Machine is UEFI with PTT, which I left as is but
1) Turned off secure boot
2) turned off fast boot
3) changed SATA setting to AHCI
installed into 512 meg ssd using whole drive; /dev/nvme0n1 -- partition#1 ESP & partition #2 ext4 (all automatic, selected no special features like LVM)

It is now running plain vanilla 20.04 LTS, so I'm marking this as complete/answered.

---

### Post by oldfred on 2020-09-26
Glad you got it working.

Many prefer a smaller / (root) and use rest of drive as /home or data partition(s).
And use  HDD as a backup location and/or data partition.

---

