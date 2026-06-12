---
title: "Reinstall ubuntu"
date: 2018-08-06
forum: Installation &amp; Upgrades
---

### Post by kozs7 on 2018-08-06
Hi, I am kozs7, a beginner in ubuntu.
I have installed ubuntu 18.04 to my board PC UDOOx86 with UNetbootin in a USB memory, and it worked.
Now due to some reason, I have to reinstall ubuntu 14.04 instead.
So I have been trying to reinstall it from BIOS monitor, but it throws the following error:
"This device cannot do calls on its own. It is not a modern."

As an alternative way, I tried to uninstall the current ubuntu and initialize the UDOO computer, but I failed, because the software OS-uninstaller is not available now. 

Could anyone help me to reinstall the ubuntu of an older version or uninstall the OS and clean up the PC?

Thank you in advance :)

kozs7

---

### Post by Impavidus on 2018-08-06
I'm not sure what that error message means. It sounds like a poor translation. Maybe Ubuntu 14.04 is too old to support your hardware. Have you tried the 14.04.5 live disk or an older one? You must have a really good reason to install 14.04, as it only has 8 months of life left.

To clean up, you can always wipe the hard drive. Wiping the first megabyte should do it. Installing a new OS over whatever is in place should do it too, but sometimes the partitioning tools get confused by whatever is present and you may have to wipe the first megabyte anyway.

---

### Post by kozs7 on 2018-08-08
Hi Impavidus,

Thank you for your kind reply.
As you suggest, Ubuntu14.04 is too old and the UDOOx86 computer does not support the version anymore.
I need Ubuntu of that version since a software used for my work requires it, but I am aware of the disadvantage that you pointed out.

Also, I appreciate your advice on how to clean up the current OS. I will try to reinstall a newer Ubuntu on that PC, and see whether the PC would be confused by the current OS as well.

Thank you very much! :)

---

