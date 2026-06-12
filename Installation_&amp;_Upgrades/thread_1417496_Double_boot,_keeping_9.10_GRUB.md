---
title: "Double boot, keeping 9.10 GRUB"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2010-02-27
Hello, there!
I'm installing 10.4 on a empty partition on my laptop, to test it, since last time it was a major headache. I want to keep the 9.10 GRUB to be the one that controls the boots and leave LL just for testings, is there a way I can do this?

---

### Post by darkod on 2010-02-27
Yes,and it would be a very smart decision. When installing 10.04, at the last installer screen before clicking Install click on Advanced. There you can tell it not to install a bootloader (grub2).

If you have only ubuntu (no current dual boot) don't be surprised that 9.10 will boot directly when you restart. It still doesn't know 10.04 is around. Once 9.10 boots up, just run

sudo update-grub

and it should detect 10.04 and from there on offer you grub boot menu at start to select an OS.

---

### Post by arashiko28 on 2010-03-02
couldn't pass the partition assignment step on the installation. :S:S

---

### Post by arashiko28 on 2010-03-20
Still want to try the upcoming 10.04, but keep having a couple of problems. Here's my partition table, with the unallocated space where i want to install 10.04 but can't pass from partition assignment for installation. :frown:

I also want to keep the 9.10 GRUB to be that that controls the boots, how do I do this? All I remember about GRUB has changed, not even the files are the same anymore.

---

### Post by arashiko28 on 2010-03-23
**[SIZE="5"][COLOR="Red"]where is menu.lst???[/COLOR][/SIZE]**

I have looked back and forth the /boot/grub/ for menu.lst and can't find it!

---

### Post by andrewthomas on 2010-03-23
Unless you upgraded to 9.10 from an earlier Ubuntu distro and kept your previous grub, you will not have legacy grub (0.97) but will have grub2 which does not use menu.lst

---

### Post by forkandles on 2010-03-23
As per the above reply, GRUB 2 does not use menu.lst.
Look here for more details:

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by arashiko28 on 2010-03-23
Already found a guide in the forum, thanks anyway.

---

