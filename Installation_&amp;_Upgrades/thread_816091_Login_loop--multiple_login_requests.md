---
title: "Login loop--multiple login requests"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by 3birds on 2008-06-02
I've solved the NOAPIC problem, but I'm still getting stuck in a "login loop."  I enter userid/pw and the system seems to boot, but then I'm presented with the login screen again.

Ideas appreciated.

---

### Post by diogopedrosa on 2008-06-15
Hi 3birds!

Could you solve your problem? I'm facing the same problem. I have a AMD 64 bits. I've already made a clean instalation using a live CD of 8.04 32 bits version and a live CD of 8.04 64 bits version, each one in a different partition, and the problem happens on both!

Besides, I also notice a display failure on the top part of the screen when shuting down or restarting the computer. Do you also have this problem?

I found a topic about this on [http://ubuntuforums.org/showthread.php?t=800091](http://ubuntuforums.org/showthread.php?t=800091), but the solution proposed by markbuntu there didn't solve my problem.

Regards,
Diogo

---

### Post by 3birds on 2008-06-15
> **diogopedrosa said:**
> Hi 3birds!

Could you solve your problem? I'm facing the same problem. I have a AMD 64 bits. I've already made a clean instalation using a live CD of 8.04 32 bits version and a live CD of 8.04 64 bits version, each one in a different partition, and the problem happens on both!

Besides, I also notice a display failure on the top part of the screen when shuting down or restarting the computer. Do you also have this problem?

I found a topic about this on [http://ubuntuforums.org/showthread.php?t=800091](http://ubuntuforums.org/showthread.php?t=800091), but the solution proposed by markbuntu there didn't solve my problem.

Regards,
Diogo
No, I was not able to solve the problem.  In the meantime, I tried "a bunch" of things and caused other problems.

Then, I decided to reformat the partition and start again.  Whoops!  There went my Windows installation.  (If I had known it could be fixed, I'd have done that, but as it was I reinstalled Windows.)

So, I'm back at Square -1 on this one.  I have a squeaky-clean Windows XP Home SP3 installation (working great) and a "missing" partition that I used for the Ubuntu installation.

Yes, I did see the funky display band at the top of the screen while rebooting.  I have since updated my BIOS and video driver, but I have not had a chance to try again since then.

Good luck finding the solution, and if you do, please repost to this thread!

Thanks!

---

### Post by naturalfreak on 2008-08-14
I tried enabling the ATI driver and that fixed things.  In Failsafe mode, System > Administration > Hardware Drivers then select the ATI driver.

---

