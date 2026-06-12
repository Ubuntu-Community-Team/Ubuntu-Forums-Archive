---
title: "Changing *DM"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by mabreaux on 2007-07-14
In the work I do I must know if my programs work under both gdm and kdm.   Is there and easy way to toggle these back and forth so that testing can be done.   

Although in the lab we use kdm almost everywhere.  I am noticing a few gdm units seeking in.

Please help.
Michael

---

### Post by kidders on 2007-07-15
Hi there,

There's no reason why you can't run as many display managers as you want on the same machine. Toggling between them is a matter of simply switching console.

---

### Post by mabreaux on 2007-07-16
The question is how do you do it with out locking out the machine.

---

### Post by kidders on 2007-07-16
I'm not quite sure what you mean by "locking out" your machine. Ubuntu will happily let you run multiple X servers simultaneously, and it doesn't really make much difference whether each uses a different display manager, or the same one.

Normally, when I do things like this, I tend to invoke Xorg & [?]dm manually, since things can sometimes get a little messy & confusing ... especially if the apps you're running might accidentally break things. It's nice to be able to hit CTRL+C and kill entire process trees quickly & easily.

**Edit:** If you have more than one monitor, you can also run a different X server on each one ... but you'd need more than one mouse/keyboard for that to work well.

---

### Post by mabreaux on 2007-07-16
When I type /etc/init.d/gdm stop the system shut down to a black screen and I can not type /etc/init.d/kdm start.  So what I end up with is a dead system.

---

### Post by kidders on 2007-07-16
Hmm... That shouldn't happen! Unfortunately, I have no idea what might be causing it. :-( Maybe something keyboard-related is stopping you being able to switch back to a text-based console?

At any rate, for greater speed, I would suggest running KDM and GDM at the same time, rather than having to repeatedly log in and out, etc. You'd probably have to tweak your /etc/init.d scripts to have Ubuntu do that automagically though, which is one of the reasons I suggested going the manual route ... it's just plain quicker, and you don't have to mess about with startup scripts.

---

