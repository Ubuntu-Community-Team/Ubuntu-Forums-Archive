---
title: "Ubuntu 16.04 for Lenovo Ideapad 320 touchpad, WLAN &amp; other proprietary driver working"
date: 2017-08-24
forum: Installation &amp; Upgrades
---

### Post by lordjette on 2017-08-24
[COLOR=#000000][FONT=&amp]I have problem with my new laptop ,  I bought Lenovo  ideapad 320 in store and install a dual boot Ubuntu 16.04. then,  my touchpad , WLAN and some propriety drivers are not working. I have search many drivers  in Ubuntu for ideapad 320. I got nothing. Please help ...&#65279;[/FONT][/COLOR]:(

---

### Post by lordjette on 2017-08-24
proprietary drivers are not working.. please help on this...

---

### Post by BenginM on 2017-08-24
Hiya , welcome to the forums .

which kernel is currently in use , is the system up-to-date? and what is the wlan card and what are these other proprietary drivers you're referring to ..!

#See :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1708852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1708852)

So, first try with this kernel & X stack packages for desktop here , 
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by ajgreeny on 2017-08-24
Please remember we are all volunteers here at ubuntuforums.org and that includes all we forum staff.

If you do not get any answers after 12 hours (that's a minimum period) bump the thread by adding just the word **bump** to a reply but do not repeat your request as you did immediately above.

To find your hardware quickly install inxi if you don't already have it and run command inxi -F and copy back here the output.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by dobiegillis on 2017-09-16
According to this patch, this should be fixed in the latest kernels: [https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/commit/drivers/input/mouse/elan_i2c_core.c?id=1874064eed0502bd9bef7be8023757b0c4f26883](https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/commit/drivers/input/mouse/elan_i2c_core.c?id=1874064eed0502bd9bef7be8023757b0c4f26883)

However, I'm still having this touchpad problem on my Ideapad 320, and I've tried kernels 4.12.12 and 4.13.2.

---

