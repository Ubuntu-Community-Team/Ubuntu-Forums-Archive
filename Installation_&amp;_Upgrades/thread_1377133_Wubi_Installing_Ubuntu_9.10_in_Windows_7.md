---
title: "Wubi Installing Ubuntu 9.10 in Windows 7"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by alvin4 on 2010-01-09
Hi, I just got finished wubi installing ubuntu in windows 7, and when I select ubuntu from the dual boot menu I get a strange message. Anybody know what's wrong with it?

---

### Post by garvinrick4 on 2010-01-09
What does it say?

---

### Post by alvin4 on 2010-01-09
> **garvinrick4 said:**
> What does it say?Thanks for replying. :)

OK, First it flashes something so fast I can't see it. Then this message appears:
> **GNU GRUB VERSION 1.97 BETA**

[Minimal bash-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device, file completions.]



sh:grub>It might as well be Greek. 

By the way, I did not worry about capitalization.

---

### Post by Sef on 2010-01-10
What are your system specs?

---

### Post by alvin4 on 2010-01-10
> **Sef said:**
> What are your system specs?

3 GB RAM


32-bit Computer


232 GB HDD

---

### Post by meierfra. on 2010-01-10
Boot into Windows and try this:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by alvin4 on 2010-01-10
> **meierfra. said:**
> Boot into Windows and try this:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)Is it safe?

---

### Post by meierfra. on 2010-01-10
Yes. The patch is from the person in charge of Wubi, and I have seen various people in the Ubuntu forums who used it successfully.

---

### Post by alvin4 on 2010-01-10
> **meierfra. said:**
> Yes. The patch is from the person in charge of Wubi, and I have seen various people in the Ubuntu forums who used it successfully.Thanks! Your the man!!:D You totally rock!:D It works!:D

---

### Post by meierfra. on 2010-01-10
> It works
Great. I had never seen this happen on a fresh install. So I wasn't sure it would work.

---

### Post by alvin4 on 2010-01-10
> **meierfra. said:**
> Great. I had never seen this happen on a fresh install. So I wasn't sure it would work.I am just wondering, what did all that text mean?

---

### Post by meierfra. on 2010-01-10
That was the Grub shell. One can use it to try to  boot into Ubuntu. See item 15 in the [The Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275")

Usually you will never see the Grub shell.  But there seems to be  a bug which prevents Grub2 from reading large ntfs partitions correctly.  So Grub2 was not able to reach the Grub Menu.  In other cases, Grub 2 is able to reach the Grub menu, but then fails to load some of the other boot files correctly.  The patch you downloaded works around this  bug. 

You can get to the Grub shell anytime by pressing "c" at the Grub menu. (press "esc" to get back to the Grub menu).

---

### Post by alvin4 on 2010-01-10
> **meierfra. said:**
> That was the Grub shell. One can use it to try to  boot into Ubuntu. See item 15 in the [The Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275")

Usually you will never see the Grub shell.  But there seems to be  a bug which prevents Grub2 from reading large ntfs partitions correctly.  So Grub2 was not able to reach the Grub Menu.  In other cases, Grub 2 is able to reach the Grub menu, but then fails to load some of the other boot files correctly.  The patch you downloaded works around this  bug. 

You can get to the Grub shell anytime by pressing "c" at the Grub menu. (press "esc" to get back to the Grub menu).Thanks for the info, much appreciated!:D

---

