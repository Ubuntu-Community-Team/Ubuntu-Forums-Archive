---
title: "Problem loading Ubuntu on Acer netbook"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by mcriegel on 2012-12-27
Hi there,
I have been wanting to experiment with the Linux operating system for a while so I decided I would load Ubuntu on my Acer Aspire One Netbook. It seemed to have installed completely, I even got to the Linux desktop once. However, now every time I try to boot up the machine, it gives me an error saying there's no Bootable Disk. I'm assuming this means I haven't installed it correctly. How can I get it back to the way it was, for example starting the machine in windows? Let me also add that the Alt + f10 solution only takes me to the same error message screen, but I can access the Setup Utility by pressing f2. the D2D recovery is enabled so I'm not sure why the alt+f10 isn't allowing me to recovery boot the computer. Thanks in advance

---

### Post by dabl on 2012-12-27
Using your Ubuntu Live CD, or a Parted Magic Live CD/USB stick, or a GParted Live CD, you need to set the "boot" flag on your hard drive or SSD.

---

### Post by mcriegel on 2012-12-27
I did not use a CD to install the Ubuntu. Rather I downloaded 12.10 from ubuntu.com. Therefore I have no external access to the file and cannot boot using a CD or flash drive. Any other suggestions on how I might recover either Windows XP or the Ubuntu that I downloaded from the web?

---

### Post by oldfred on 2012-12-28
If you installed from inside Windows did you install wubi?

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

    
Wubi uses the Windows boot loader to boot and is really just a large file inside the Windows NTFS partition.

If you cannot boot, you may need to use your Windows XP disk to reinstall the boot loader - fixBoot, fixMBR and or chkdsk. Some BIOS will not let your start booting unless a primary partition has the boot flag and Windows has to have the boot flag on the main install that you boot from. In Windows setting the boot flag is called make active.

       XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

---

