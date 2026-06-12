---
title: "UEFI External drive"
date: 2015-09-01
forum: Installation &amp; Upgrades
---

### Post by Amol_Gupta on 2015-09-01
Hi,

I read this thread till now. Even I am facing same problem.

I have UEFI mode enabled on my computer. I have already installed Ubuntu 14.04 on external hard disk. When I connect my hard disk I am able to boot Ubuntu from my hard disk. But when I disconnect hard disk boot loader doesn't pickup windows boot loader automatically. A grub window pops out and I have to type 'exit' and then choose windows boot manager to boot my windows.
Boot Order right now is 
1. Ubuntu 
2. Windows Boot Manager
3. USB HDD

 Now changing boot options are not helping much. I tried keeping boot options in this manner
1. USB HDD 
2. Windows Boot Manager
3. Ubuntu
But it would always load Windows and not pick up hard disk at all where Ubuntu is installed.

I want that whenever hard disk is connected it should boot Ubuntu and when hard disk is disconnected it should directly boot windows without asking for any grub command.

Help me with this please as after reading top messages I was not able to figure out what exactly I have to change or copy.

Thanks in advance.

Amol Gupta

---

### Post by Amol_Gupta on 2015-09-01
Hi,

I read this thread till now. Even I am facing the same problem.

I have UEFI mode enabled on my computer. I have already installed Ubuntu  14.04 on external hard disk in UEFI mode only. When I connect my hard disk I am able to  boot Ubuntu from my hard disk but when I disconnect hard disk boot  loader doesn't pickup windows boot loader automatically. A grub window comes up  and I have to type 'exit' and then choose windows boot manager from boot options to boot my windows.
Boot Order right now is 
1. Ubuntu 
2. Windows Boot Manager
3. USB HDD

 Now changing boot options is not helping much. I tried keeping boot options in this manner
1. USB HDD 
2. Windows Boot Manager
3. Ubuntu
But it would always load Windows and not pick up hard disk at all where Ubuntu is installed.

I want that whenever hard disk is connected it should boot Ubuntu and  when hard disk is disconnected it should directly boot windows without  asking for any grub command.

Help me with this please as after reading top messages I was not able to figure out what exactly I have to change or copy.

Thanks in advance.

Amol Gupta

---

### Post by oldfred on 2015-09-01
Moved to your own thread.
Boot issues almost always are unique.

What brand/model system?

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2015-09-01
It sounds to me that you have Grub installed on to the internal hard disk (Windows) but it is looking for its configuration files in the /boot/grub folder on the external hard disk. Which it cannot find when the external hard disk is disconnected.

A link to the URL that is given when we run Boot Repair - Bootinfo Summary will help us give accurate advice.

Regards.

---

