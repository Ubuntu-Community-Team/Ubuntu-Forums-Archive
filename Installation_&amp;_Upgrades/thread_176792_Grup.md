---
title: "Grup"
date: 2006-05-15
forum: Installation &amp; Upgrades
---

### Post by ravibharadwaj on 2006-05-15
Can v use Boot.ini for a dual boot option instead of GRUP or LILO?
I know it can b done. Can ne 1 plz tell how do i do it?

---

### Post by localzuk on 2006-05-15
I am guessing you are asking if you can use the Windows boot method to choose the OS to boot.

I would recommend that you don't - simply because I would not like Windows to have any access to my Linux partitions... But according to  [http://www.slackbook.org/html/booting-dual.html](http://www.slackbook.org/html/booting-dual.html) you can use Loadlin to do it...

Why would you not want to use grub? It is much more flexible than Windows's attempt...

---

### Post by Sef on 2006-05-16
> Can v use Boot.ini for a dual boot option instead of GRUP or LILO?

Why do you want to do it that way?

---

### Post by ravibharadwaj on 2006-05-16
I'm quite happy wid the GRUP loader,no issues with it.
It's just a curiosity,just wanna know how to do it.

 1 more question-How can i increase the TIME OUT ON GRUP?

---

### Post by localzuk on 2006-05-16
In your /boot/grub/grub.conf file you should have a line 'timeout=blah' somewhere. Simply edit the file (using sudo) and change the value of blah to what you want.

---

