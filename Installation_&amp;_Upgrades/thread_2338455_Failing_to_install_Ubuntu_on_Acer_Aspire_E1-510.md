---
title: "Failing to install Ubuntu on Acer Aspire E1-510"
date: 2016-09-28
forum: Installation &amp; Upgrades
---

### Post by zannabianca1997 on 2016-09-28
I'm trying to install Ubuntu 16.04 (same with previous 15.10) on a Acer Aspire E1-510. I received  the pc from a frien of mine, not used to linux, that already failed the  installation, then deleting the previous Windows version. I don't care  about dual boot, only getting Ubuntu there.


  I created a Usb stick with the Startup disk creator. Loaded into the  pc, clicked "Install Ubuntu". The installation ran fine, selected to  delete the previous version of Ubuntu, loaded wifi, all seemed fine. Got to file copy, run until "Copy file 55 of 55" and then black screen,  lot of errors and stop. It appeared a little window on a black screen  reporting a system error and then nothing.


  Tried to load then live, but it just visualized the console and then  the same error. I can still load terminal with Ctrl+Alt+F1, thought.


  Loading without usb still takes to the same problem. I selected the option to download driver from the net.
  Is this a graphic driver problem? Please help me, I'm clueless.

---

### Post by howefield on 2016-09-28
Try again, this time using using 16.04.1 for your bootable USB stick as 15.10 went End of Life in July, no point fighting with an old dead release.

---

### Post by zannabianca1997 on 2016-09-29
Tried to live with Ubuntu 16.04. Opens to a black screen that remains  for more than ten minutes. Still able to open terminals with  Ctrl+Alt+Fn, and log-in with user Ubuntu. I also tried Kubuntu 16.04 (I had that already downloaded). It opened  live with no problem, but the installation wizard stopped after settings  (more or less same point it stopped for ubuntu when I direct installed)  with "[Errno 30] Read only disk".

---

### Post by zannabianca1997 on 2016-09-29
Tried intalling Ubuntu 16.04 (no live). Crashed the installation after system and program installation with: [error setting ownership of './lib/modules/4.4.0-38-generic/kernel/divers/input/input-polldev.ko': Read-only file system]("http://i.stack.imgur.com/aocvF.jpg")  Now the mouse is stuck. No idea of what to do

Rebooting now (not from usb) take me again to a grub> prompt.
I think it's like he cannot properly install the grub bootloader... but i know almost nothing of that.

---

