---
title: "what is the best way of reinstalling GRUB?"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by ingo on 2006-11-05
Hi,

I wondered what the best way of reinstalling GRUB is bearing in mind that you don't want to touch anything other than the MBR.

Reason I'm asking is 'cos I've come across a number of threads where people ended up reinstalling Ubuntu just to fix GRUB, bit of an overkill...

Personally, whenever anything untoward happens (God forbid!) I use a Suse installation CD.


Any bright and easy ideas?

Cheers

Ingo

---

### Post by mark_g on 2006-11-05
```
/sbin/grub-install /dev/sda with sda the correct hard drive
```

(more details can be found on [http://forumz.tomshardware.com/softw...ict231779.html](http://forumz.tomshardware.com/softw...ict231779.html))
That should do it.

---

### Post by ingo on 2006-11-05
nice one mark_g but the link is dead :( 

you got more info on what happens next, whether it is configured, etc.?

ta

Ingo

---

### Post by orb9220 on 2006-11-05
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by ingo on 2006-11-05
wicked :)

---

