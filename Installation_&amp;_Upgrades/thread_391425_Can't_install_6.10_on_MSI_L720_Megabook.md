---
title: "Can't install 6.10 on MSI L720 Megabook"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by dimadee on 2007-03-23
Firstly, I am a newbie to the Linux world, so be gentle :) 

I have a brand new MSI L720 Megabook and would really like to give Ubuntu (or a derivative) a go as I am sick of Windows (aren't we all?).  For more info on the laptop visit [http://www.msi.com.tw/program/products/notebook/nb/pro_nb_detail.php?UID=619](http://www.msi.com.tw/program/products/notebook/nb/pro_nb_detail.php?UID=619)  - I have a Pentium M 1.73 Ghz with 1Gb RAM.

The problem is when I try to install Edgy, it fails to install X server, and the log shows the current messages:

[B](EE) I810(0): No Video Bios modes for chosen depth
(EE) Screen(s) found, but none have a useable configuration
Fatal server error:
no screen found[/B]

I have tried adding combinations of vga=771, noapic, nolapic in the boot string with no success.

Can anyone help with some suggestion of how I can get Ubuntu running?  I would really appreciate your help.

---

### Post by cviorel on 2007-08-06
Try installing 915resolution, it's in the repository.

---

### Post by dimadee on 2007-08-06
Hi,

Thanks for the reply.

Can you give me a bit more info please?  Where is the repository, and how do I get it to where I can use it?

thanks!

---

### Post by cviorel on 2007-08-27
Here are some usefull links:
[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)
[http://slibuntu.wordpress.com/2007/03/13/using-915resolution-to-change-resolution/](http://slibuntu.wordpress.com/2007/03/13/using-915resolution-to-change-resolution/)
[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

---

### Post by slibuntu on 2007-08-27
Hey, thanks for linking to my blog, appreciate it!

---

