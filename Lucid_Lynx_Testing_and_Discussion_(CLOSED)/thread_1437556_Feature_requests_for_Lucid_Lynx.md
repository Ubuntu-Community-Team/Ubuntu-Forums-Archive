---
title: "Feature requests for Lucid Lynx"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hachaboob on 2010-03-24
#1: At the end of installation from the install media you are presented with a window dialog with a "Restart" button. You need to restart the computer in order to complete the installation and there is no other options. If you have to restart there should be a count down timer like every other sane OS installer which will restart after 30 seconds have elapsed.

#2: You can not install any software or change any settings which require admin rights when logged in as a non-admin user via the GUI. For example the unlock dialog window just has a field for password. This should be done similarly to the way done in Mac OS X.

#3: The installer should have a customise option before install starts to select/deselect extras languages etc because the user should not be expected to click anything during installation of files.

---

### Post by yoasif on 2010-03-24
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by b00lean on 2010-04-17
I would like to have a TRIM support for my ext4 SSD drives.
Looks like that TRIM support for ext4 was added in kernel 2.6.33, but Ubuntu 10.04 has 2.6.32 kernel so it supports TRIM only on btrfs filesystem.

I believe that TRIM support is important maintaining ssd disk performance, even windows7 has TRIM support.

Is it possible to backport this feature from 2.6.33 into Lucid Lynx planned kernel release?
If not what is the suggested workaround?

Thanks for your time,
Karel

---

### Post by cariboo on 2010-04-17
Have a look [here]("https://help.ubuntu.com/community/Signpost/Answers#Suggesting a feature in a specific program") for how to request a feature. Don't take to long, as [UDS-M]("https://wiki.ubuntu.com/UDS-M") is from May 10 -14 2010.

---

### Post by b00lean on 2010-04-18
> **cariboo907 said:**
> Have a look [here]("https://help.ubuntu.com/community/Signpost/Answers#Suggesting%20a%20feature%20in%20a%20specific%20program") for how to request a feature. Don't take to long, as [UDS-M]("https://wiki.ubuntu.com/UDS-M") is from May 10 -14 2010.
I wil do that, thank you.

---

### Post by lucasart on 2010-04-18
> **hachaboob said:**
> #1: At the end of installation from the install media you are presented with a window dialog with a "Restart" button. You need to restart the computer in order to complete the installation and there is no other options. If you have to restart there should be a count down timer like every other sane OS installer which will restart after 30 seconds have elapsed.


I agree with you in principle, but in reality there's no other way. If the reboot is automatic, then Ubuntu can eject the CD and reboot, which it does when you click. But when the computer reboots, your BIOS will swallow the CD again and reboot from it, and start all over again. Windows 7 actually has the same problem and you must remove the CD after install when rebooting orelse you'll restart the install from scratch.

---

### Post by b00lean on 2010-04-18
> **b00lean said:**
> I wil do that, thank you.
It has been confirmed to me by one of the ubuntu kernel engineers that trim for ext4 will be available in ubuntu 10.10 kernel and will be backported later on to LTS.

---

