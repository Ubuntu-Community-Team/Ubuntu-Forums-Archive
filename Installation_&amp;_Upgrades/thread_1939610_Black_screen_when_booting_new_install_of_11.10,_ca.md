---
title: "Black screen when booting new install of 11.10, cannot access GRUB menu"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by Vpc on 2012-03-12
I installed 11.10 on my desktop but just get a black screen after the BIO screen when I try to boot it. I cannot access the GRUB menu to try: 

> Press and hold down Shift key from Bios screen until see the Grub menu. Highlight the first entry, press “e” to edit it. Navigate to words “quiet splash”, delete them and type “nomodeset” in their place (without quotes). Press Ctrl + X to continue boot.
Once on the desktop, go to System > Administration > Additional Drivers and activate the recommended drivers and the problem should go away for ever.

Holding the shift key from the BIOS screen doesn't work.

---

### Post by Vpc on 2012-03-16
> **Vpc said:**
> I installed 11.10 on my desktop but just get a black screen after the BIO screen when I try to boot it. I cannot access the GRUB menu to try: 



Holding the shift key from the BIOS screen doesn't work.

Running Boot-Repair (installation instructions: [http://ubuntuforums.org/showpost.php?p=11136267](http://ubuntuforums.org/showpost.php?p=11136267)) solved the problem. In Boot-Repair I chose Advanced options->GRUB options. I selected 'Add a kernel option:" and selected 'acpi_osi=' from the drop down menu beside it to make the kernel not respond to osi queries (as suggested here:[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) because some bioses contain fixes for specific Windows versions that may not work with other OS's).

I clicked on 'Edit GRUB configuration file' which loaded /mnt/boot-sav/sda1/etc/default/grub. In this file I set GRUB_CMDLINE_LINUX_DEFAULT="" , removing it's 'quiet splash' value to display the boot messages when booting ('splash' enables the splash screen with condensed text output and 'quiet splash' results in just the splash screen image being shown), put a # in front of GRUB_HIDDEN_TIMEOUT to display the grub menu and set GRUB_TIMEOUT=10 to give the user 10 seconds to make a selection. I don't recall but these changes may already have been made from editing /etc/default/grub while running 11.10 on my pendrive (where I got an error message when I tried 'sudo update-grub' after the editing).
More details on Grub2: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 

You can also adjust the amount of time to 'Unhide boot menu' in the Advanced options->Main options. This was left at the default value of 10 seconds. 'Reinstall GRUB' was also selected by default. In Advanced options->GRUB location, the default settings were sda1 for 'OS to boot by default' and 'Place GRUB in all disks (except USB disks without OS)' was selected. 

I clicked 'Apply' and restarted the computer after Boot-Repair finished running. I changed the boot order of hard drives in the BIOS (my usb pen drive was listed as a hard drive so I would adjust the order according to which drive I wanted to log into) then pressed 'Enter' at the Grub menu. After the boot messages, the login screen appeared. The system also automatically boots after the Grub menu appears for 10 seconds.

---

