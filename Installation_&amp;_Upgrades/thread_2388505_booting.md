---
title: "booting"
date: 2018-04-03
forum: Installation &amp; Upgrades
---

### Post by diewke1 on 2018-04-03
Got  win 10 in C drive is it possible to put Ubuntu 16.04 in D drive

---

### Post by wildmanne39 on 2018-04-03
*Thread moved to **Installation & Upgrades, a more appropriate forum**.*

---

### Post by yancek on 2018-04-03
> Got  win 10 in C drive is it possible to put Ubuntu 16.04 in D drive 		

No because drive letters (D) on windows are only assigned to windows filesystems and you won't be able to install any Linux to a windows filesystem.  Resize (shrink) your largest windows partition using windows tools (Disk Management?) and use the unallocated space created on which to install Ubuntu.

I would also suggest that before you begin installing, you read the Ubuntu documentation at the link below on dual booting Ubuntu and windows 8/10. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by diewke1 on 2018-04-05
thank you for the instructions about the Ubuntu booting result for me is 
no device connected   error oxc0000225

---

### Post by diewke1 on 2018-04-05
followed instruction for booting Ubuntu with win10 in acer computer z24-880
result device not connected   error OXC 0000225 use other OS to restart  

thank you  diewke1

---

### Post by mörgæs on 2018-04-06
You need to post much more information. Please explain in all details everything you did, for example how you shrank the Windows partition.

---

### Post by oldfred on 2018-04-06
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by diewke1 on 2018-04-07
disk management shrink unallocated new simple volume install Ubuntu 16.04
other, free space root \   free space   home \ in stall finished restart remove disk enter 
error OX0000225
f1 recovery environment
f8 startup settings
esc for UEFI firmware
f9 use diff operating system

---

### Post by diewke1 on 2018-04-08
looks like Ubuntu is clashing with acer win 10  Ubuntu UEFI  win 10 BIOS
not able to dual boot

---

### Post by oldfred on 2018-04-08
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="https://ubuntuforums.org/showthread.php?t=2358003"]https://ubuntuforums.org/showthread.php?t=2358003

[/URL]
 [http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
      
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    


[URL="https://ubuntuforums.org/showthread.php?t=2358003"]
[/URL]

---

### Post by diewke1 on 2018-04-10
tried many suggestion at last got it fixed with help of boot repair
thank you

---

