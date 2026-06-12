---
title: "Trying again but I need a little help..."
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by LinuxUser007 on 2011-09-10
I have an HP dv7 AMD Phenom(tm) II N620 Dual-Core Processor 2.80 GHz. 4.00GB (3.74 GB usable) 64-bit Operating System. I did the 3 partitions to install Ubuntu for the 3rd time. My Ubuntu and Window7 both worked fine when I would reboot I could go to either one I tested them both and they were both working perfectly. However when I checked on my computer on Windows7 where the C: driver was with the others I made for Ubuntu to use the three partitions I made for Ubuntu were empty. So I had 4 partitions 3 empty and 1 with both Windows7 and Ubuntu with little memory left to do much on the C: drive and 3 empty partitions that had nothing on them. What did I do wrong? I restored the laptop back to factory setting and its ready for me to try again. Since I'm new to Linux I need help...I try to do it on my own but my 1st time my laptop crashed and the 2nd only Ubuntu worked. But I refused to give up on Linux...So I think its time to ask for help...Please help me...what am I doing wrong? I fallow the Ubuntu installation wizard step by step...Did I miss something?

---

### Post by howefield on 2011-09-10
Thread moved to the "*Installation & Upgrades*" forum. 

Sounds like you installed Ubuntu into the Windows partition using the side by side option at the partitioning stage allowing Ubuntu to resize the Windows partition to make room for itself.

Create your Ubuntu partitions as you did previously, then at the partitioning stage during the installation process you need to select the "Something Else" option and mount each of the Ubuntu partitions as appropriate.

---

### Post by howefield on 2011-09-10
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=1841749](http://ubuntuforums.org/showthread.php?t=1841749)

---

