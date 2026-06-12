---
title: "Ubuntu UEFI installation with Existing Windows 10..."
date: 2016-03-16
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2016-03-16
Hi, all:

I tried to install a 2nd system, Ubuntu (tried both 14.04.4 and 15.10), along with the 1st system Windows 10.
Since Windows 10 is already installed as UEFI, Ubuntu must be UEFI (instead of Legacy) as well.

I followed the help at [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI"), but I still fail to install Ubuntu.
I guess it might have something to do with my BIOS.
I'm currently using the **BIOS Aptio Setup Utility** 

Can anybody give me a hand on how to successfully install Ubuntu with such a BIOS?


Cheers
Pei

---

### Post by ajgreeny on 2016-03-16
From a live Ubuntu system run the boot-info-script which comes as part of the Boot-Repair utility in my signature.
Copy back here the pastebin link you will be given by that script.

This will give us a lot more info about your system and where you have got to so far.

---

### Post by Bucky Ball on 2016-03-16
Did you boot into Windows and switch off hibernation? Essential. If hibernation is on Windows never unmounts the hard drive making it unavailable for installing any other OS.

---

