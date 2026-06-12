---
title: "Install Windows 7 partitioned to Kubuntu"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by pokemondawg2 on 2013-03-05
Hi, I would like to install Windows 7 as a secondary OS, but I wouldnt know where to start. Can anybody help? Much appreciated, thanks. P.S. Running Quantal 12.10 :p

---

### Post by mastablasta on 2013-03-06
create an NTFS formated partition and then boot from win7 install disk. from there onwards search help on win7 forums.

---

### Post by pokemondawg2 on 2013-03-06
Ok, thank you. I will try that. What size should the partition be?

---

### Post by pokemondawg2 on 2013-03-06
Also, is the partition seperate to the other two?

[ATTACH=CONFIG]239842[/ATTACH]

---

### Post by gordintoronto on 2013-03-06
What do you have in sda1? If it were my system, I would backup everything, then move the stuff in sda1 to a folder in sda6, then reformat sda1 to ntfs.

---

### Post by oldfred on 2013-03-06
Windows likes to own system. So its normal install is a small 100MB hidden in Windows boot/repair partition and the main install. But it will install to one primary partition formatted NTFS with the boot flag. The usual minimum I have seen is 30GB, but Windows can consume space quickly. May also be a good idea to have another NTFS for shared data, so you can set the Windows system partition as read-only from Ubuntu.

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

