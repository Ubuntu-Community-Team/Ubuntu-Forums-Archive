---
title: "Not able to load windows."
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by raghavendran_te on 2009-11-26
I had windows XP installed already when I installed ubuntu 9.04. My windows, due to some problem later, had to be reinstalled. Because of that, my grub got deleted. I was able to access only windows then. Later, I followed the instructions to install grub. Now the grub shows both ubuntu and windows option, but when I select from the grub options to load windows, the grub simply restarts itself and presents me with the same options again. I am not able to load windows at all. What should I do?

Please help!!!

---

### Post by lemming465 on 2009-11-28
Please post the output from```
sudo -i
fdisk -lu
blkid
cat /boot/grub/grub.conf
```
and we can offer you more specific advice.  This is definitely solvable.

---

### Post by lemming465 on 2009-12-07
Your symptoms are consistent with overwriting the windows secondary boot loader with the grub secondary boot loader.  The boot process, extrememly oversimplified, runs MBR -> secondary boot loader -> boot menu -> OS-specific kernel loader -> live kernel.  Grub can load Linux directly; XP needs "ntldr" off your C:\ drive.  Assuming you have 5 partitions on 1 disk, say:

1: windows recovery
2: ntfs windows xp C:
3: extended
5: linux ext3
6: linux swap

Then what I'd do is use the windows recovery disk to reinstall the windows loader on the C: partition first.  Then use a live Linux CD to put grub on the MBR + the Linux partition.  Write back for more directions if that matches your situation.

---

### Post by presence1960 on 2009-12-07
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

