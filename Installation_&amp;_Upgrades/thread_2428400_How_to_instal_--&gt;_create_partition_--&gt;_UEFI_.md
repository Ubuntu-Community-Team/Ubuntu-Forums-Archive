---
title: "How to instal --&gt; create partition --&gt; UEFI / Legacy --&gt; FAT32 --&gt; Boot"
date: 2019-10-03
forum: Installation &amp; Upgrades
---

### Post by logibash on 2019-10-03
Hello All, I have maybe simple question, but as the situation show not for me, how to instal Linux ubuntu?

Details:
I have two disk and I need two systems for each one.
First SSD disk 512 GB has factor installed Windows 10 Pro Workstation, and there is stars under UEFI settings.

I bought second disk Dysk M2 PCIe NVMe 256GB for Linux Ubuntu v. 18.04.3-desktop-amd64 LTS.

The problem is that uder settings UEFI I can not make choise the second disk during instalation Ubuntu. If I switch to Legacy, the problem is not appear, but after the instalation when it is done, I swith back to UEFI and I still can not see the system. 

I can run linux if I'm on Legacy switch, but then I have two system one WINDOWS is UEFI and Ubuntu is Legacy, It not make sense.

Please let sb explain me what is going on with this, because I try a lot with the partition combination, even though I create Partition FAT32 on the 256GB NVMe disk, this operation allow to see the disk when bios is UEFI but still it is not available during the instalation.

Machine: 
Dell Precision 5520 
Updated BIOS to the newest one

---

### Post by ubfan1 on 2019-10-03
Check out bugs 1396379 and 1173457.  Ignoring the sepcified UEFI bootloader location and putting them on the first one seen (sda).  You can manually copy all the files from the first disk's UEFI partition to the second one's, then it chould boot by selecting the device in USBI mode.  Install in USBI mode, then manually fix the (empty) UEFI partition.

---

### Post by oldfred on 2019-10-03
You may also need to update firmware for SSDs.

Possibly similar Dell, issues common across many models. Bigger differences if AMD or Intel based.
       Dell Precision 5530
[https://ubuntuforums.org/showthread.php?t=2420905](https://ubuntuforums.org/showthread.php?t=2420905)
Dell 5230 with 3 m2 drives.
[https://ubuntuforums.org/showthread.php?t=2406057](https://ubuntuforums.org/showthread.php?t=2406057)
Dell Latitude 5490 M.2 PCIe SSD
[https://ubuntuforums.org/showthread.php?t=2405822](https://ubuntuforums.org/showthread.php?t=2405822)

---

### Post by logibash on 2019-10-07
Thank you for answer, the problem has been solved.

I change at BIOS (UEFI) SATA operation mode from RAID to AHCI,
1) type at power shell as a administrator command: bcdedit /set safeboot minimal.
2) restart system, get into BIOS and switch the SATA operation mode, confirm and restart the windows, at the safe mode.
3) open Power shell and type: bcdedit /deletevalue safeboot
4) restart system, and everything works fine.

I don't know why Dell switch the SATA operation mode as a RAID defauld.

Answering for the suggestion by oldfred, I tried it and there was no any changed.

---

