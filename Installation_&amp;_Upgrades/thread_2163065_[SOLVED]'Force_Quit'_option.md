---
title: "[SOLVED]'Force Quit' option?"
date: 2013-07-16
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2013-07-16
Whatever happened to the  'Force Quit' option?
It used to be a very handy feature earlier versions of Ubuntu had, that for some reason was abandonded. If you had a freeze up or a non-responding program, you just opened the  'Force Quit' option and forced the unresponsive app/program to shutdown. Was playing around with 13.04 yesterday and got a bunch of freeze-ups but this  'Force Quit' option popped up a couple times and I was able to shutdown the offending app. 

Is the  'Force Quit' feature still available and if so where is it?
I miss it.

---

### Post by oldfred on 2013-07-17
I remember the elephants.Alt and SysRq    together and then R-E-I-S-U-B.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by cybrsaylr on 2013-07-17
This is the force quit feature I meant:

[IMG]http://cdn.howtogeek.com/wp-content/uploads/2010/07/sshot86.png[/IMG]

Just Googled and found this but haven't tried it yet:
[http://superuser.com/questions/456363/how-to-add-force-quit-icon-in-ubuntu-12-04](http://superuser.com/questions/456363/how-to-add-force-quit-icon-in-ubuntu-12-04)

Will this work on 13.04?

---

### Post by cybrsaylr on 2013-07-17
Sucess!

Just installed the 'Force Quit' icon on 12.04 Unity using this link:
[http://www.upubuntu.com/2012/02/how-to-add-force-quit-icon-to-unity.html](http://www.upubuntu.com/2012/02/how-to-add-force-quit-icon-to-unity.html)
Been testing it out and it works fine.

[IMG]http://2.bp.blogspot.com/-M0PCadauLag/Tyz3kkdCyAI/AAAAAAAAC0Q/Q1YUczdJQu0/s400/Force-Quit-Oneiric.png[/IMG]

Not sure if it will work with 13.04

---

### Post by oldos2er on 2013-07-17
```
xkill
```

---

### Post by cybrsaylr on 2013-07-17
> **oldos2er said:**
> ```
xkill
```

Curious?
Will that code work for all Ubuntu veersions?

---

### Post by oldos2er on 2013-07-17
Yes. The 'Force Quit' app is just a GUI front-end to xkill.

---

### Post by cybrsaylr on 2013-07-17
Thanks.

---

