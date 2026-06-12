---
title: "Reinstalling Ubuntu; I have separate /home partition"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by strange_cathect on 2007-11-14
After upgrading to Ubuntu 7 I noticed a few problems with the operating system.  I decided to do a clean install.  I have a separate /home partition and decided to just reinstall ubuntu to my root partition (/).

I went through the install and instructed the installer to mount my existing /home partition without formatting and only had the installer format and replace the "/" or root directory.

However, after rebooting, I noticed that the GRUB menu doesn't have an option for Ubuntu 7.  Instead I can choose between Windows and 2.6.20 generic Linux kernel.  I get a bunch of error messages concerning "unexpected inconsistency" "no job control in this shell" "apt-get is not installed" and finally a command prompt.  I can't get Ubuntu to "startx."  Something is broken. 

Where did I go wrong?

Here are my partitions:

/dev/sda1 as my ntfs windows file system (which still works).
/dev/sda4 is my /home partition
/dev/sda2 is my / root partition
/dev/sda3 is my extended (swap) partition.

When I did the install the ntfs was blanked out so that I could not alter it.  I set /dev/sda4 to mount as /home and did not format it.  I set /dev/sda2 to mount as "/" and selected format to ext3.  And finally I left dev/sda3 as swap.  The install seemed to go fine and then, upon rebooting, I have some serious issues.

Any help would be greatly appreciated.

---

### Post by ruibernardo on 2007-11-14
Hi strange_cathect,

even on a tty console, can you login and access to your home directory? If you do, then your problem is not about your mount points in fstab but rather graphic card driver or another problem.

Also remember that you did a fresh install, so some packages you had installed in your previous Ubuntu install aren't present now.

Can you post what error message you are getting on boot?

---

### Post by strange_cathect on 2007-11-14
Hello,

Thanks for the reply.  I updated my previous post with information about the error messages.  I am able to login using the user and password.  But all I have is a command prompt.  I cannot get it to accept "startx" to load Gnome.

---

### Post by ruibernardo on 2007-11-14
If GRUB doesn't show "2.6.22 generic" (gutsy), something went wrong in the install (if you tried to install gutsy).

Can you see your files in your home directory?

Confirm the kernel you booted with "uname -a".

Also confirm you do have anything installed from the kernel 2.6.22 (gutsy) in the /boot directory with "ls -l /boot". 

This should show you files like "initrd.img-2.6.22-14-generic" if the Gutsy install worked. If both "initrd.img-2.6.20-16-generic" and "initrd.img-2.6.22-14-generic" are present, you didn't format that partition and you installed Gutsy over Feisty without an upgrade. This would be a sign that you forgot to format the / partition(?).

---

### Post by strange_cathect on 2007-11-14
I tried a reinstall again.  This time GRUB does give me the appropriate selection for Ubuntu.  However, after Ubuntu begins loading I have error messages.

The error seems to be related to an fsck check of the filesystem.  I am told that /dev/sdb1 "resize inode not valid" and that /dev/sdb1 has an "UNEXPECTED INCONSISTENCY."  

How do I run fsck manually to correct this problem?

Thanks!

---

### Post by strange_cathect on 2007-11-14
Ok.  Ran fsck, corrected errors.  Rebooted.  Now I'm up and running.  Only problem is my dual monitor is not being supported but I can fix that no problem.

Thanks for your help.

---

### Post by ruibernardo on 2007-11-14
You're welcome. Glad you worked out the fsck problem.

---

