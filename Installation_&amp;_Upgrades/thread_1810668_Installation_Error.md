---
title: "Installation Error"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by jtpokora on 2011-07-23
I just installed Ubuntu 11.04 side by side with Windows 7. I can boot to Ubuntu fine, but when I select to boot Windows from the GRUB screen, it will show the "Starting Windows" screen with the 4 spinning dots then gives the message
------
Checking file system c:
the type of the file system is NTFS
volume label is OS

One of your disks needs to be checked for consistency. You may cancel the disk check, but it is strongly recommended that you continue. To skip disk checking, press any key within X second(s).
-----
When the countdown reaches 1, it freezes and won't perform the disk check. I have left it for hours, and it won't continue. Any suggestions on how to fix the problem so that I can boot into Windows? Thanks

---

### Post by raja.genupula on 2011-07-23
have you checked with out waiting what its going to give ? if it s booted you successfully into that then go for check your disk through command prompt for errors

---

### Post by jtpokora on 2011-07-23
When I try to say continue w/o checking the disk, it freezes there and won't proceed (if that answers your question). I have been unable to log into Windows, because when I try to boot to Windows, it always gets hung up on the disk check.

I fact, it actually never gets to the disk check (or so it appears). It freezes on the screen that says it should check the disk for inconsistency.  Is there a way to access the command prompt before the disk check message to see any errors?

---

### Post by Quackers on 2011-07-23
How did you resize the Windows partition to make room for Ubuntu (if that's what you did)?

---

### Post by jtpokora on 2011-07-23
When I was installing Ubuntu, there was a screen that asked how much you wanted to delegate to Ubuntu with a little slide in the middle. I just kept it where it was at (apprx. 130 GB) and pressed continue.

This was the screen: [http://www.ubuntu.com/sites/www.ubuntu.com/files/active/natty/05-install-ubuntu-alongside.jpg](http://www.ubuntu.com/sites/www.ubuntu.com/files/active/natty/05-install-ubuntu-alongside.jpg)

---

### Post by Quackers on 2011-07-23
It may be that the Ubuntu installer has resized the Windows partition slightly, which is not a good method. It is vastly preferrable to use Windows Disk Management console to resize C:, if necessary, and it should be defragmented first.
Do you have a Windows repair disc or a Windows installation disc?

---

### Post by jtpokora on 2011-07-23
Yep, I have the recovery disk that came with the laptop. Should I reinstall Windows from that? I did a full backup before I installed Ubuntu

---

### Post by Quackers on 2011-07-23
That's not a repair disc or an installation disc. It does not have the repair tools.
If there is nothing on there that you can lose it may be preferrable to recover the system, but beware as it may use the whole disc by default, wiping out Ubuntu too.

---

### Post by jtpokora on 2011-07-23
Alright, I think I can do that. But before I do, Is this the Windows repair disk that you are talking about?

[https://help.ubuntu.com/community/RecoveringWindows#Resizing](https://help.ubuntu.com/community/RecoveringWindows#Resizing) Windows Vista / 7 Partitions

just a little ways down the page under "Dual-Boot" header? 
Will that .ISO file have the repair tools necessary?

Thanks a bunch, I appreciate your help

---

### Post by Quackers on 2011-07-24
No, those downloads have been removed due to copyright issues, I believe. 
There are other sites still hosting them. It's a 120MB iso file that you burn the image to disc. It gives you several repair functions.

---

