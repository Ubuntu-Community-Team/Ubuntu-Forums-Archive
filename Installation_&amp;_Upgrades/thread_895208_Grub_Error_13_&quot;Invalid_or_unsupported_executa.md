---
title: "Grub Error 13: &quot;Invalid or unsupported executable format&quot;"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by nicholasbgr on 2008-08-20
Hi. I was dualbooting vista and ubuntu for a long time, but today I needed to use a software that only works on windows xp. So I created a new partition and instaled on it. After that I restored the grub loader and tried to boot on windows vista. The problem is: i get the error Grub Error 13: "Invalid or unsupported executable format" and windows xp is not showing up. Can someone help me fixing windows vista entry and creating a new one for XP?

This is what I got on fdisk -l:
> Dispositivo Boot Início Fim Blocos Id Sistema 
/dev/sda1               1        2117    17004771   83  Linux 
/dev/sda2   *        2118        2366     2000092+  82  Linux swap / Solaris 
/dev/sda3            2367        5764    27292866    7  HPFS ou NTFS  **[VISTA PARTITION]**
/dev/sda4            5765        9729    31848862+   f  Win95 (LBA) Partição Extendida 
/dev/sda5            5765        8643    23125536    b  W95 FAT32 
/dev/sda6            8644        9729     8723263+   7  HPFS ou NTFS   **[XP PARTITION]**


And this is my menu.lst:
> 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a5acf5fa-00cb-4bf9-acfb-9d42d592312d ro quiet splash locale=pt_BR 
initrd		/boot/initrd.img-2.6.24-19-generic 
quiet 
 
 
# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda2 
title		Windows Vista/Longhorn (loader) 
root		(hd1,0) 
savedefault 
makeactive 
chainloader	+1 


---

### Post by Sef on 2008-08-20
It looks like problem is is that Windows likes to be on the first partition.  I don't have the time now to research how to fix your problem, I will post something later if time permits.

I had a similar problem and ended up reinstalling Windows and Ubuntu.

---

