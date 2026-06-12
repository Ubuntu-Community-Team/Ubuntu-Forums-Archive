---
title: "Dual boot Windows 8 partition disappeared"
date: 2015-07-02
forum: Installation &amp; Upgrades
---

### Post by patond on 2015-07-02
About a year ago I installed Ubuntu 14.04 on a friends Toshiba Satellite Pro C850.  It was installed as dual boot with original Windows 8.

Recently she couldn't boot into Window.  It booted into Ubuntu OK.  Gparted didn't even show the Windows partition although the Ubuntu partition was only half the size of the laptop's hard drive.  

I used Boot-Restore but this did not solve the problem. Restore MBR was greyed out.  I attach link to boot-info report [http://paste.ubuntu.com/11809189/]("http://paste.ubuntu.com/11809189/")

Can anyone help.

---

### Post by yancek on 2015-07-02
The boot repair output you posted shows only Ubuntu installed on the drive using UEFI.  The proper EFI files for Ubuntu are on the first partition and the second partition takes up almost the rest of the drive excepting the small swap space.  No sign of windows.  Somebody made some kind of changes as operating systems don't usually just disappear.  Not knowing what happened prior to being unable to boot windows it is difficult to say if it is possible to recover data.

---

