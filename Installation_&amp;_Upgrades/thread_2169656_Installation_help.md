---
title: "Installation help"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by aditya4 on 2013-08-22
hello ev1 i have 32 bit intel core 2 duo processor with windows 8 installed,,so i wanted to know whether to install 32 bit version or 64bit version of ubuntu 13.
and i have two partitions namely C: and D:. Windows 8 is installed on C: and i want to install buntu on D:,please can anyone give me step by step instruction on how to install,i want an option on the screen to boot into which os when i switch on the system.

---

### Post by sanderj on 2013-08-23
> **aditya4 said:**
> hello ev1 i have 32 bit intel core 2 duo processor with windows 8 installed,,so i wanted to know whether to install 32 bit version or 64bit version of ubuntu 13.
and i have two partitions namely C: and D:. Windows 8 is installed on C: and i want to install buntu on D:,please can anyone give me step by step instruction on how to install,i want an option on the screen to boot into which os when i switch on the system.

Intel Core 2 is 64-bit, so you can use Ubuntu 64-bit (and 32-bit too)
About C: and D:: you will probably see them as "/dev/sda1" and "/dev/sda2" during the install. Select the correct one, so probably /dev/sda2

See [http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest)

---

### Post by aditya4 on 2013-08-23
thanks man , i didnt see it properly in windows system information it says 32 bit operating system .
now when i select [COLOR=#000000]/dev/sda2 and press ok i recieve a error message saying "no root file system is defined",what should i do
i have created a bootable usb drive[/COLOR]

---

### Post by grahammechanical on 2013-08-23
Ok, so you running the Ubuntu Live session and select Install Ubuntu and you have an option to install alongside Windows or do something else. Which one did you choose? Or are you using the Windows installer (wubi.exe). You should not use wubi.exe with Windows 8. The two are incompatible.

If we choose the Something else option we get to a partition screen where we select the partition to install Ubuntu into. Do not select the partition with Windows on. Select the partition that you want Ubuntu to be in and then click Change.

In the dialog box use the drop down menu to change the Use As setting from Do not use to use as Ext4. Tick the box to format the partition and in the Mount Point panel select /

You have now defined a root file system. Click OK. You will see a message advising you that it takes time to resize a partition and you will wonder why you're seeing that as you did not resize the partition. Accept the message and you will be taken back to the partitioning page where you can click Install and you will not get that "no root file system is defined" message again.

Oh, by the way a 32 bit operating system will run on both 32 bit and 64 bit CPUs. That is why you are running 32 bit Windows 8 on a 64 bit CPU. The minimum specification for Windows 8 64 bit is 2GB RAM. But 64 bit operating systems will only running on 64 bit CPUs.

Regards.

---

### Post by aditya4 on 2013-08-24
thanks a lot :)

---

