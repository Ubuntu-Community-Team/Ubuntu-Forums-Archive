---
title: "Can't boot into Ubuntu"
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by niven2 on 2014-05-24
I recently installed Ubuntu 14.04 alongside windows 8.1 on my laptop. At the end of the installation guide, it told me that I needed to restart my computer to finalize the changes and that I would be able to select which OS to boot into upon turning it back on. I restarted my laptop, but was never able to choose an OS. It automatically booted up windows 8.1 (I restarted multiple times just to make sure). I checked the C: directory to see if the memory I partitioned to Ubuntu was still accessible to windows, and it was not. I also, tried Ubuntu by booting from my USB and was able to see the drive with the data partitioned for Ubuntu so I know for a fact that the OS was installed. Does anyone know what I need to do to fix my problem so that whenever I restart my computer I get a choice of operating systems to boot from?

*I'm using a Lenovo G580
*I have secure boot disabled

---

### Post by Bucky Ball on 2014-05-25
Welcome. Try Boot Repair. It is the most painless fix, if it works, that is:

[https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair)

You have two options. You can install it while running from a LiveCD/USB desktop (if you have internet access, that is) and run it from there, or you can download the ISO, create a bootable disk/USB, and boot from that, then run it. Hope that helps and good luck.

---

### Post by ubfan1 on 2014-05-25
Or try invoking the EFI boot menu at power-on (some function, varies by machine), and selecting ubuntu (or maybe you have to chose HDD first, then choose between Windows and ubuntu.  If that works, install efibootmgr, and change the boot order to put ubuntu first.

---

