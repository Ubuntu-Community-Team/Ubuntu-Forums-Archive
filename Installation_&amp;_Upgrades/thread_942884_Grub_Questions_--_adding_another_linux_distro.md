---
title: "Grub Questions -- adding another linux distro"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by cha0sthe0ry on 2008-10-09
I currently have 4 partitions on my computer.  Hda (0,0) - (0,3).  On them I have:

0,0:  Windows Vista
0,1:  Linux Swap
0,2:  Ubuntu
0,3:  Slackware

Slackware is the last thing that I installed, a project to learn most basic linux commands from a professor at school.  I want to continue using Ubuntu's GRUB, because if I don't like Slackware, or decide to change it out with another distro, then I can keep using the Ubuntu GRUB without any problems.

I am a newbie, and need to know how to add Slackware to the current GRUB.  Thank you.

---

### Post by oldos2er on 2008-10-09
You would add an entry to your /boot/grub/menu.lst that looks something like this:

title Vector Linux SOHO 5.9 (Slackware 12.0.0) (on /dev/sda7)
root (hd0,6)
kernel /boot/vmlinuz-2.6.22.19 root=/dev/sda7
savedefault

 Of course, for "title," you can put whatever you like; and you'll need to adjust the location of "root" and the kernel name and location.

---

### Post by cha0sthe0ry on 2008-10-09
Thank you, I will try that just as soon as I repair my grub now, lol

---

### Post by WWSmith36 on 2008-10-09
There are a few different ways to boot a system with multiple linux distros.  The problem with just putting a manual entry in the menu.lst is that update-grub will not automagically update the kernel entry for the other distros.

There are three ways to do this: a configfile boot entry, a chainloader boot entry, or a symlink boot entry.

The is a good description of how to do this at the Grub Page
[http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)

---

