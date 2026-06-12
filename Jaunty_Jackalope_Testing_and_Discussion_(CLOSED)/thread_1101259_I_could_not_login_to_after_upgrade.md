---
title: "I could not login to after upgrade"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by halovivek on 2009-03-20
Hi 
yesterday Ubuntu has downloaded the Jaunty updates. The upgrade went fine. After reboot it struck in the load screen and even i am not getting to the login screen. i rebooted and tried to use the recover fail safe Generic. even i could not get the screen. the screen went crash and i could not continue. how to over come this one?

---

### Post by Anthon on 2009-03-20
If there was a kernel upgrade, make sure you select the previous kernel while booting. 

If you only have one kernel in grub's menu list then there should be some output from the failsafe boot. If not edit the bootline in grub and remove 'quiet' and 'splash' keywords, then continue booting. 
The output should give you some idea about where it hangs.

---

### Post by jheaton5 on 2009-03-20
I have the same problem.

I can login with the previous kernel, but cannot login with the newly updated kernel.  How can I take advantage of the new kernel?

---

### Post by riftt on 2009-03-20
> **jheaton5 said:**
> I have the same problem.

I can login with the previous kernel, but cannot login with the newly updated kernel.  How can I take advantage of the new kernel?

What I done is to select recovery grub entry for the newest kernel and then select resume (just press enter), later on, when prompted. This will probably get you to safe login with the newest kernel.

---

### Post by Bert Mariën on 2009-03-21
Read this:

[http://www.phoronix.com/vr.php?view=13559](http://www.phoronix.com/vr.php?view=13559)

---

