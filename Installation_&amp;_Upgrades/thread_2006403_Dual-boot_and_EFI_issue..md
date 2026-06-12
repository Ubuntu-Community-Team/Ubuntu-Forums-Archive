---
title: "Dual-boot and EFI issue."
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by ahanabu on 2012-06-19
**(repost)** 			 			 			 		   		 		 		Im helping a  friend deal with a dual-boot issue (Windows 7 and Ubuntu (Kubuntu)  12.4). He has a 64-bit Samsung laptop with 8GB and a Tb Disk. It came  with Windows 7 and EFI with a 100Mb sda1 partition. He installed Ubuntu  12.4 and GRUB2 naturally pointed to both Ubuntu and Windows, but when he  booted Windows, it said it had to do some recovery stuff and undid  GRUB, hence no booting into Ubuntu. He reinstalled Ubuntu and it set up  GRUB2 but this time no Windows boot entry. I went over to his place last  week and installed the new boot-repair utility and ran it, which  restored the Windows entry, but Windows doesn't boot because of an EFI  issue (and until then I knew zero about EFI/UEFI). Boot-repair prints  out a little window which gives some info about where EFI should point  to, and this probably will solve the Windows boot issue, but this  requires configuring I'm not familiar with. How to point GRUB2 and EFI  boot to properly boot Windows 7? Thanks in advance.

---

### Post by vykuntamsrinivas on 2012-06-19
hi, i didn get u and i don knw UFI/etc but i can help u ...we have a program called boot-repair which detects the OSs installed on your HDD and repairs/sets,the GRUB..so that you can boot  from either of your OSs........please check this
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mastablasta on 2012-06-19
he already ran that. please read the thread before posting something.
 
to the OP have a look here: [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
and maybe here... ugh...: [https://wiki.ubuntu.com/UEFI-howto](https://wiki.ubuntu.com/UEFI-howto)
 
user friendly? not really. and since most computer will now be built using UEFI i would expect a better/easier solution.

---

### Post by YannBuntu on 2012-06-19
Hello

> **ahanabu said:**
> Boot-repair prints  out a little window which gives some info about where EFI should point  to, and this probably will solve the Windows boot issue

What was this message? What was the BootInfo URL that appeared after you used Boot-Repair?
if you don't remember, please run Boot-Repair again, click "recommended repair" and indicate the new URL that will appear.

---

### Post by ahanabu on 2012-06-20
> **YannBuntu said:**
> 
What was this message? What was the BootInfo URL that appeared after you used Boot-Repair?
if you don't remember, please run Boot-Repair again, click "recommended repair" and indicate the new URL that will appear.

Hi, and thanks for the help. I don't have access to my friends computer at the moment, and won't until perhaps tomorrow or even later.  If I can reach him on Facebook, I might be able to get this info sooner. I will post when I can. Regards,

---

### Post by nehaljwani on 2012-10-08
You don't necessarily need to dual boot Windows and Linux on UEFI. Follow the guide [http://www.youtube.com/watch?v=PEou2dIcMSE](http://www.youtube.com/watch?v=PEou2dIcMSE) to convert your UEFI to MBR-BIOS without loss of data. Or read about it here: [http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html](http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html)

---

