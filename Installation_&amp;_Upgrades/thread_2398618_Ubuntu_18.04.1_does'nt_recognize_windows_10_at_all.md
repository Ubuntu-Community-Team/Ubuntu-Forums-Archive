---
title: "Ubuntu 18.04.1 does'nt recognize windows 10 at all"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by 1.mysterio on 2018-08-15
My laptop initially had windows 18.04 dual  booted in it. It had grub menu for selecting OS. I had initially  problems in installing WiFi adapter but finally i was able to install  it, but temporarily. Probably, while making the settings permenant i  would have made some mistake. I was unable to reinstall the driver. I  tried a lot but i was not able to reinstall it. Finally, i decided to  reinstall ubuntu.I deleted the entire drive partition in which ubuntu  18.04 was installed in. To properly delete grub, i typed some commands in  command prompt of Windows 10 automatic pc repair and troubleshooter. I  executed-

bootrec /fixmbr - Successfull
bootrec /fixboot - *access is denied*
I  resatrted my pc. Windows 10 was successfully starting without showing  any errors. I rebooted it 3-4 times to ensure ubuntu is fully deleted,  everything was fine. So i downloaded latest ubuntu 18.04.1 and tried to  dual boot. Everything goes well. But, before installing ubuntu it  does'nt shows option for "Install Ubuntu alongside windows" it shows all  other 4 options like "erase drive and install ubuntu"; "something  else", etc. It shows NO OPTION like "Install Ubuntu alongside windows". I  have dual booted 2-3 times before but it never happened like this. I  don't want to risk my windows 10. I uncheked the hibernate option and  fast start  option in control panel of windows 10 but it does'nt  work.link for my previous post for wifi adapter-  [https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/No-WiFi-adapter-in-ubuntu-18-04-LTS/t...]("https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/No-WiFi-adapter-in-ubuntu-18-04-LTS/td-p/6785623")

 
Please help me.

---

### Post by yancek on 2018-08-15
You need to first determine if you are using UEFI/GPT with windows 10 as that is the default.  If you are using UEFI/GPT with windows you need to do the same with Ubuntu.  This is explained in detail at the Ubuntu site at the link below.  You should not try the auto-install (Ibnstall Alongside) method when you are using UEFI.  Read the link so you understand UEFI.  If you are not using UEFI, post back with specific information on it.  I'm not a windows user but I understand there are multiple hibernation options on some system, in the BIOS and also in windows so check that again.  Good luck.

---

