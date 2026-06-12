---
title: "Occasional boot problem on dual boot windows/ubuntu 14.04 pc"
date: 2016-08-23
forum: Installation &amp; Upgrades
---

### Post by krichar50 on 2016-08-23
Hello folks

I have a dual hard drive pc with windows (Vista) installed on 1 drive and ubuntu 14.04 on the other. After upgrading from 13.02, intermittent boot problems appeared (there were no major issues with the 13.02 install). In all problematic cases, ubuntu gets to the grub menu and usually loads init but gets stuck just before creating swap (I think). Occasionally it doesn't even get that far, and I end up with the GRUB prompt. On other occasions it gets to the login screen, but freezes after logging in.

I've tried installing and running running boot-repair to generate a boot-info diagnosis (see [http://paste.ubuntu.com/23077264/](http://paste.ubuntu.com/23077264/)) but I'm not familiar enough with ubuntu's boot process to be sure whether to accept the suggested repair or what the underlying problem might be. I'd appreciate some advice on how ro proceed from those with greater expertise.

Many thanks in advance for the help.

---

### Post by oldfred on 2016-08-23
Do not run Boot-Repair's autofix. That installs grub to all MBR, and you want to keep the Windows boot loader in the MBR of sda, so if necessary, you an go into BIOS and directly boot sda and Windows.

Not sure if related. I do not fully understand the Enablement stack. But with LTS versions you get interim new kernels with the middle versions. If you install 14.04.1 or earlier, you keep the old kernel & have 5 years. If you install anything after 14.04.1, you have to upgrade to 14.04.5's kernel (based on Xenial) to get the remaining part of the 5 years.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by krichar50 on 2016-08-27
Thanks, that answers my specific question about Boot-Repair's autofix and makes sense to me. 

I don't understand the Enablement Stack either (yet), but it looks like I upgraded from 13.04 to 14.04.3 and haven't had any problem with updating the kernel since then. So is that idea still worth pursuing?

In any case I'd still like to understand how to find the cause of the boot problem, so if r anyone else has suggestions about how to do that please let me know.

---

### Post by krichar50 on 2016-09-01
Bump

---

