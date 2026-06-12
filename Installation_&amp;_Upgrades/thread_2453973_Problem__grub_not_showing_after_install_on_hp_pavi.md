---
title: "Problem : grub not showing after install on hp pavilion"
date: 2020-11-20
forum: Installation &amp; Upgrades
---

### Post by tytoalba2 on 2020-11-20
Hello,

I've disabled windows fast boot, and followed this : [https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/)

(basically : 
In Windows command prompt, copy and paste the command below:

 bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi)


But it's still not working. Grub menu doesn't show up, and the laptop boots straight to windows! Really annoying. Any idea of a solution?

---

### Post by dino99 on 2020-11-21
There are many wiki/howto to install ubuntu alongside windows, like that one:
[https://fossbytes.com/install-ubuntu-20-04-with-windows-10-dual-boot/](https://fossbytes.com/install-ubuntu-20-04-with-windows-10-dual-boot/)

---

### Post by ajgreeny on 2020-11-21
See **Boot-Repair** in my signature and follow the instructions there to run the Boot-Info script.
Do not run the default repair; just run the script and post back here the Pastebin link you see so our experts can look and hopefully find a solution for you.

---

### Post by Raffles727 on 2020-11-21
You must also make sure secure boot is disabled in the BIOS/UEFI

---

