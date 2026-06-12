---
title: "Dual boot problem - Win7 wont start"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by saturnine2 on 2014-09-01
Hello everyone!

I'm having trouble with my desktop computer. I previously had Ubuntu and Windows 7 installed and they both worked fine, the dual boot worked. 

Then I needed to install Ubuntu all over again. In that process Ubuntu "lost" Win7 completely, meaning that GRUB didn't find it anymore. When starting the computer it just went straight to Ubuntu. So I tried fixing it with Boot Repair. Now I have the option to boot to Windows but when I do it gives me this:

[I]Setting partition type to 0x7
error: invalid EFI file path.
[/I]
And here's what I got from Boot Repair:

[http://paste.ubuntu.com/8208118/](http://paste.ubuntu.com/8208118/)

Any ideas? I'm obviously not smart enough to deal with boot issues :)

---

### Post by yancek on 2014-09-01
You have windows 7 installed in MBR mode and Ubuntu on another drive in EFI mode, a problematic combination.  You also have Grub on the mbr of the windows drive, did you have Ubuntu previously installed on that drive?  Looking at your output, you do have EFI files for windows on sdb, the second drive but your windows system is on sda.   I don't use EFI partitioning so you'll need to wait for someone with experience with it.

Looking at your output, you do have EFI files for windows on sdb, the second drive but your windows system is on sda.

---

### Post by saturnine2 on 2014-09-03
Alright. Thanks for the reply. Do you think it might help if I installed Ubuntu again? I can't recall that there was an option between EFI and MBR in the installation process? If I changed the Ubuntu drive to MBR as well, would that help?

---

