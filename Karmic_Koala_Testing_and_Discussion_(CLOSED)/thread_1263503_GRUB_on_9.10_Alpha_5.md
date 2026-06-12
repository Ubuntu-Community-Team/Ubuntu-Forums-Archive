---
title: "GRUB on 9.10 Alpha 5"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by frozenheart on 2009-09-11
I was running 8.04 because I borrowed a friends disk. I wanted to update to 9.04, but something broke between 8.10 and 9.04. I decided to just test out the Alpha 5 of 9.10. That sounds fine, right? 

Windows XP doesn't appear in the GRUB Menu (I'm running XP Pro. I don't know if the problem is a missing driver as my machine was built for Vista but I dumped Vista in favour of XP Pro). I need to get into it to run programs that don't work in Linux. 

I tried running gksudo gedit /boot/grub/menu.lst in the terminal, but no avail. It just shows a blank document.

I have to have it back as soon as I can because I need XP for homework!

Thanks!

---

### Post by oboedad55 on 2009-09-11
> **frozenheart said:**
> I was running 8.04 because I borrowed a friends disk. I wanted to update to 9.04, but something broke between 8.10 and 9.04. I decided to just test out the Alpha 5 of 9.10. That sounds fine, right? 

Windows XP doesn't appear in the GRUB Menu (I'm running XP Pro. I don't know if the problem is a missing driver as my machine was built for Vista but I dumped Vista in favour of XP Pro). I need to get into it to run programs that don't work in Linux. 

I tried running gksudo gedit /boot/grub/menu.lst in the terminal, but no avail. It just shows a blank document.

I have to have it back as soon as I can because I need XP for homework!

Thanks!

As you know 9.10 is still in alpha testing so your mileage may vary, widely. If you'll post how you installed Ubuntu- Wubi or dual boot, how you did your partitioning, etc. you'll get a better response. Also tell us what your Jaunty (9.04) problem is and maybe someone can help.

---

### Post by overdrank on 2009-09-11
Moved to Karmic Koala Testing and Discussion

---

### Post by The Cog on 2009-09-11
9.10 uses /boot/grub/grub.cfg (iirc) instead. This is automatically rebuilt from scripts in /etc/grub so you shouldn't edit grub.cfg manually.

---

### Post by The Cog on 2009-09-11
P.S.
I just found these references in another thread:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

