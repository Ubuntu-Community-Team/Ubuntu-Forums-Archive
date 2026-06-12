---
title: "Upgraded Kernel + Video Problems"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2008-05-08
Hi.  I installed the 2.6.24-16 kernel per [this post]("http://www.justubuntu.com/install_2_6_22-10_ubuntu") and I'll explain why at the bottom.  After it rebooted, The screen had a distorted graphic of the regular Ubuntu logo, and then I was prompted saying I was running in low-graphics mode and I could either Configure, Exit, or Continue. It also gave the option to "always run in low-graphics mode".  I selected "continue".  After logging in, I was prompted to download and install a couple packages - nothing much, a few hundred kb of the ESD plugin - so I did.

I went to System -> Administration -> Screens & Graphics and changed my screen driver to a 1024x768 LCD which usually works for my laptop.  I restarted the x-server and it logged in fine, no problems with the graphics now.  However, if I reboot, I get the same deal from above.  Can you think of a way to resolve this?

If you can't tell by my sig I'm using ATI X1300 graphics card and the ATI restricted driver.  All other hardware is just as listed on the [Lenovo website]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-62487").

The reason I upgraded the kernel is the suspend feature didn't work in Gutsy (which came with the 22-14 kernel).  When I upgraded to Hardy the suspend feature worked, plus I could switch desktop sizes without rebooting.  However, I can't access password-protected shares, per the thread in my sig and what seems to be a common bug, and that's more important than the other two so I put Gutsy back on.  Thanks!

---

### Post by MaindotC on 2008-05-13
bump

---

### Post by zvacet on 2008-05-13
Maybe you can try [this.]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html")

---

