---
title: "WinXP installation AFTER Ubuntu Dapper installation"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by Distue on 2006-07-19
Hi community,

I've got a Ubuntu 6.06 Dapper Drake installation on my laptop and it was good for a time, but then I realized that I need WinXP for my study. Don't want it but I have to have it.

Summary:
Ext3 partition with Ubuntu
Swap partition
empty partition where windows should be installed
FAT  partition where a recovery version of windows is, but I've got a CD anyways.

My question:
I want to keep Ubuntu as my primary OS and wanna install WinXp. How do I do that so that the Grub Loader isn't damaged? There are thousands of guides howto installing Linux AFTER a Windows installation but I didn't found any proper tutorial for reverse use.

Why I'm posting here? Cause Windows forums would just give me the advice to discard linux :E

---

### Post by philippe_carlo on 2006-07-19
Been there:
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Installing_windows_AFTER_Linux]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Installing_windows_AFTER_Linux")

Advice: backup your ext partition.

---

### Post by frodon on 2006-07-19
Installing XP after ubuntu will destroy GRUB and you can't do anything against that, however re-installing GRUB is really easy and painless.
There're many different ways to re-install GRUB : 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

So just install XP then use the live or the alternate CD to restore your GRUB, that's all ;)

---

