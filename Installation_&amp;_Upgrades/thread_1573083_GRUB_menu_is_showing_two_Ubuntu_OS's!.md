---
title: "GRUB menu is showing two Ubuntu OS's?!"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by Martificiam on 2010-09-12
I have dual-booted Windows XP and Ubuntu. Because Ubuntu 10.04 doesn't have the required proprietary drivers for my system, I chose Ubuntu 8.04. The installation procedure went well, the drivers are there, everything's perfect but... there's a problem with the GRUB menu that appears just after launching my laptop.
When I first installed Ubuntu it showed Ubuntu (and some letters and numbers), another instance for recovery mode, some memory test lines (I guess there are two of them) and Windows XP.
But after I used the software updater in Ubuntu (to make it up-to-date), the grub bootloader shows two more lines - and those are the same as the first two - Ubuntu (with some letters and symbols) and Ubuntu recovery mode.

Why are those duplicates there? I've never installed another Ubuntu OS on my PC. How do I fix it? Because at the moment I have two Ubuntu and two Ubuntu recovery mode lines which is stupid.

---

### Post by wojox on 2010-09-12
What does this command return:

```
dpkg --list | grep linux-image
```

---

### Post by beefone on 2010-09-12
Sounds like the kernel was updated. You can remove the old kernel using synaptic, if you want.

---

### Post by oldfred on 2010-09-12
We actually recommend you keep two kernels as sometimes the newest creates an issue, so you can still boot the older working one. If you do not change menu settings or delete kernels your list will continue to grow with updates.

There are settings in menu.lst that let you set howmany to show. Kernels do not take a lot of space so unless you are very limited on space you do not need to house clean on every update.

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even in lucid.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

---

### Post by Martificiam on 2010-10-08
I've edited the menu.lst file and removed the unnecessary entries. Thanks for pointing me to the right direction!

---

