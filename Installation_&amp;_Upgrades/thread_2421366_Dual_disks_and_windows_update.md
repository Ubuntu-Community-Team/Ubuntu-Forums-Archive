---
title: "Dual disks and windows update"
date: 2019-06-20
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2019-06-20
I am experiencing similar problems on two dual boot machines. A Toshiba L555 and a Dell M6800. On the latter, I recently installed 18.04 using a separate disk (UEFI mode). On the Satellite it was Legacy boot. In the other disk, in both cases I have windows - W7 on the Satellite and W10 on the Dell. The boot loader is in the Ubuntu disk and the BIOS is configured so the Ubuntu disk is seen first. The problem is that when I attempt to run an update on windows, it gets stuck and does not progress any further. I solved it by disabling the Ubuntu disk on the bios and then windows updates correctly. Obviously this is not practical, so I was wondering if anybody experience this problem and if so, if they have a better solution.

Many thanks in advance

---

### Post by yancek on 2019-06-20
I don't use windows so I don't need to update but if you are booting windows from Grub2, you could change the boot priority temporarily so that on reboot, it boots windows since you normally need multiple reboots to do a windows update.  Bit bizarre, but...

---

### Post by danielsender on 2019-06-20
I understand that, the problem is that the update process gets stuck, it finds the items to install but it does not go beyond the "Preparing to install". After some time it will come back with a button saying "Retry" and an error message 0x800705b4 - I googled for that error and followed some of the recommendations but none worked. Furthermore, like everything in windows they don't clarify how that error message is printed and from what program(s) we can see it.

---

### Post by yancek on 2019-06-21
Is this problem with both windows 7 updates and windows 10 updates, on both machines which both have Ubuntu?   I saw some sites which indicated that it always/usually happens when you have an upgrade from7/8 to windows 10, is that the case?   I don't think there is much any one here can do to help as it seems to be a problem with the update process on windows.  I'd agree that many of the error messages we see on windows are very obtuse and not helpful.  Good luck with it.

---

### Post by Rubi1200 on 2019-06-21
Not sure what you have tried so far but perhaps this article will help offer some possible solutions:
[https://windowsreport.com/windows-10-update-error-0x800705b4/](https://windowsreport.com/windows-10-update-error-0x800705b4/)

---

### Post by danielsender on 2019-06-24
Here are my findings.

1. For the dual-disk 18.04+windows7, windows7 will update if I disable the ubuntu disk,

2. For the dual-disk 18.04+windows10 there wasn't anything that would make it update, I followed Rubi1200's link as well as other recipes and I was always getting the same message.

So I went through a Reset process and then windows10 started updating. Pretty scary if the only solution to fix something is to reset and/or reinstall the system.

Thanks guys.

---

