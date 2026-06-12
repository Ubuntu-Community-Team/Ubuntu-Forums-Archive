---
title: "upgrading 11.04 -&gt; 11.10, can not boot"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by tbred on 2011-10-31
after upgrading from 11.04 to 11.10, when i try to boot into ubuntu, i get a blank screen.

what should I do?

---

### Post by Rubi1200 on 2011-10-31
Hi and welcome to the forums :)

Please provide more details such as the computer specifications, error messages, or anything else that might be relevant.

Thanks.

---

### Post by tbred on 2011-10-31
it's a e6300 on an asus p5g41t mobo with geforce 7600gt and ddr3 ram
there is no error message, i installed 11.04 with wubi on windows vista beforehand, then upgraded yesterday to 11.10, after which when i was prompted to restart, i shut down. 2 hours later, came back, turned it back up, it boot to the windows/ubuntu selection, when ubuntu is chosen, the screen is soon stuck on a black screen (with orange tint). boot into windows works fine.

---

### Post by drs305 on 2011-10-31
I have the same video card and it works fine in 11.10. You may need to install the nvidia drivers. To allow the system to boot to the Desktop, try booting with the 'nomodeset' kernel option.

The details are provided in the following link. Look at the "How to temporarily set" section. 
[http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

If it boots click on Dash and type "Additional" and select the Additional Drivers applet and install the nvidia drivers.

---

### Post by tbred on 2011-10-31
doesn't work.

---

### Post by tbred on 2011-11-01
i tried replacing the wubildr with the one in \ubuntu\winboot and now i get to the grub menu, when i selected recovery mode it gets stuck at "loading initial ramdisk"

---

### Post by tbred on 2011-11-01
actually, ignore my last post, recovery mode gets to a command prompt of some sort. normal mode gets stuck at the UBUNTU loading screen (ubuntu in text with 5 dots underneath)

---

### Post by tbred on 2011-11-01
ok i tried with a 3.0.x generic instead of 3.0.x-pae and it gets into ubuntu fine, i can log in with my useraccount to the desktop environment.

should i do something with this or can i just stick with this workaround?

---

### Post by drs305 on 2011-11-01
> **tbred said:**
> ok i tried with a 3.0.x generic instead of 3.0.x-pae and it gets into ubuntu fine, i can log in with my useraccount to the desktop environment.

should i do something with this or can i just stick with this workaround?

Using the 'pae' kernel may allow you to use more memory, but if you aren't having problems or don't have more than 4GB of memory you probably won't notice the difference.

---

