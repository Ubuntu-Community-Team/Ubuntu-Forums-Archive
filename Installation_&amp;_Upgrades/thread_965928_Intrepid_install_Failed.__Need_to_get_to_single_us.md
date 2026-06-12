---
title: "Intrepid install Failed.  Need to get to single user root mode"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by davidkahn on 2008-10-31
I have set up Grub to require a password to select recovery alternative modes.  However, in the past when I selected a "Recovery Mode" version of a kernel, it went directly to a command prompt logged in as root.  Now with Intrepid I come to a new menu that has an entry "Drop to root shell prompt", which I can't use because it requires the root password, and in Ubuntu you don't need to know root's password.
 
What am I supposed to do?
 
Help!!!
 
David

---

### Post by davidkahn on 2008-11-01
I don't know if anyone is going to read this, since there were no replies to my question.  But since I solved it, I wanted to post my solution for other people.  Moreover, if requiring a password to get to the single user prompt logged in as root was intended to improve security, I just found a security hole.  This hole might not apply to my computer because I setup /boot/grub/menu.lst to cause grub to require a password to edit the grub boot parameters.  But since many people don't, this procedure is a security hole for them.
 
I used grub to perform a one-time edit of the boot line:
[INDENT]kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/md0 ro single
[/INDENT]and made it:
[INDENT]kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/md0 rw init=/bin/bash
[/INDENT]Booting then brought me to a command prompt as root, with the file system being read-write.  I then used the passwd program to set root's password to a known value, and now I can select menu item that has an entry "Drop to root shell prompt", and enter root's password.
 
However, having a (presumably) crackable root password seems so un-Ubuntu.  So I am wondering if anyone else has a more elegant solution.

---

