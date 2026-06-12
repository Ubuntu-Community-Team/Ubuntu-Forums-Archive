---
title: "&quot;Fatal Error&quot; on Ubuntu-Installation because of GRUB (dual-boot)"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by steigweis on 2005-07-30
ubuntu version: 5.04

- CPU: Athlon 2000+
- Grafikkarte: Geforce 4Ti

Hello! I have some trouble installing Ubuntu on my machine. I use WinXP on the c:\ patition and now I want to have a second OS, that is Ubuntu on the u:\ patition of the same drive. This is my first Linuxinstallation, so please be kind O:) 

First of all, my partitioning:

Drive 1 (Seagate Barracuda 80 GB IDE):
c: winXP - ntfs (BOOTFLAG)
d: XPswap - ntfs
e: XPprogramme - ntfs
g: eigene daten - ntfs
u: UBUNTU - ext3 /root (6,5 gb)
v: /home - ext3 (8 gb)
w: swap(ubuntu) (800 mb)



And now, the problem: 
The trouble occurs during the Ubuntuinstall, when GRUB is trying to install into MBR before my WinXP partition. Then the message "Fatal Error" is displayed. GRUB could not be installed in MBR. Sadly, no further information.

I need GRUB as a dualbootmanager and want to solve the problem but have not found any useful information ao far. Do you have a clue, what goes wrong with GRUB? Is that a problem of partitioning, bios, boot-flag, wtf?

I want my ubuntu  \\:D/ 

Thanks in advance....




Btw: bootsequence virus protection is DISABLED

---

### Post by heimo on 2005-07-30
For me the solution around grub related installation problems (which were probably caused by lack of knowledge or sata-drives), was to use expert mode and install lilo instead of grub. At the very beginning of booting install CD you have the screen with some text and you can type 'expert' and press enter to use expert mode. It gives you more control over what will be done during install (needs some more work, too) and at the end when grub would be installed, you can choose to install lilo.

It's been some time since I installed Ubuntu, I can't remember the details. Could be actually that I used server install mode. But the keypoint is - easy way around this *could* be using lilo. However, don't rush to do anything that you can't recover from.

---

### Post by steigweis on 2005-07-30
[QUOTE=heimo]For me the solution around grub related installation problems (which were probably caused by lack of knowledge or sata-drives), was to use expert mode and install lilo instead of grub. At the very beginning of booting install CD you have the screen with some text and you can type 'expert' and press enter to use expert mode. It gives you more control over what will be done during install (needs some more work, too) and at the end when grub would be installed, you can choose to install lilo.

It's been some time since I installed Ubuntu, I can't remember the details. Could be actually that I used server install mode. But the keypoint is - easy way around this *could* be using lilo. However, don't rush to do anything that you can't recover from.[/QUOTE]

Unfortunately, the LILO installation failed as well. The normal ubuntu installation routine offers LILO alternatively, btw.

---

### Post by heimo on 2005-07-30
When it fails, can you change to different virtual console (by entering ctrl+alt+F2,F3 ...), in one of those should be output of those commands and maybe some valuable error messages. Did the lilo installation give exact same error?

---

### Post by steigweis on 2005-08-04
Problem solved. Partition Magic was the cause. The installationsetup could not read the /root partition, because linux has recognized the linuxpartitions as ntfs (funny PM mess). 
I had to format the linuxpatitions once again with cfdisk and then ubuntu had properly installed GRUB. :)

---

