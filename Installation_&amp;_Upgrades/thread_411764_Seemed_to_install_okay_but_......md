---
title: "Seemed to install okay but ....."
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by jtesolin on 2007-04-17
hello all, 
A few months ago I installed Ubuntu Dapper as Dual Set-up with Windows XP Media Center. It seemed to go through the install okay, with partitions and such.  I believe after I rebooted everything seemed okay. And where the screen asked me to choose my OS it has two options for Ubuntu (mem test ?) and the Ubuntu kernel 2.x.x. And then the windows partitions. However it seems after each time I perform updated to my computer, new entires are listed on the dual boot screen. They all have different kernel numbers. I am relatively new to Ubuntu and love it , however is there a way to remove or hide the duplicate entries? A few tings I should note are my desktop computer (P4) was from a store(TigerDirect) that you do not received the Windows XP disk so reinstall from scratch is out and I did not do a recovery disk for ubuntu (which I will definitely do next time). Will I have re-install over existing partitions or is there another way?

---

### Post by joft on 2007-04-17
> **jtesolin said:**
> hello all, 
They all have different kernel numbers. I am relatively new to Ubuntu and love it , however is there a way to remove or hide the duplicate entries?

I think, you have to uninstall these previous/old kernel versions. If there is no reason keeping older versions, just use e.g. Synaptic or (on console) aptitude to remove the **old** version - but don't remove all :D . The names of the packages you may remove are "linux-image-2.6.x-x-xxx", e.g. "linux-image-2.6.15-26-386" . Then, on next reboot they should have gone away.

---

### Post by jtesolin on 2007-04-19
Okay. Thanks for your reply :) 

I will try this after work and post what happens.

---

### Post by rocknrolf77 on 2007-04-19
It's good to at least keep the previous kernel to fall back to. In cause an upgrade goes wrong with the newest kernel. :)

---

### Post by jtesolin on 2007-04-19
Okay. I so I logged into Ubuntu to try to remove a kernel. I saw that there was updates, one for automatrix, and a few others so I tried to get those before I remove the previous kernels. However, it said download failed. So i looked in Symnatec to remove the kernel however i was not sure ... do you remove the kernel-header or kernel image? I even tried to install the new feisty fawn but it said authentication failed. I checked the manual it said to make sure you have the latest update manager. I do which is weird.Would it be better if I do a fresh install over the dual boot edgy?

EDIT: Wow. Sorry I guess I missed part of the previous post. I deleted the previous ones as suggested. Maybe tomorrow I will try to see if the Update to Feisty will work. I have the alternate cd if download fails from the update manager.

---

