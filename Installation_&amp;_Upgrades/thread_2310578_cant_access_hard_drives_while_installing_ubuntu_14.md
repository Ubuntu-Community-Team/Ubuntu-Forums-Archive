---
title: "cant access hard drives while installing ubuntu 14.04"
date: 2016-01-20
forum: Installation &amp; Upgrades
---

### Post by farbod3 on 2016-01-20
I have a problem in installing ubuntu 14.04 LTS and that is when im  trying to load my hard drives in live boot (try without installig) i get  this "Not authorized"  and when i want to install it it shows my hard clean without any  partitions or used space but i have some partitions and windows 10 as  well.
  
any idea to solve it ?

---

### Post by grahammechanical on 2016-01-20
> when im  trying to load my hard drives in live boot

I do not understand what you mean by that sentence. Does the live session load and run correctly? Do you get this "not authorised" message when you are using the live session file manager to access the Windows partition? Are the Windows partitions encrypted?

Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Note this comment

> In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").

This also applies to Windows 10. It might be useful if you take a screenshot from Windows of your partition layout and attached the image to your thread.

Regards

---

