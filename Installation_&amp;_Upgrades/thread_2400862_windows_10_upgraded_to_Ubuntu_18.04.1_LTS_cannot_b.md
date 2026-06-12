---
title: "windows 10 upgraded to Ubuntu 18.04.1 LTS cannot boot into windows"
date: 2018-09-11
forum: Installation &amp; Upgrades
---

### Post by michaelgshaw on 2018-09-11
Hi all, 
I am new to Linux and have just added Ubuntu 18.04 LTS to my windows 10 home install (want to dual boot win and ubuntu) as I want to run Magento Community Edition on localhost.
Problem is when I did this i turned off fast boot and installed but now I do not get option to boot to windows. I have added the pastbin below.

[http://paste.ubuntu.com/p/qbGDRp2qKy/](http://paste.ubuntu.com/p/qbGDRp2qKy/)

I have a reasonable understanding of boot sector for windows but not idea for Ubuntu, I have not made any changes. From what i could tell partitions exist but just not being seen when booting up. It is an Acer PC

Any help would be greatly appreciated.

Kindest regards

Michael

---

### Post by yancek on 2018-09-11
Your primary drive with windows and Ubuntu is GPT and EFI.  Your EFI partition does not show any windows or Linux EFI files so I'm not sure how that happened.  Ubuntu will create a separate folder on the EFI partition for its files but they don't show in boot repair nor do the windows EFI files which should be there?  Since you have an ACER, you need to set Trust somewhere in the BIOS before you can install/boot another system.  You might go to the Ubuntu site below which explains dual-booting windows/Ubuntu UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

