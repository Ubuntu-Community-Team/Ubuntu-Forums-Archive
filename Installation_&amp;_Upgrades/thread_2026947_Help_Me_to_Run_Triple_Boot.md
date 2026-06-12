---
title: "Help Me to Run Triple Boot"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by bheemamahesh on 2012-07-16
At Present i ve Windows 8 & Windows Server 2008. Now i want to install Ubuntu and run "triple boot"

when i install linux after windows server 2008 and windows 8, it didn't show windows in boot menu only linux will show there(i installed grub loader to sda)

i think this problem can overcome by installing "grub loader to /boot partition" (while trying to install grub loader to /boot linux installation crashed)

Help me out from this issue. I want to run Triple boot Windows Server 2008, Windows 8 & Ubuntu

---

### Post by jtarin on 2012-07-16
Do you still have a Windows loader present in the MBR? If yes install Grub to "/" partition of Ubuntu. When that is done look to my signature and install EasyBCD in the first Win OS on your drive. Use EasyBCD to modify your Win bootloader to boot all three.

---

