---
title: "upgrade to feisty: waiting for root file system"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by Stebbins on 2007-09-18
Hello everyone,

Others have posted about problems similar to mine.  However, in the threads that I have scoured, either (a) the details of the problem are different, or (b) the solution completely bewilders me.

I run a dual boot of Windows XP and Edgy.  When I tried to upgrade to Feisty, my computer froze at the end of the upgrade and I was forced to shut down the computer.  When I tried to boot Ubuntu again, I received the "can't access tty" message that many others have been getting.

I tried booting Ubuntu in verbose mode.  My boot sequence is:
   root (hd0,4)
   kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sda5
   initrd /boot/initrd.img-2.6.17-11-generic
   quiet
   savedefault
   boot

Startup progressed fine until it reached this line:

   Begin: Waiting for root file system... ...

After a long wait, the computer printed the following lines:

   Done.
      Check root= bootarg cat /proc/cmdline
      or missing modules, devices: cat /proc/modules ls /dev
   ALERT! /dev/sda5 does not exist. Dropping to a shell!

   BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
   Enter 'help' for a list of built-in commands.

   /bin/sh: can't access tty; job control turned off
   (initramfs)

The initramfs prompt works, but the file system it accesses seems to be different from the one in which my files are located.  I tried running the alternate CD in recovery mode, and sda5 does indeed exist and contains the root file system.

I would grately appreciate it if someone could shed some light on this problem for me.  I have very important files stored in my Linux partition and would like to keep them intact if possible.

Thank you,
~Stebbins

---

### Post by Stebbins on 2007-09-18
I guess 2 am EST isn't the best time of day to post questions. bump.

---

### Post by kambrik on 2007-09-19
I'm having same problem... How do i resolve this?

---

### Post by Stebbins on 2007-09-22
What I finally ended up doing is burning a new LiveCD.  Running Ubuntu off of the CD, I was able to access the files in the Linux partition and transfer the ones I wanted to keep to a USB drive.  Then I simply re-installed Ubuntu.  I lost all of my personal settings and programs, but since I was able to save what I really cared about, I'd call this one a win.

Since Kambrik is having the same problem as I was, I won't mark this thread as solved, in case the solution I came up with isn't satisfactory in his case.  It seems like there is a way to fix the booting problem we were having... I just don't know what it is :-P

---

