---
title: "Install problem on Dell Power Edge 2650"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by greazy on 2013-01-15
Hello all.

I'm having issues installing Ubuntu server 12.x or 11.x on my newly-acquired Dell Power Edge 2650.  It has 3gb ram, 1x 140gb SCSI hard drive and all bios up to date.

I was successful with installing Win 2k8 server via the Dell CD but I want Ubuntu!  At least with this step I knew I had the HD setup correctly through my PERC controller.

When installing 11.x server I had zero issues but upon completion of the install and the following reboot I get a blank screen.  It was disconnected from the network during and after install.  When installing 12.x server it required additional drivers - but othewise it was fine.

is this an xorg.conf issue?  Curious because if I hold down my SHiFT button during boot it doesn't allow me to boot into safe mode.

Thoughts?  My next step is to just try it one more time and see what happens.

Thanks for reading,

Greazy

---

### Post by manchild408 on 2013-03-01
Hi there Greazy,

I'm having the same issue using server 12.04. It appears to be a video mode issue. I'll update if I come up with a solution.

---

### Post by manchild408 on 2013-03-02
By hitting ESC instead of Shift at boot, you can get the GRUB boot menu (assuming you installed GRUB). It wont display, but with a standard install, you can hit the down arrow once, then Enter which will bring you to the recovery console, which DOES display. From there you can drop into a root console. This allowed me to install openssh-server and get things rolling remotely (you have to use the "enable networking" option to both turn on networking services and mount the filesystem in read/write mode). I also found that if you use the "continue normal booting" option after booting into the recovery console, the system will come up just fine. Haven't yet had the chance to investigate why this is, but I'll add another update if I come up with anything.

---

