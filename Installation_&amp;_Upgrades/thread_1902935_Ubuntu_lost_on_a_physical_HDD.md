---
title: "Ubuntu lost on a physical HDD"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by paulcliman on 2012-01-01
I have two HDDs in a computer. The master drive has Windows 7 installed.
I installed UBUNTU from CD and requested it go on the second (Slave) HDD.

Now, when I boot the machine it goes straight to Windows and the UBUNTU drive is not even seen now .
How can I get some sort of dual-boot option to appear when I turn on this computer, please ?
Any ideas ?
Thanks in anticipation...

---

### Post by darkod on 2012-01-01
The windows bootloader does not detect other OSs and does not create a dual boot menu. Your computer is still booting from the windows hdd as first option.
Go into BIOS and set it to boot from the other hdd and it will use the grub2 bootloader installed by ubuntu on that hdd. Grub2 will have a menu with ubuntu and windows.

---

### Post by Mark Phelps on 2012-01-01
IF you had both drives connected when you installed Ubuntu to the second drive, then Darko is correct -- the GRUB menu should have entries for both OSs.

If the drive was NOT connected, however, when you boot from the second (Ubuntu) drive, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB menu.  You should see it find the presence of "Windows 7 (Loader) " on your drive as it does that.

---

### Post by paulcliman on 2012-01-02
Many thanks to you both for your help.
Much appreciated.

---

