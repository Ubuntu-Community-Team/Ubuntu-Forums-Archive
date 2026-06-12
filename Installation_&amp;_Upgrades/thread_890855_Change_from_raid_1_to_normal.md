---
title: "Change from raid 1 to normal"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by muzehyun on 2008-08-15
I have installed Ubuntu 8.04 Server with Raid 1.
It is ubuntu software raid.
Now, I want to use one hdd for another machine.
Is there any simple way to make it normal hdd system? without format?

I unplugged one hdd then..
I can see some of ubuntu starting screen.
But it finally shows
---
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)
--- 

Thank you
Sean

---

### Post by psusi on 2008-08-15
You can use the mdadm command to reshape the array to consist of only a single disk.  This process is somewhat complicated however, and I can't recall all of the details.

---

