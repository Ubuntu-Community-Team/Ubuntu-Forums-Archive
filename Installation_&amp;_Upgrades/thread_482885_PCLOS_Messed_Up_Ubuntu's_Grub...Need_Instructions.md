---
title: "PCLOS Messed Up Ubuntu's Grub...Need Instructions"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by sbjaved on 2007-06-24
Installed PCLOS after Ubuntu Feisty to check it out. Ubuntu was nowhere in the PCLOS Grub upon reboot, so manually added "vmlinuz" and "initrd" in Grub Menu via a Boot Configuration GUI. Problem is that Ubuntu loads but gets stuck during loading trying to find root dir. So my Ubuntu is lost. Any idea how to get it back?

---

### Post by Pumalite on 2007-06-24
> **sbjaved said:**
> Installed PCLOS after Ubuntu Feisty to check it out. Ubuntu was nowhere in the PCLOS Grub upon reboot, so manually added "vmlinuz" and "initrd" in Grub Menu via a Boot Configuration GUI. Problem is that Ubuntu loads but gets stuck during loading trying to find root dir. So my Ubuntu is lost. Any idea how to get it back?

Pop in Ubuntu's Live CD and try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by sbjaved on 2007-06-25
Thankyou Pumalite.

By the way i figured out an easier way. Open the menu.lst file of your Ubuntu installation (in my case loacted at /ubuntu/boot/grub/menu.lst) using kwrite or any text editor you prefer. Copy the **/boot/vmlinuz-2.6.20-16-generic** in the **Image** option of the Boot Configuration GUI (PCLOS Control Center) and **root=UUID=eeddb350-210b-4f74-b9ad-307e84654948 ro quiet splash** (these values are specific to your machine) to **Append** option. Hit "OK" and it will modify the boot loader. Ubuntu is in bussiness!

---

