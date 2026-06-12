---
title: "Need help with Windows boot-up"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by TheRandomRedhead on 2013-06-16
Hi guys,
This is my first post, so I hope it's in the right place.

Here's the deal: I installed Ubuntu 12.10 with Wubi a few months back and Windows Vista was also installed and working so I could switch OS any time. However, then I updated to 13.04, which obviously is not compatible with Wubi. I didn't realise this until I tried to go back to Windows briefly to do something, and found that only Startup Repair came up. I tried all the obvious things such as System Restore, and Startup Repair. Nothing. Ubuntu still works fine but I was wondering if I have mucked up the GRUB and if it's reversable. I'm going to try Boot Repair but have been warned it could be risky. Does anyone know how to fix this please?
Thanks for any answers,
TheRandomRedhead

PS. Also, when 'Ubuntu' is starting up it says 'Kubuntu', even though when it loads up, it is Ubuntu. Is this anything to do with it?
Thanks again.

---

### Post by Frogs Hair on 2013-06-16
This thread is huge and its author is best equipped to help you.  You may want to look through it while waiting for a direct more answer.     [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bcbc on 2013-06-17
> **TheRandomRedhead said:**
> Hi guys,
This is my first post, so I hope it's in the right place.

Here's the deal: I installed Ubuntu 12.10 with Wubi a few months back and Windows Vista was also installed and working so I could switch OS any time. However, then I updated to 13.04, which obviously is not compatible with Wubi. I didn't realise this until I tried to go back to Windows briefly to do something, and found that only Startup Repair came up. I tried all the obvious things such as System Restore, and Startup Repair. Nothing. Ubuntu still works fine but I was wondering if I have mucked up the GRUB and if it's reversable. I'm going to try Boot Repair but have been warned it could be risky. Does anyone know how to fix this please?
Thanks for any answers,
TheRandomRedhead

PS. Also, when 'Ubuntu' is starting up it says 'Kubuntu', even though when it loads up, it is Ubuntu. Is this anything to do with it?
Thanks again.
The details are rather confusing to me. 13.04 is compatible with Wubi, you said yourself it is working. Therefore that's not the problem. You have an issue instead with Windows. I'm not sure how you could have Kubuntu in your ?Windows boot manager but then boot Ubuntu, unless you installed Kubuntu with Wubi, and then installed the ubuntu-desktop package (switching to Ubuntu). 

But for a start, let's see the result of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). Don't run boot-repair for now, let's just see what the script result says.

---

### Post by bcbc on 2013-06-17
Also post the result of:
```
df -h
```

---

