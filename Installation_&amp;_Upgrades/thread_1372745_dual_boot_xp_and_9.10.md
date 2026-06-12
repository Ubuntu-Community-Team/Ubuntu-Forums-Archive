---
title: "dual boot xp and 9.10"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by mkapadia13 on 2010-01-04
Hello all:

I'm a newb and appreciate your help.

I recently installed XP Pro and 9.10 on my hard drive, and I'm experiencing a very long wait time my computer to start up.  It takes about a minute or two to get to a screen where it says 'GRUB Loading', and another minute to get to the selection screen.  

When I select Ubuntu it also takes about two minutes to boot, when I select XP it takes the same time as if I just started the computer.  Is there a way to make this faster?

Thanks a lot.

//Moiz

---

### Post by oldfred on 2010-01-05
If you have multiple drives this could be part of your problem:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

You can also look in your log files to see if some process has issues.
/system/administration/log file viewer  look in all logs but particularly kern.log

---

