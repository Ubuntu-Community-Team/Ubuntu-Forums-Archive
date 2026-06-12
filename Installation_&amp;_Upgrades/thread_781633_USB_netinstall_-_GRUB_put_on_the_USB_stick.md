---
title: "USB netinstall - GRUB put on the USB stick"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by suhewabe on 2008-05-04
While doing an install to a HDD from a USB stick, the end of the process installs GRUB onto the USB stick and not the HDD.  

I tried installing LILO instead, but it seems that the HDD was /dev/sdb during the install and without the USB drive is /dev/sda, so lilo fails.

How do I fix this?

---

### Post by Pumalite on 2008-05-04
According to that, in step 8 'Advanced Tab'. you should change (hd0) for (hd1)

---

### Post by suhewabe on 2008-05-04
Step 8?

---

### Post by Pumalite on 2008-05-04
Sorry, I forgot you are installing from USB. Try to find a way to change where Grub installs.

---

### Post by suhewabe on 2008-05-04
I ran the installer again but in rescue mode and now I can get to a command prompt, and I'm even able to start a grub command line but I know nothing about grub.

When I fdisk -l I see
/dev/sdb1 * ..... Linux
/dev/sdb2   ..... Extended
/dev/sdb5   ..... Linux swap / Solaris

I found a [thread]("http://www.fedoraforum.org/forum/showthread.php?t=975") in fedoraforum.org that talks about how do install grub to the HD but it's not going quite as smooth as they make it look.

I've tried setting the root using "root (sdb1)", but obviously that's not right.

---

### Post by suhewabe on 2008-05-04
Pumalite - wanted to thank you for pointing me in the right direction.  I've got everything working right.

Thanks.

---

### Post by Pumalite on 2008-05-04
You are welcome. Good luck.

---

