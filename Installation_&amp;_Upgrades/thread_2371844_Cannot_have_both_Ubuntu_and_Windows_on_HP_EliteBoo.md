---
title: "Cannot have both Ubuntu and Windows on HP EliteBook 840 G2"
date: 2017-09-19
forum: Installation &amp; Upgrades
---

### Post by dale032 on 2017-09-19
Hello everyone, 

For now I only have ubuntu on my HP EliteBook 840 G2 laptop. Since I hade some problems booting into ubuntu after instalation, I found out here that HP expects to boot into windows and one of you helped me fix my problem. Now I really need both ubuntu and windows on my laptop but every time I try to do that it boot only windows. I want my PC to open GRUB where I can choose windows or ubuntu. 
Can someone help me with this?

Thanks everyone, I will apriciate it!

---

### Post by kc1di on 2017-09-19
Hello dale032 and Welcome to Ubuntu,

You need to get windows installed and working properly before installing Ubuntu.  
[here is a page ]("https://www.linuxtechi.com/how-to-dual-boot-windows-10-ubuntu-16-04/")that explains how to do a dual boot. 

Note: if Windows is installed with UEFI then Ubuntu must be installed the same.

---

### Post by dale032 on 2017-09-19
Thank you for warm welcome. I will try this and will get you back with results. Thanks again!

---

### Post by oldfred on 2017-09-19
The work around for dual booting on HP is a bit different than that of just booting Ubuntu.
You should be able to directly boot both Windows & Ubuntu from UEFI boot menu. escape, f9 for menu.

 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

Boot-Repair now copies /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi which is the path for the fallback or hard drive UEFI boot entry. But Boot-Repair sees all the HP .efi boot files it has for various maintenance functions and creates a new grub 25_custom which adds lots of entries to grub menu. Many edit most of those out, or delete 25_custom.

With HP you probably cannot set Ubuntu as default or first in boot order, or HP resets if you do using efibootmgr. But you should be able to set Hard Drive entry as first and that then will boot grub/Ubuntu.

Grub only boots working Windows. And Windows udpates may turn fast start up back on which is hibernation. Grub then will not boot hibernated Windows.  Just directly boot from UEFI menu and turn off fast start up again to make it work from grub.

---

