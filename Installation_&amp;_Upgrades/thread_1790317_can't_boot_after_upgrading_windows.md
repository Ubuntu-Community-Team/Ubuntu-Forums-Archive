---
title: "can't boot after upgrading windows"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by armadi on 2011-06-24
Hello,

I had ubuntu 10.04 dual boot with win xp and I recently decided to upgrade windows to win 7. Once I did that I could no longer see the grub therefore I couldn't manage to boot into ubuntu. I don't know what to do, the installation is there because I never touched that partition. 

Any suggestions will be very appreciated.

---

### Post by 67GTA on 2011-06-25
Windows wiped out the grub boot loader. Look here for instructions on reinstalling grub using a live CD. [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) Once you boot back into Ubuntu you will have to update grub to include Windows 7 by running ```
sudo update-grub
``` in a terminal. It must be nice to imagine you are the only operating system in the universe.

---

### Post by armadi on 2011-06-25
Thanks a lot buddy. it worked.

---

### Post by YesWeCan on 2011-06-25
> **67GTA said:**
> It must be nice to imagine you are the 
only operating system in the universe.

Strictly speaking...
It is Ubuntu that is non-compliant with the MBR-system standard. But that doesn't mean we can't hate Windows for other reasons. ;)

---

### Post by jocko on 2011-06-25
> **YesWeCan said:**
> Strictly speaking...
It is Ubuntu that is non-compliant with the MBR-system standard. 
Really? Is it Ubuntu's fault that the windows installer does not look for other operating systems?

---

### Post by YesWeCan on 2011-06-25
Yes. This topic belongs in the cafe so I'll stop here. Just to clarify that the MBR boot system and the Windows boot-loader are two different things. The MBR system will boot any compliant OS in any primary partition, including an extended partition. If Ubuntu were MBR compliant there would be no need for the constant grief of broken MBRs that we see in this forum.

---

### Post by 67GTA on 2011-06-25
IBM created the MBR system. Windows OS does not hold the standard for the MBR. Windows actually treats the MBR as empty space and writes to it to identify disks among other things, and lets certain apps hide reactivation codes there. Linux uses the MBR for the bootloader (grub/lilo), which was the original standard.

---

