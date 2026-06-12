---
title: "is there any rescue disk?"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by mrhellboy86 on 2010-01-19
My Ubuntu have experienced a hang
I shut it down by power
and I have a Grub Error
this is the grub error:


grub loading
error: unknown filesystem
grub rescue>


is there any way to fix it?
or any tools?
I am fresh man not familiar with shell commands

---

### Post by tommcd on 2010-01-19
For fixing the grub problem you could try a Super Grub Disc:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
If you system is not recoverable and you need to save any data you can try a System Rescue CD:
[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

As far as the "hang" is concerned, if you could describe in detail what is going on, perhaps with a thread title that is more descriptive of your problem, perhaps someone will be able to help.

---

### Post by AmirM on 2010-01-19
I dont know that this can help you or not but after some Errors in ubuntu I found a site/forum that told me to install the grub again,and the problem was fixed.this is the instruction:
1.boot with cd.
2.open terminal.
3.go to super user by typing "sudo -s",enter password if necessary.
4.type "grub"
5.type "find /boot/grub/stage 1" you get an answer like "(hd0,1)"
6.type "root (hd0,1)" or what ever your hard disk and boot partitions are.
7.type "setup (hd0,1)" or "setuo(hd0)" and use your info instead.
8.type "quit" to quit.
9.reboot from HDD.

---

### Post by tommcd on 2010-01-20
That was for grub-legacy. The procedure for reinstalling grub2 from the live CD is different:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

