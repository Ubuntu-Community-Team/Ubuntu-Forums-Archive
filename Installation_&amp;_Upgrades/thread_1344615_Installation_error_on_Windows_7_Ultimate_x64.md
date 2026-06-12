---
title: "Installation error on Windows 7 Ultimate x64"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by vidyesh on 2009-12-03
Hey,

I downloaded the latest Ubuntu 9.10 amd 64 for my 64bit system.
I mounted the ISO and tried to install it using wubi but got this error 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=138432&stc=1&d=1259833081[/IMG]


Please help me sort it out.
I am not sure if i should provide you the log file as the log file has many data which might not be safe to share.

Present os : Windows 7 Ultimate x64

Anything else you want to know? 

Thank you.

---

### Post by madverb on 2009-12-03
Possibly try right click the install file for wubi and select Run as Administrator.

---

### Post by vidyesh on 2009-12-04
Yup went in the ISO and did the run as Admin thing . 
Same error again :(

---

### Post by darkod on 2009-12-04
Any particular reason you want to install wubi and not side-by-side dual boot?

---

### Post by vidyesh on 2009-12-04
Well wubi is supposed to do the same thing. it would eventually make it dual boot only.
I had used wubi before a few months back and it wrked dunno whts wrng now :| :(

---

### Post by darkod on 2009-12-04
No, it won't. It will only create sort of "virtual" dual boot and ubuntu. For example, your partitions will still be ntfs, all of them. Wubi is NOT a side-by-side dual boot install of two OSs.

People get confused a lot about that. The ONLY way to make a dual boot where windows and ubuntu will be on separate partitions witha filesystem on their own, is by booting with the ubuntu cd and selecting Install Ubuntu option.

Wubi will just add entry to the windows bootloader for example. If windows gets corrupted in most situations you can't start wubi too. While with peoper dual boot if one system is corrupted you can still work with the other.

Wubi documentation clearly says, installing ubuntu INSIDE windows. In other words, sort of like virtual machine. Otherwise no version of linux can run inside windows.

---

### Post by vidyesh on 2009-12-04
Okay, so can you give me a details guide for installing Ubuntu and windows together?

---

### Post by darkod on 2009-12-04
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by fidamehran on 2009-12-05
Dear Darkod, But does this really solve the initial issue? Your solution speaks of a side-by-side Dual Boot. We are talking about an Wubi install here. I'm quite sure the side-by-side dual boot will work really fine. But the Wubi option needs to stay alive.
Definitely, the Windows developers put in some sort of protection to alter the boot information by any third party. But there has to be a workaround, a solution. No?

We have to keep the avenue open for people who want to try Ubuntu through Wubi before actually digging in.

---

### Post by darkod on 2009-12-05
> **fidamehran said:**
> Dear Darkod, But does this really solve the initial issue? Your solution speaks of a side-by-side Dual Boot. We are talking about an Wubi install here. I'm quite sure the side-by-side dual boot will work really fine. But the Wubi option needs to stay alive.
Definitely, the Windows developers put in some sort of protection to alter the boot information by any third party. But there has to be a workaround, a solution. No?

We have to keep the avenue open for people who want to try Ubuntu through Wubi before actually digging in.

No, it definitely doesn't solve it. But it seems you missed the biggest point, the OP was at the opinion that wubi would create the same setup, which is not true. I never said wubi should never be used.
But I can't help with the original issue, I have installed wubi inside Vista Ult for example without any problem. Besides, when windows issues get involved too you can't always find the solution and maybe the problem is not in the Ubuntu. You said yourself, if the MS developers implemented some sort of protection which in some cases activates? Should the Linux community try to "break" that or should MS who says it doesn't mind competition anyway, change its ways?
I have no solution for the original problem, if you do just post it. I just helped realize that wubi is not creating the same. The final choice is always with him/her.

---

### Post by fidamehran on 2009-12-05
> **darkod said:**
> No, it definitely doesn't solve it. But it seems you missed the biggest point, the OP was at the opinion that wubi would create the same setup, which is not true. I never said wubi should never be used.
But I can't help with the original issue, I have installed wubi inside Vista Ult for example without any problem. Besides, when windows issues get involved too you can't always find the solution and maybe the problem is not in the Ubuntu. You said yourself, if the MS developers implemented some sort of protection which in some cases activates? Should the Linux community try to "break" that or should MS who says it doesn't mind competition anyway, change its ways?
I have no solution for the original problem, if you do just post it. I just helped realize that wubi is not creating the same. The final choice is always with him/her.

Thanks, Darko. I'm at a way too amateur level to give such serious solutions. But I'll definitely let you know if I find something.
Please do the same if you find any solution.:D

---

### Post by vidyesh on 2009-12-05
Ya that would be helpful actually.
I find wubi more practically easy to manage. 
Else would be dual booting side by side i guess.

---

