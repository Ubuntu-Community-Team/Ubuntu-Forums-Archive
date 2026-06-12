---
title: "Overwrote 16.04 with 18.04 on a W10/Ubuntu dual-boot machine, grub mayhem ensured"
date: 2018-05-03
forum: Installation &amp; Upgrades
---

### Post by mco404 on 2018-05-03
Hi guys,I wanted to install 18.04 LTS on a Windows 10 and  Ubuntu 16.04 dual-boot machine today. I somehow managed to destroy the bootloader on the way, and now I can only boot into grub-rescue. I tried to otherwise very handy tool Boot-Repair, but it is of no help, as the shell-commands provided by the program only end in error messages.Here is the paste of Boot-Repair: [http://paste.ubuntu.com/p/cj3zFH38BS/](http://paste.ubuntu.com/p/cj3zFH38BS/) If you could help me out, that would be great.

---

### Post by dino99 on 2018-05-03
Set the bootloader on a ext4 partition, not a ntfs one, then update-grub

---

### Post by oldfred on 2018-05-03
Since Windows is on sda and Ubuntu on sdb, best to leave Windows boot loader in MBR of sda, and use Boot-Repair's advanced options to choose sdb3 and MBR of sdb for grub boot loader. Then set BIOS to boot from sdb.

If newer Windows it may turn fast start up back on and then grub will not boot Windows, but you can directly from BIOS boot sda and Windows should still work or be able to get into its repair console.

---

### Post by mco404 on 2018-05-03
I was able to repair the Windows boot loader, thank you for your fast help!

For people in similar situations in the future: I set the "Restore MBR" option in the Main options and then I restored sda in the MBR Options menu.

---

