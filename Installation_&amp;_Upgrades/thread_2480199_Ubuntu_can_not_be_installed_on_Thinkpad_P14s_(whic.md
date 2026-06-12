---
title: "Ubuntu can not be installed on Thinkpad P14s (which is supposed to be supported!)"
date: 2022-10-22
forum: Installation &amp; Upgrades
---

### Post by matej-kovacic on 2022-10-22
I have tried install Ubuntu Desktop (22.04.1 and 22.10) on my Lenovo P14s (AMD version).
CPU is AMD Ryzen 7 PRO 5850U with Radeon  Graphic, UEFI BIOS version was R1MET44W (1.14). I updated BIOS (from  Windows OS) and now I have version R1MET49W (1.19). I also updated Lenovo firmware through Ubuntu Software (with Live USB).

I disabled Secure Boot (Security &#10140; Secure Boot), disabled OS Optimized Defaults (Restart &#10140; OS Optimized Defaults), and set Sleep state to "Linux" (Config &#10140; Power &#10140; Sleep State &#10140; "Linux").

Now, Canonical states that P14s with AMD Ryzen 7 PRO 5850U is Ubuntu compatible/supported! Also, the [official documentation]("https://download.lenovo.com/pccbbs/mobiles_pdf/tp_p14s_amd_ubuntu_20.04_lts_installation_v1.0.pdf") from Lenovo states P14s supports Linux, but, they also say I need to go (in BIOS) to Config - Storage and there set AHCI mode (instead of RST).

  

 The problem?

  

 My BIOS **does not have Storage option** under Config!!!

 

 Anyway, I just tried to install Ubuntu (remember, I tried 22.04.1 and 22.10), but after I set up WiFi password, and select which packages I would like to install (normal vs minimal installation),I get  some really weird error.

You can see this "pearl" here:
[https://i.ibb.co/GnHxv0t/ubuntu-22-10-install-wtf.jpg](https://i.ibb.co/GnHxv0t/ubuntu-22-10-install-wtf.jpg)

**And the installation hangs.**

 

When I exit the installer, crash reporting software says that Ubuntu has experienced internal error. The problematic app that crashed is /usr/bin/parted_server.

So, my question is - any idea how to solve this problem?

---

### Post by ubfan1 on 2022-10-22
Did you hashcheck the downloaded ISO, and run any offered media check on the install media?  Looks like something is garbled.

---

### Post by matej-kovacic on 2022-10-22
No, the checksum is OK. Besides Ubuntu Desktop 22.04.1 and 22.10 I also tried Mint Vanessa. And there is THE SAME error. 

[IMG]https://i.ibb.co/sPyq2vb/mint-vanessa-wtf.jpg[/IMG]

---

### Post by matej-kovacic on 2022-10-22
Another thing. I tried Ubuntu 20.04, which Canonical says it is supported: [https://ubuntu.com/certified/202104-28912](https://ubuntu.com/certified/202104-28912)

Guess what?

The SAME error.

---

### Post by ubfan1 on 2022-10-22
Might be a language/font issue.  Try selecting english and see if the error windows is readable.

---

### Post by matej-kovacic on 2022-10-22
Well, I tried this. THE SAME.

I also tried another USB key. THE SAME.

I am out of ideas...

---

### Post by tea for one on 2022-10-22
> **matej-kovacic said:**
> I am out of ideas...
I would try _without_ connecting to the internet.

---

### Post by matej-kovacic on 2022-10-22
I would say that this is complete nonsense. But yes, I also tried this. THE SAME.

I am inclined to the idea that there is a problem with parted_server...

---

### Post by tea for one on 2022-10-22
Quite possibly nonsense but you did say you were out of ideas.
Can you boot into a live session, open a terminal and run:-
```
sudo parted -l
```

---

### Post by matej-kovacic on 2022-10-23
OK, I found the solution. I erased Windows completely (actually rewrite first part of device /dev/nvme0n1 with zeroes - sudo dd if=/dev/zero of=/dev/nvme0n1 bs=16M), and then I was able to install Ubuntu.<br><br>I guess there is a problem with partitioner which does not recognize one of the Windows partitions... So yes, it is Ubuntu fault. But luckily, I was able to solve this.

---

