---
title: "GRUB error"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by calvinfreakme on 2010-09-06
Earlier i had a ubuntu 9.1 installed under dual installation along side windows xp...bt day before yesterday...i deleted d ubuntu drive frm windows. 

i whn i boot the system...it says  "GRUB ERROR. CANNOT FIND ANY PARTITIONS".  plzz help me...i knw i hav a dne mistake by deleting d ubuntu drive. 


plzz suggest me a solution!!

---

### Post by androiddev on 2010-09-06
This is because GRUB had overwritten Windows' boot loader. What you'll need to do is put in your Windows XP disc and run these two commands "fixmbr" and "fixboot". This will rewrite the Windows boot loader and you'll be able to get back into Windows.

The other way is to boot from the Ubuntu disc and reconfigure GRUB to point only to your Windows XP installation.

Check out this link to reinstall GRUB:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by presence1960 on 2010-09-06
If you deleted ubuntu and want to run only windows there are two ways to fix the MBR so you can boot right to windows without GRUB.

1. Boot the ubuntu Live CD, go to the desktop. Open a terminal and run ```
sudo apt-get install lilo
``` Ignore the warnings. This will install lilo to the Live CD session.

Next in terminal run ```
sudo lilo -M /dev/sda mbr
```

Reboot without the Live CD and you will boot right to windows provided you did not mess up windows prior to the above operation.

2. See [here]("http://ubuntuforums.org/showthread.php?t=1014708"). Scroll down to the paragraph which is your version of windows.

---

