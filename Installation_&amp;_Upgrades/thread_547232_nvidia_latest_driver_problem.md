---
title: "nvidia latest driver problem"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by wststreet on 2007-09-09
I installed the latest drivers from nvidia website..
i have Nvidia A6600 GT

Because i'm new to linux idon't really know stuff.... 

Anyway.. i installed those drivers, everything was going well.... until i restarted... i couldn't start X anymore... i used a portable device to search google for stuff so after an hour i finaly made "startx" work...

Now i'm not interested in installing the latest drivers... i just want to uninstall this think i just installed.... 

Here's the link to the file i installed:
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)

I got it from this page:
[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

Can you please tell me how to uninstall it?

---

### Post by Pumalite on 2007-09-09
If you reconfigured xserver and you are IN the system, you don't have to worry about it.

---

### Post by iAndrew on 2007-09-09
I had a problem like this. First off there is a script called Envy which installs the correct driver for you. I'm not sure if it uninstalls what you have. But, \

[http://ubuntuforums.org/showthread.php?t=435199](http://ubuntuforums.org/showthread.php?t=435199)

Look at that thread.

To stop gdm:

> sudo /etc/init.d/gdm stop

---

### Post by Pumalite on 2007-09-09
Post your specs and tell me what card you have and what you want to do.( as I understand it, part of the Envy script includes removal of old drivers)

---

### Post by wststreet on 2007-09-09
I used envy, i'll report here when i'm ready... and if it doesn't work i'll post my xorg.conf maybe there is the problem

---

### Post by wststreet on 2007-09-09
Ok it worked.... I used ENVY first uninstalled then installed the nvidia drivers.. it automaticly build me the kernel for the driver.. it worked perfectly...

---

### Post by Pumalite on 2007-09-09
Glad you fixed it. All it took was courage, it seems.

---

