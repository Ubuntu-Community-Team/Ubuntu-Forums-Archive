---
title: "grub problem after ubuntu 10.10 update"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by legionarius on 2010-12-04
Hello! I have a dual boot windows 7 64 bit - ubuntu 10.10 64 bit on the same hard disk. A few days ago I launched the ubuntu update manager. I downloaded and installed something like 100 MB of updates, and after the reboot I noticed that something was changed in the grub:
[[IMG]http://img27.imageshack.us/img27/2325/grubb.th.jpg[/IMG]](http://img27.imageshack.us/i/grubb.jpg/)

[](http://imageshack.us)
Some new lines had been added in the grub menu after the update. Now if I do not touch anything on my pc boot, it loads a new black screen in which it asks me my username and after the password. After these requests it says something like: "welcome in ubuntu". I write down: "sudo reboot", I write the password, it reboots the pc, and I'm back to the grub menu. Now if I select the third line on the grub menu, it loads ubuntu as it was before the update. I mean the "standard" ubuntu, in which I can use the mouse to click on programs etc.
Windows 7 is ok too. The question is: what has happened after the update? Moreover I would like to change the grub lines order so that it loads directly the third choice to go directly inside of ubuntu, or directly windows 7. Or if it is possible I would like to cancel the other lines that are appeared after the update. At the moment after a few seconds it loads ubuntu from the first line of the grub menu. So every time I turn my computer on, I have got to wait the grub loader to select the third line, or the last one to boot windows 7. I would like to avoid this waste of time. 
Thank you in advance :)

---

### Post by legionarius on 2010-12-05
Any ideas to solve the problem? Thank you.

---

### Post by yiannis66 on 2010-12-05
Try to delete only the grub that makes you the proplem.
You can do it from synaptic
A safe way to do it is with [http://www.webupd8.org/2010/04/2-click-update-for-ubuntu-debian-based.html]("http://www.webupd8.org/2010/04/2-click-update-for-ubuntu-debian-based.html").
If you don't have it downloand it ,it's very helpfull.

---

### Post by legionarius on 2010-12-05
Thank you for the answer. I will try it as soon as possible.

---

### Post by sikander3786 on 2010-12-05
You can remove the un-needed kernels as per instructions here by **drs305**.

[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

And for setting Windows or Ubuntu as the default (GUI way), see this.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by legionarius on 2010-12-05
Thank you for the help. At the moment I've solved installing the "StartUpManager". Now when I turn my computer on, it loads directly the third option of the grub menu. In this way it loads ubuntu 10.10 without losing time. If more lines will appear in the grub menu, I will try the other solution (to delete the ones I do not need).
Thank you again for the help.

---

