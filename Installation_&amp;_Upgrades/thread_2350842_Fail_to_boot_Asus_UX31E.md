---
title: "Fail to boot Asus UX31E"
date: 2017-01-28
forum: Installation &amp; Upgrades
---

### Post by kybiss on 2017-01-28
Hello everyone,

I have an Asus UX31E ultrabook. I've installed Win 7 and Ubuntu to it. A while ago, it started not to boot. Computer guys said SSD and boot are damaged. Unfortunately replacing SSD is really expensive for this notebook. I've decided to use it with any live linux distro but I could not find a way to repair boot. Here is the details of my boot grabbed with boot–repair:
paste.ubuntu.com/23882258

I would like to be happy if anyone can help me about the status of my boot problem.

Thanks in advance.

Kybiss

---

### Post by wildmanne39 on 2017-01-28
*Thread moved to **Installation & Upgrades for better support**.*

---

### Post by oldfred on 2017-01-28
[FONT=arial]> [/FONT][FONT=arial]Invalid MBR Signature found[/FONT][FONT=arial]

That is a bigger issue.
System cannot seem to recognize any type of partitioning on drive.

What does testdisk show?
[/FONT]
[FONT=arial]       [/FONT] [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) 
    
[FONT=arial]       [/FONT] Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 
    
[FONT=arial]This user had Secure Boot on, and turned it off. As well as other issues. 
boot-Repair also says you may have Secure boot on. Check & turn it off.
[/FONT] Cannot boot...Invalid MBR Signature found on boot partition 
[https://ubuntuforums.org/showthread.php?t=2268040](https://ubuntuforums.org/showthread.php?t=2268040) 

[FONT=arial]
[/FONT]

---

