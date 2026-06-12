---
title: "GRUB : update-grub doesn't detect Windows 7 anymore"
date: 2016-05-07
forum: Installation &amp; Upgrades
---

### Post by magowiz82 on 2016-05-07
Hi,
today I upgraded kernel to 
4.4.0-22-generic #39-Ubuntu
since then all my "sudo update-grub" doesn't detect windows 7 OS , it happened to me in both home computers, what should I check ?
I have to say that since upgrade from 16.04 I didn't have this issue, only today, I don't know if it's the kernel package of some other that has some bugs, I would exclude it is an hardware/bios issue, since the issue came out in two different pc, and I didn't change windows installation or BIOS configuration.
How can I check what went wrong this time ?

---

### Post by oldfred on 2016-05-07
Just to confirm your configuration.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

Usually os-prober does not find Windows because it is either hibernated or needs chkdsk.
Windows 8 and later is always hibernated as its fast start is a partial hibernation.

---

### Post by magowiz82 on 2016-05-07
Hi Oldfred,
first of all thank you, I followed the instructions in the link you posted, installing boot-info into running (installed ubuntu), and here it is the link with the information reported :
[http://paste2.org/kcDzpnOw](http://paste2.org/kcDzpnOw)

For what I understood it doesn't seem to be any error on windows partition, but perhaps I didn't read the whole log.

---

### Post by oldfred on 2016-05-08
It shows Windows NTFS partitions with typical boot files in both sda1 & sda2. Grub looks for those boot files bootmgr & BCD to know partition for Windows boot. Windows uses boot flag which is on sda1.

If you use Boot-Repair's advanced mode and choose Windows & repair, it should install a Windows type boot loader. Or use your Windows repair disk and fixMBR. Then does Windows boot, or perhaps sda1 or sda2 or both need chkdsk? 
Once Windows boots use Boot-Repair to restore grub to MBR.

---

### Post by magowiz82 on 2016-05-08
> **oldfred said:**
> It shows Windows NTFS partitions with typical boot files in both sda1 & sda2. Grub looks for those boot files bootmgr & BCD to know partition for Windows boot. Windows uses boot flag which is on sda1.

If you use Boot-Repair's advanced mode and choose Windows & repair, it should install a Windows type boot loader. Or use your Windows repair disk and fixMBR. Then does Windows boot, or perhaps sda1 or sda2 or both need chkdsk? 
Once Windows boots use Boot-Repair to restore grub to MBR.

Thank you oldfred for your support, I didn't know about boot-repair iso, I burnt boot-repair iso and done reccomended repair on both machines, it worked, on one of the two, on first start, windows launched CHKDISK, the only defect is that now grub's script, upgrade-grub, doesn't detect memtest86+ image anymore... for now it's ok, at least I can boot without problems in both OSes.

Thank you very much again

---

### Post by magowiz82 on 2016-05-09
I also noticed this issue also on my work laptop, using boot-repair solves, but I think, somehow it was introduced a regression.... in 3 PCs I installed new kernel and all of them "losts windows menu entry" and I needed to repair boot with suggested software.... In all of them, after repairing, memtest86+ doesn't get detected.

---

### Post by oldfred on 2016-05-09
Do not know why it would be missing. It is a script as part of all the scripts update-grub runs.

Post this:
sudo ls -l /etc/grub.d

---

### Post by magowiz82 on 2016-05-09
Hi oldfred, here it is the content of /etc/grub.d as you requested :
```

$ sudo ls -l /etc/grub.d 
totale 72
-rwxr-xr-x 1 root root  9791 apr 16 00:00 00_header
-rwxr-xr-x 1 root root  6258 mar 15 19:08 05_debian_theme
-rwxr-xr-x 1 root root 12261 apr 16 00:00 10_linux
-rwxr-xr-x 1 root root 11082 apr 16 00:00 20_linux_xen
-rwxr-xr-x 1 root root 11692 apr 16 00:00 30_os-prober
-rwxr-xr-x 1 root root  1418 apr 16 00:00 30_uefi-firmware
-rwxr-xr-x 1 root root   214 apr 16 00:00 40_custom
-rwxr-xr-x 1 root root   216 apr 16 00:00 41_custom
-rw-r--r-- 1 root root   483 apr 16 00:00 README

```

---

### Post by oldfred on 2016-05-09
Mine is identical except for your missing memtest.

> -rwxr-xr-x 1 root root  1992 Jan 28 06:44 20_memtest86+

Unless a hidden backup or in root's trash, I do not know how to get that back except by a total reinstall of grub. Boot-Repair can do that or just run from synaptic or command line a reinstall of grub. If BIOS package is grub-pc and if UEFI it is grub-efi-amd64. 
But if you manually edited any grub settings those would also be overwritten with new default copies, so back up those changes.

My 16.04 install is from daily and I updated to current 16.04. But date has not changed on memtest, but has on all other files. Is it not included in new installs? Mine could be left over from old daily version, or file just has not been updated?

---

### Post by magowiz82 on 2016-05-09
I was able to restore a copy of 20_memtest86+ and update-grub now produce the menu with both windows entries and memtest entry ..... Boot-Repair in mine case made me remove completely grub and then reinstall it.... is it possible that somehow, in new version of grub (shipped with 16.10) memtest script is not provided anymore ?

---

### Post by oldfred on 2016-05-09
If experimenting with 16.10 who knows. I have not installed it yet.

---

