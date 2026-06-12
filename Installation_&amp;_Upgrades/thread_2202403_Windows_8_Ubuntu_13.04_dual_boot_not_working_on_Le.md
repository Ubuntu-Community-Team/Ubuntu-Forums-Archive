---
title: "Windows 8 Ubuntu 13.04 dual boot not working on Lenovo G505s"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by fusionstrings on 2014-01-29
I have Lenovo Essential G505s laptop with 1TB HDD and 8 GB ram. I t has AMD A8 64 bit processor. BIOS is set to boot UEFI first. HDD is set to legacy boot and I have Windows 8.1 installed in legacy mode. I have successfully installed Ubuntu 13.04 after creating manual partitions.

After reboot it directly booted to Windows. Then I ran boot repair. Here is the URL i got after running boot repair. [http://paste.ubuntu.com/6834525/](http://paste.ubuntu.com/6834525/) . Now I am getting nothing but a purple screen while rebooting system. Fast boot and secure boot (no option for secure boot in BIOS) is off.

---

### Post by fantab on 2014-01-29
Probably your BIOS should also use 'legay/csm' mode first.
There seems to be an issue with your Extended Partition, use [Fixparts]("http://www.rodsbooks.com/fixparts/") to fix it.

What graphics card do you have? It it is not Intel then use '[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' kernel parameter during boot.

---

### Post by oldfred on 2014-01-29
BootInfo shows this, so you need the latest AMD drivers and 13.10 may work better as 13.04 has expired:

> *******lspci -nnk | grep -iA3 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Richland [Radeon HD 8550G] [1002:990d]
Subsystem: Lenovo Device [17aa:3804]
Kernel driver in use: radeon
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Trinity HDMI Audio Controller [1002:9902]

 EOL Notice: Raring (13.04) will be End of Life on January 27, 2014
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

---

