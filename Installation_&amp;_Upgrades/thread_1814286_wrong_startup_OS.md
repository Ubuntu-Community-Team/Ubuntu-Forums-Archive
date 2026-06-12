---
title: "wrong startup OS"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by soloman498 on 2011-07-29
I recently loaded Ubuntu 11.04 in dual boot with Windows 7.I want Windows 7 to be the default start up but even though I adjusted it in Start Up Manager it still defaults to Ubuntu 11.04.(64 bit OS)Any Ideas please.

---

### Post by Quackers on 2011-07-29
DId you edit /etc/default grub?
If so, when you saved the edited file did the terminal report some errors about /root/.local/share/xxxxxxxx files or directory not existing?

---

### Post by soloman498 on 2011-08-07
No I didn't but I reloaded 11.04 and it was running o'k and then it updated to the new kernel .10 and it went back to being Ubuntu default.Is there any way to change which kernel it is using?

---

### Post by JRV on 2011-08-07
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1795241](http://ubuntuforums.org/showthread.php?t=1795241)

Any of the three methods listed will work.

---

### Post by soloman498 on 2011-08-08
i tried the three ideas and even installed grub customiser but they all showed that windows 7 was in the correct position to be the default startup OS.This has only happened since the kernel was updated to .10 Is there a way to revert to .08 ?

---

### Post by Mark Phelps on 2011-08-08
There's a fourth method -- which I've found ALWAYS works ...

When you edit /etc/default/grub, the DEFAULT line, instead of changing the number there, copy the text from the Window 7 line in /boot/grub/grub.cfg into there -- between quote marks.

That way, when the number of stanzas changes, it will still default to the Win7 Loader entry.

---

### Post by soloman498 on 2011-08-13
All fixed.Thankyou everyone:D

---

