---
title: "Cannot install UBUNTU on Intel NUC7i7DNHE"
date: 2018-12-27
forum: Installation &amp; Upgrades
---

### Post by mlort on 2018-12-27
Hi,

I am trying to install Ubuntu on a recently acquired Intel **NUC7i7DNHE **with 16 GB of RAM (Ballistix sport) and a 1 TB Samsung SSD 860 EVO.

I have download the Ubuntu **16.04 LTS 64-bit certified version** from the following website: [https://certification.ubuntu.com/hardware/201802-26116/](https://certification.ubuntu.com/hardware/201802-26116/).

I am trying to install or launch Ubuntu from a previously flashed USB  but the system freezes without doing it. Any clue of what could I do to  install it?

I would appreciate any help. Thank you!!

---

### Post by ajgreeny on 2018-12-27
How did you create the USB you're using, and did you check the ISO image file you used with the hashes you can find at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) ?

---

### Post by ubfan1 on 2018-12-27
Did you check the Intel site ([https://downloadcenter.intel.com/)for](https://downloadcenter.intel.com/)for) any BIOS updates? 0059 is the latest, from Nov 2018.I found kernels earlier than 4.19 did not have full hardware support for the little Intel Compute Stick STCK1A8LFC. You might try a later release, 18.04 was pretty good for the stick, just lacking bluetooth.

---

### Post by mlort on 2018-12-27
Ajgreeny thank you for your response.

To create the USB I download the ISO image and burn into the USB using the "Startup Disk Creator".

I do not check the hashes but I have used the USB in another computer and it works perfectly.

---

### Post by mlort on 2018-12-27
Ubfan1 thank you for your response.

I have updated the BIOS to the latest one and also tried the 18.04 release and the same problem arises.

---

### Post by oldfred on 2018-12-27
Some more threads on NUCs, but each generation seems to have its own issues.

       How to install Bionic on Hades Canyon (nuc8i7hvk/nuc8i7hnb) with Vega M GPU support  - using ppa
[https://ubuntuforums.org/showthread.php?t=2400400](https://ubuntuforums.org/showthread.php?t=2400400)
Intel NUC
[https://www.omgubuntu.co.uk/2018/06/intels-7th-gen-nucs-are-now-ubuntu-certified](https://www.omgubuntu.co.uk/2018/06/intels-7th-gen-nucs-are-now-ubuntu-certified)
Certified ISO & Instructions
[https://www.ubuntu.com/download/iot/intel-nuc-desktop](https://www.ubuntu.com/download/iot/intel-nuc-desktop)
intel nuc - nuc5i5MYHE w/M.2 SSD 
[https://ubuntuforums.org/showthread.php?t=2376245](https://ubuntuforums.org/showthread.php?t=2376245)
boot into the EFI shell and manually point startup.nsh to the grubx64.cfg and run it
Running The Intel NUC6i7KYK On Linux With Skylake Iris Pro Graphics 16.10
[http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1)

---

### Post by Tadaen_Sylvermane on 2018-12-27
Is the ram on the list as supported. I tried a Nuc awhile back and just got a random stick of ram of the right size required but it wasn't on the list of supported ram
. It just froze on boot till I got a stick that was listed as supported.

---

### Post by liaata on 2018-12-28
Sounds like an ISO problem

---

### Post by mlort on 2019-01-03
[**[COLOR=#000000]Tadaen_Sylvermane[/COLOR]**]("https://ubuntuforums.org/member.php?u=1914514"),

You were right! I have bought a new ram from the supported list and now everything works! Thank you for your help.

---

