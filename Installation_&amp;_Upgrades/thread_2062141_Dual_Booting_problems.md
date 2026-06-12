---
title: "Dual Booting problems"
date: 2012-09-24
forum: Installation &amp; Upgrades
---

### Post by gilestelnarbe on 2012-09-24
Hi there
its been some while that I was using Win7 + Ubuntu Oneiric alongside eachother, but my Win7 crashed and I was forced(!) to reinstall it in its old drive by formatting the drive, which clearly deleted my bootloader info.
my HDD is partitioned to a NTFS drive for Win7 + Ubuntu drives + a NTFS drive which can be accessed by both.
So I have no access to ubuntu.
please help

---

### Post by Bucky Ball on 2012-09-24
You could try Boot Repair. 

Boot from the LiveCD, install Boot Repair from Synaptics or Software Centre (yes, it will install in a Live session) and launch/run it.

---

### Post by NikTh on 2012-09-24
And a Link for boot-repair , here : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
:)

---

### Post by gilestelnarbe on 2012-09-24
any other option? its a 300+ MiB package and I'm using a low-speed internet connection.

---

### Post by Pand5461 on 2012-09-24
> **gilestelnarbe said:**
> any other option? its a 300+ MiB package and I'm using a low-speed internet connection.
Boot from LiveCD (you have one, once you've managed to install Ubuntu, don't you?), [install GRUB afresh]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#The_terminal_way")

---

### Post by NikTh on 2012-09-24
> **gilestelnarbe said:**
> any other option? its a 300+ MiB package and I'm using a low-speed internet connection.

You made some mistake here , I think 

```
The following NEW packages will be installed:
  **boot-repair** boot-sav boot-sav-nonfree gawk glade2script libsigsegv2 pastebinit python-configobj
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get **1,312 kB** of archives.
After this operation, 5,707 kB of additional disk space will be used.
```

---

### Post by titanSavior on 2012-09-24
I believe he means he no longer has the disc and needs to re-download Ubuntu. I believe there is a program GRUB4DOS that you can run in Windows to install it. I looked it up and downloaded it and it was 801kb.

---

### Post by Bucky Ball on 2012-09-24
*Thread moved to **Installation & Upgrades***

---

### Post by YannBuntu on 2012-09-25
> **gilestelnarbe said:**
> any other option? its a 300+ MiB package and I'm using a low-speed internet connection.

If you have a Ubuntu CD (or liveUSB) , you can boot on it, choose "Try Ubuntu", then install and run Boot-Repair this way:
[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

---

