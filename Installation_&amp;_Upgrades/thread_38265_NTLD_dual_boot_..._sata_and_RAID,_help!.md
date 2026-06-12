---
title: "NTLD dual boot ... sata and RAID, help!"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by mgorbach on 2005-05-30
Ok ... i have complicated setup with 2 SATA drives in a RAID configuration (motherboard RAID), and a third SATA drive i just installed for linux. Linux refused to install before i removed the other 2 drives, but once i did it installed correctly. I then fixed up the bootloader (GRUB) so i can boot ubuntu while all 3 drives are connected using the motherboard boot menu (lets me select what drive to boot). What i want to do now is use NTLDR to load GRUB and boot linux. 
I used DD to copy the first bytes of my root partition can emailed the file through to the windows partition. Copied from /dev/sdc, this is my root partition. The problem is, when i add the file to the boot.ini and choose it on the menu, i get the word GRUB and a total freeze. 
Can i please get some help getting linux booting?

My menu.lst entry looks like so

[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /KERNEL=LOGOOS.EXE
c:\ubuntu64.mbr="Ubuntu Linux AMD64 Hoary Hedgehog (Grub)"

---

### Post by mgorbach on 2005-05-31
anyone?

---

### Post by mgorbach on 2005-07-27
i would love some help on this ... no one knows?

---

