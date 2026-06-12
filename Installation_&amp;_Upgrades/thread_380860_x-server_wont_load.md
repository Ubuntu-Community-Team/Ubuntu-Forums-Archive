---
title: "x-server wont load"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by celticbhoy on 2007-03-10
after following a how -to to upgrade to xorg 7.2 I can no longer start x-server, I have read the instructions on the how-to to downgrade, but I have a small prob, I cant use gedit to edit the sources.list file from the text interface which ubuntu now starts with. I am surethere must be another small prog todo this, can anyone please help.

---

### Post by tintix on 2007-03-10
Use nano! :popcorn:

---

### Post by celticbhoy on 2007-03-10
thanx worked a treat.

On a seperate not, I have edgy installed, but on my grub screen I have two versions of Ubuntu listed, .17.11, and .17.10, both with recovery options, what is the diferance between the two as any changes I make in one changes the other.

And secondly how do I change from one drive to another in the terminal window ??

---

### Post by tintix on 2007-03-10
You ask about 17.11 and 17.10? They ain't ubuntu versions - they're the Linux kernel versions. You system is the same, but now you have two kernels. The system needs to boot the kernel first, and then the whole stuff around (programs, servers and etc.).
Probably the system has downloaded another kernel because it has some modules to better support your graphic adapter.
The recovery mode is being used to recover your system (it doesn't do anything automatically. You have to do it by yourself). It's like the fail safe mode in the windoze. :) But in the recovery mode xserver won't be started automatically (to start X type "startx").
You can choose the kernel to boot in the grub bootloader.
So there are any seperate systems, only little bit different kernels. So if you reconfigure the system (I mean servers (probably except the xserver), programs), you will see the same changes in your system - more or less it will not matter which kernel you boot.
So which kenel to boot? The one, which has the newest version and on which your graphic card works well.
But why did you upgrade your xserver???? :lolflag:  There's no sense. Personally, ain't feel any changes. And if there would be critical updates required, youd got them from the ubuntu update manager.
How to change to another drive? You got all drives mounted in the /media folder. So type "cd /media" and "ls -l" and you'll see all drives. Just cd to drive, you need, because all mounted drives are displayed like "folders" (all devices in Linux are displayed as files).
Peace, bro. Good luck studying Ubuntu Linux. Later, if you have learned ehough, you will feel, that Linux rocks and it's much better and powerfull than windoze. :guitar:

---

