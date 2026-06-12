---
title: "No Dual Boot Option Given"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by terrapin893 on 2010-03-26
So I was using Ubuntu on my desktop.  I had a windows install that I did first and then shrunk the disc and installed ubuntu.  Everything was good until windows went windows on me and had to be reformatted.  So I reinstalled windows on the partition and now when my computer boots it does not give me the option to chose the ubuntu partition, it just loads windows.  Is there a way this can be fixed or do I need to start from scratch and reload windows and then ubuntu?

---

### Post by lindsay7 on 2010-03-26
You need to tell us what version Ubuntu you have installed to get the grub menu back for example do you have 9.10 installed or 9.04 etc.

If it is 9.10 it has grub2 so do this

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

If it is the older grub do this.

> Originally Posted by lindsay7 View Post
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type &#8220;sudo grub&#8221;. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Note:  Do not type in the quotation marks in the commands.

---

### Post by terrapin893 on 2010-03-28
Solved, thank you very much!

---

