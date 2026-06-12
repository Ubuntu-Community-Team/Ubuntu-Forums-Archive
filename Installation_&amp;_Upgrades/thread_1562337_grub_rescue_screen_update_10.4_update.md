---
title: "grub rescue screen update 10.4 update"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by guptan on 2010-08-27
I updated Ubuntu 10.4 dual boot installation (with winxp) and system asked me to do a restart. So did I. I'm ended up with grub rescue screen showing an error at first line: no such device: xxxx-xxx-xxx-xxx

While installing updates system had showed some GRUB dialog window where I clicked to continue install. I don't know what it does, and why Ubuntu assume a normal user know what GRUB is???

What should I do now to get both OS working? Any help appreciated.

---

### Post by quixote on 2010-08-29
This problem has been going around a lot.  There must be some badly phrased choice in the upgrade which is misleading a lot of people.  Not good.

What the error message means is that grub has lost the location of the OS, but all your data and all the operating systems are still there and are fine.  Getting grub to find the right partition is tedious (instructions here, under [Command Line and Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode")), but not difficult.  Let me first make sure I understand what's going on.  Do you get the initial list of choices of OSes?  And then when it starts ubuntu it goes off into the uuid-not-found stuff?

The way to fix it is to boot with a LiveCD, find the partition that has your root system files on it, and give grub specific commands to use that.  I can go over all that and try to simplify some of the instructions in the link, if it sounds like that's what you need to do.

Grub, by the way, stands for "grand unified bootloader."  It's basically a tiny operating system capable of telling the hardware where to find the rest of the operating system.

---

