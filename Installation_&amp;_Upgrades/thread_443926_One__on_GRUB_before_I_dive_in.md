---
title: "One ? on GRUB before I dive in"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by cerebral_mamba on 2007-05-14
HI,

I am a first time Linuxer and after extensive reading, I have pretty much figured out how to use NTLDR as the boot loader. I need to do this becaue (1). I need access to IBM Rescue & Recovery partition using the Access IBM button & (2) windows has to remain trouble free as my bread and butter depends on half a dozen software that only runs in windows.

I tried installing ubuntu fiesta on two old desktops in my office as an experiment and during both the trials I the installation did not ask me where I want GRUB installed? After I did the windows re-sizing and creating new partitions '/','/home' & 'swap', it just proceeded to format them and install ubuntu and did not give me an option to select where to install GRUB. Is it because I did not make a /boot partition? 

I under any cost do not want my MBR taken over by GRUB and am totally clueless on how to specify the installation location for GRUB while installing Ubuntu (I will be manually resizing my windows partition and other stuff required using ubuntu's partition manager during the installation process). I know how to manually install GRUB to my desired location and recover my MBR because I will be backing it up using "MBRTool", but i can save all the hazzle if I could do it right at the time of installing ubuntu. Please Help.

Thanks a million.

---

### Post by confused57 on 2007-05-14
> **cerebral_mamba said:**
> HI,

I am a first time Linuxer and after extensive reading, I have pretty much figured out how to use NTLDR as the boot loader. I need to do this becaue (1). I need access to IBM Rescue & Recovery partition using the Access IBM button & (2) windows has to remain trouble free as my bread and butter depends on half a dozen software that only runs in windows.

I tried installing ubuntu fiesta on two old desktops in my office as an experiment and during both the trials I the installation did not ask me where I want GRUB installed? After I did the windows re-sizing and creating new partitions '/','/home' & 'swap', it just proceeded to format them and install ubuntu and did not give me an option to select where to install GRUB. Is it because I did not make a /boot partition? 

I under any cost do not want my MBR taken over by GRUB and am totally clueless on how to specify the installation location for GRUB while installing Ubuntu (I will be manually resizing my windows partition and other stuff required using ubuntu's partition manager during the installation process). I know how to manually install GRUB to my desired location and recover my MBR because I will be backing it up using "MBRTool", but i can save all the hazzle if I could do it right at the time of installing ubuntu. Please Help.

Thanks a million.

You can definitely specify where to install grub with the alternate install cd, which is what I use, exclusively...I believe with the desktop live cd, there is a section that it says  grub will be installed to (hd0), the mbr by default, but that you can change it to the root partition by typing it in, i.e. (hd0,2) or /dev/sda3...or there might be an arrow with a drop-down menu that will allow you to specify?

---

### Post by psusi on 2007-05-14
Grub is installed to the MBR by default, and should automatically pick up on your windows install, and have an option to chain load windows via ntldr.  Why don't you just use that?  If you have a special entry on your windows boot menu, it will still be usable when you choose to have grub boot windows.

---

