---
title: "Can't Install"
date: 2012-04-08
forum: Installation &amp; Upgrades
---

### Post by AstarothChild on 2012-04-08
[FONT=Century Gothic]I'm trying to install Ubuntu alongside Windows. I want to have a dual-boot system. So I downloaded it. The download went fine, but when I tried to install it, I got an error message. It said that I had something in C:\ with the same name already installed, basically. I know for a fact that I do NOT. I even checked to see. I looked through everything. Any ides would be greatly appreciated. Dx[/FONT]

---

### Post by darkod on 2012-04-08
If you want to install ubuntu as proper dual boot on its own partition, it has nothing to do with C:. Are you sure you didn't start the wubi installation?

For a dual boot installation just boot with the ubuntu cd, and if it doesn't offer the 'along side windows' option then there is something stopping it.

For example, you might have all 4 primary partitions used, or something similar...

---

### Post by AstarothChild on 2012-04-08
This is where I was... [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
I thought that this installer downloaded Ubuntu in such a way that you could choose which OS to boot from the boot menu. O.o
I didn't know I'd need to partition

---

### Post by darkod on 2012-04-08
That installs what is called wubi, a sort of virtual version of ubuntu working inside windows. Yes, you will have a choice which OS to boot but not in the real way.

Wubi works similar like a program installed in windows, so if windows breaks down for example, wubi will not be able to work.

When you have proper dual boot, the OSs are independent, and if one breaks down, the other still works. The dual boot is much better and I personally recommend it.

But you are free to install wubi if you want.

If you have vista or 7 instead of double click when you start wubi.exe, it's better to use right-click, Run As Administrator. That will run it with maximum permissions that is needed in windows.

---

### Post by AstarothChild on 2012-04-08
Thanks! This helped. ^_^ I think I may just get a CD for this instead.

---

