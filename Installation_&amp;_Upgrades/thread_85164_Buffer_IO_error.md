---
title: "Buffer I/O error"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by jmelton on 2005-11-01
I've just started getting a message that says "Buffer I/O error on device dm-2, logical block 13899353" (and similar messages that increment the number by 1 each time) during bootup.  I get maybe 40 of these messages and then bootup continues successfully.  It's happening when it's going through the Enterprise Volume Management part of booting.  I've struck out trying to find out what's going on and how to fix it when I've googled this message.  Anyone have any ideas?

I'm dual booting Windows XP and Hoary on a Dell Inspiron 1100 laptop.  I started getting the error message immediately after I had rebooted from Windows into Linux; actually, I think I may have had the machine on standby in Windows and then rebooted into Ubuntu.  Anyway, I've continued to get this message each time I boot into Ubuntu now.  In addition to it causing booting into Linux to take about a minute longer than it should, I'm worried that something may be seriously wrong, although so far I'm not having any problems booting into Windows.  Thanks in advance for anyone's help with this!

---

### Post by jmelton on 2005-11-02
Please, I'd really like some help with this problem if anyone can!  Thanks!

---

### Post by dbott67 on 2005-11-02
There are a couple of commands that you can try: badblocks and fsck

Check the man files for proper usage.

-Dave

---

### Post by jmelton on 2005-11-03
[QUOTE=dbott67]There are a couple of commands that you can try: badblocks and fsck

Check the man files for proper usage.

-Dave[/QUOTE]

Thanks!

---

