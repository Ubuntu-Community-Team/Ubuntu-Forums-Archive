---
title: "Fresh install (i386) 03/13/10 went fairly well"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-03-13
Thought maybe some would find this useful. I'd been running the same installation of Lucid since the toolchain was uploaded in early November. In fact the Karmic I upgraded had been installed for quite a while.

So I decided it was just time to start fresh and I'm glad I did. Things look pretty darn great, including Plymouth :D

I especially do want to mention a couple of minor glitches with the Live CD. 

#1: At present, if no action is taken, you won't even see the typical "boot menu". You must press Esc within a few seconds of the initial screen appearing and then you'll see the typical menu.

#2: The CD integrity test now works :D This is a first for me with Lucid, however when it completes and you see the results you're prompted to press Enter to reboot, well pressing Enter did nothing, nor did Esc. I finally had to either Ctrl + Alt + Del or Alt + SysReq + B, sorry I didn't take notes and I don't recall which.

#3: I next ran the Live Desktop and then installed without a problem, but once the installation had completed and I was presented with the usual, "Do you want to restart or keep testing" and then clicking restart the CD ejected properly, but then when prompted to "close tray and press Enter", once again pressing Enter did nothing. That time I know I used Alt + SysReq + B and the machine rebooted properly :D

All in all things look pretty darn good, os-prober failed somewhat but I'm multi-booting nine OS's and a simple "update-grub" sorted things. I haven't tried an auto-login yet, I'm almost scared to :P

---

### Post by Atermoon on 2010-03-13
Lol I was just thinking about a fresh install and I bumped into your thread. Nice to hear, although in Ubuntu and specially during alpha stage you never know if what works for someone else will work for you :D

---

### Post by manoriax on 2010-03-13
I've also upgraded a Karmic installation to Lucid. Is there a way to get the new boot-screen (which I do not see) to that Lucid-installation without reinstalling it? Are there any other new things in Lucid I might not see, because I do not use a fresh installation? And if yes, is there a way to get them working in my Lucid installation?

---

### Post by grubdude on 2010-03-13
Me too tried the new build and Plymouth is finally working in virtualbox. Now if they could only fix the Guest Additions problem with -16 kernel. Works great with -15 but -16 only allows low resolution and causes kernel panic....

Hope someone gets to it soon. Until then it is -15 for me I guess. :-)

9 OSs? wow....

---

### Post by manoriax on 2010-03-15
I've installed a fresh Lucid in a VM now and I was able to see the new boot screen once. After I ran all the updates, it's now replaced by some purple screen with some debug messages like "error probing SMB1" (the system works anyway). Am I able to fix this?

---

### Post by kansasnoob on 2010-03-15
I guess I spoke too soon about plymouth. It worked great through about a dozen restarts, then a few hours ago I started getting kicked to a tty again.

I'd get a text login and that would drop me a command prompt but I couldn't startx to save my soul, so I removed plymouth and did a sudo reboot and it went to gdm like it should, and X started just fine.

What broke plymouth again I have no idea.

---

