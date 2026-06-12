---
title: "windows 10 cannot resume after being hibernating"
date: 2016-03-02
forum: Installation &amp; Upgrades
---

### Post by wad_lem on 2016-03-02
good day everyone,i have a problem with windows 10 after installing ubuntu 14.04 ,windows cant resume after being hibernating and and it s too slow in starting :confused:
in the installation l didnt got any problem (enabling cms ,disabling fastboot,disabling secure boot)
i installed ubuntu in a separated partition 
the grub didnt had any problem in booting first
but when it launch windows 10 ,it start very slow (like when it start after taking out power)
i think it s coming from installing ubuntu in cms mode so may be reinstalling ubntu solve the problem
but i ll wait for your suggestions.
thank you

---

### Post by grahammechanical on 2016-03-02
Windows 8 & 10 get fast start up times being not actually shutting down but by going into hibernation. If we do not disable Fast Start & some other things then we get problems installing Ubuntu. 

Also, Windows 10 when it is pre-installed will be installed in EFI mode. And that means we need to run the Ubuntu live session in EFI mode so that Ubuntu is installed in EFI. So, installing Ubuntu in BIOS/CSM/Legacy mode when Windows 10 is installed in EFI is not the correct way to do things.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by wad_lem on 2016-03-03
Still having the same problem even after intalling ubuntu in uefi mode
Any other solutions?

---

