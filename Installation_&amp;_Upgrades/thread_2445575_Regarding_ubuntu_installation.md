---
title: "Regarding ubuntu installation"
date: 2020-06-16
forum: Installation &amp; Upgrades
---

### Post by saravjc on 2020-06-16
I'm new to ubuntu...I'm trying to install Ubuntu on windows as dual boot 
I downloaded the latest version of ubuntu from ubuntu website nd my usb is also flashed with the iso 
The problem is when I try to install Ubuntu, at the last step exactly after the choice of installation it comes as "your windows bitlocker is on turn off windows bitlocker to install Ubuntu"
I disabled all my drives and even decrypted bitlocker in windows but still it coming like the same issues
Please help me to install Ubuntu nd experience it

---

### Post by howefield on 2020-06-16
Thread moved to the "*Installation & Upgrades*" forum.

---

### Post by oldfred on 2020-06-16
Which install option are you using?
Are you trying to let the installer shrink the Windows NTFS partition with an auto install?
Better to use Windows to shrink the NTFS partition and then install into the unallocated space.
Often better to have Windows fast start up off (hibernation) and bitlocker off.
Grub will not boot hibernated nor encrypted Windows, but you can still dual boot using UEFI boot menu (same key you use to boot installer).

       Dual boot with Bitlocker works
[URL="https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10"]https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10

      [/URL]
 Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)  
    

General UEFI install info in link in my signature below.
[URL="https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10"]
[/URL]

---

### Post by TheFu on 2020-06-16
i would just use a virtual machine for the first few years to get used to linux.  Then you can swap Linux on the hardware and put Win10 in a VM for those 2 hrs a month you still need Windows.

**Update for lurkers:** If you've already chosen to encrypt the disk, using virtual machines will allow you to keep that encryption AND have the guestVMs encrypted using the same encryption methods/tools as the host.  Beware, whenever disk encryption is used, excellent backups are REQUIRED.  This is because when anything goes wrong with the storage due to logical, human, or disk failures, data recovery tools on all platforms cannot help. The **only** viable solution to getting data back is through backups that were already created prior to the issue. That applies to Windows, Linux, OSX, Android, iOS - all OSes that can use or use encryption by default need backups.

---

### Post by saravjc on 2020-06-16
Hi guys.... thank you everyone for helping me out, actually I get to install Ubuntu on dual boot. What I did was, I decrypted bitlocker in all drives and booted iso file via Rufus latest version. Now I can use Ubuntu in dual boot
Cheers nd have nice day

---

